---
layout: page
title: study note about ROS on AWS
---

### Research note about Amazon Deepracer

### Reference
[DeepRacer latest developer guide](https://docs.aws.amazon.com/deepracer/latest/developerguide/awsracerdg.pdf#%5B%7B%22num%22%3A565%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C72%2C416.96%2Cnull%5D)

[Deepracer workshops](https://www.slideshare.net/AmazonWebServices/new-launch-repeat-1-aws-deepracer-workshops-a-new-fun-way-to-learn-reinforcement-learning-aim206r1-aws-reinvent-2018)

[RoboMaker로 DeepRacer 자율주행차 만들기](https://www.youtube.com/watch?v=v5GBUpVkZbY)

[UCL - David Silver RL 슬라이드 웹사이트](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html)

[팡요랩 - 강화학습 강좌](https://www.youtube.com/playlist?list=PLpRS2w0xWHTcTZyyX8LMmtbcMXpd3s4TU)

### Deepracer 컨셉
- AWS deepracer
  - 1:18 스케일, mounted camera, on-board compute module
  - The module can run inference(추리) against a deployed reinforcement learning model in order to drive itself along a track. The compute module and the vehicle chassis are powered by dedicated batteries known as the compute battery and the drive batter
  - 시뮬레이터에서 강화학습 모델 만들기 -> 경주 트랙 시뮬레이션에서 모델을 평가 <br>-> 하이퍼파라메터를 튜닝, 훈련을 해 랩타임 줄이기 -> 딥레이서 리그 경기 출전
  - <img src="../images/ARC_1.png" alt="drawing" width="900"/>

### DeepRacer 시작
- Signup AWS and create model
- IAM (what is IAM? and why we need it?)
  <br>
  <pre>
  AWS Identity and Access Management(IAM) 사용자는 AWS에서 생성하는 엔터티로서 AWS와 상호 작용하기 위해 그 엔터티를 사용하는 사람또는 애플리케이션을 나타냅니다. AWS에서 사용자는 이름과 자격 증명으로 구성됩니다
 </pre>

- Deepracer에서 쓰이는 AWS 서비스
  - Amazon S3
    - To store trained model artifacts in an Amazon S3 bucket. 
  - AWS Lambda
    - To create and run the reward functions. 
  - AWS CloudFormation
    - To create training jobs for AWS DeepRacer models. 
  - Amazon SageMaker 
    - To train the AWS DeepRacer models. 
  - AWS RoboMaker 
    - To simulate an environment for both training and evaluation.

### Train & Evaluate Models (AWS deeprace 서비스 오픈후 테스트 가능)
- 머신러닝: Tensorflow 를 사용한다, **proximal policy optimization algorithm**
- Train and Evaluate models thru AWS DeepRacer Console
- Train and Evaluate models thru Amazon SageMaker notebooks

### Reinforcement Learning (강화학습)

#### introduction

- Reinforcement Learning<br>
<img src="../images/RL_1.png" alt="drawing" width="600"/>

- 다른 기계학습과 다른점: 
  1. 강화학습에는 supervisor 가없다. Reward 만 존재. 답을 알려주는 사람이 없다.
  2. Reward 는 목적을 정해줄뿐 구체적으로 어떻게 문제를 해결할지 정답을 주는게 아니라 여러번 반복된 경험을 통해 스스로 정답을 찾아가는 방식
  3. Feedback이 딜레이 될수 있다. 시간이 굉장히 중요하다.

- Reward = scalar(방향이 없는 단순한 수) feedback
- Sequential Decision making: reward는 cumulative 값이다, 여러 action 의 순서와 값이 만들어낸 종합적 값이란 뜻
  - Examples: 장기적 금융 투자
- 강화학습에 적합한 문제는 따로 존재할것이다. (즉각적인 행동보다 장기적으로 해결해야되는 문제들)
- 각 타임스탬프(timestamp) 마다
    - Agent: (execute action, receive observation, receive reward) 
    - Environment: (receivess action, emits observation, emits reward)
    - <img src="../images/RL_2.png" alt="drawing" width="600"/>
- History(Agent side): the sequence of observations, actions, reward (H_t = O_1, R_1, A_1, ... , A_t-1, O_t, R_t)
- State: information used to determine what happens next (S_t = f(H_t)) 히스토리를 가공해서 스테잇을 만든다.
- Environment state: observation과 reward를 결정하게 되는 source 라고 볼수있다.
  - ATARI <img src="../images/ENV_STATE_1.png" alt="drawing" width="600"/> 
  - 유저가 컨트롤러를 움직였을떄 다음 화면을 어떻게 보여줄지 computing 하게 되는데 이때 참조하게 되는 상수값(State가 그것과 비슷하다고 볼수있다.)

- Agent State: 다음 action 을 하기 위해 쓰이는 정보들.
  - <img src="../images/AGENT_STATE_1.png" alt="drawing" width="600"/>

- Markov State: State가 마르코프 하다?무슨뜻?? -> 오로지 현재 state 만 중요하다 (의사 결정을 한다)
  - Environment State 와 History 는 마르코프 하다
  - Agent State 가 현재 State 말고 이전 State 들을 참조하게된다면 그건 마르코프 하지 않다.

- Fully observable environments: Agent가 Environment State 를 observation 할수있다. 
  - Agent State = Environment State = information state (Markov Decision Process)

- Partially observable environment: ex) 카드게임 자신의 패만 보이니까, Environment state != Agent state (Partially observable Markov decision process)

- Major components of an RL agent (아래 세 가지 구성요소중 하나 이상 가진다)
  - Policy: agent의 행동을 교정해준다, it's a map from state to action
    - Deterministic policy: PI == policy, a = PI(s) state 를 넣어주면 action 이 결정
    - Stochastic policy: PI(a|s) = P[A_t = a| S_t =s], state 를 던저주면 여러 action의 각 확율이 나온다 
  - Value function: how good is each state and/or action (Value는 Policy가 존재해야만 한다.)
    - 미래 reward 기대값, to evaluate goodness/badness of states 
  - Model: agent's representation of the environment
    - 모델은 환경을 예측한다. (next state , the next(immediate reward))


### Reward Function
```python
def reward_function3(on_track, x, y, distance_from_center, car_orientation, progress, steps, throttle, streering, track_width, waypoints, closest_waypoint):

    import math
    
    marker_1 = 0.2 * track_width
    marker_2 = 0.5 * track_width
    marker_3 = 0.8 * track_width

    # If the vehicle's distance from the track center is less than 20% of the track width, the output reward is 10    
    # If the distance is greater than 20% and less than 50% of the track width, the reward is 3
    # If the distance is greater than 50% and less than 80% of the track width, the reward is 1    
    # If the distance is greater than 80% of the track width, which is assumed to be crashed or oﬀ the track, the reward is 0.01    
    if distance_from_center >= 0.0 and distance_from_center <= marker_1:
        reward = 10
    elif distance_from_center <= marker_2:
        reward = 3    
    elif distance_from_center <= marker_3:
        reward = 1
    else:
        reward = 1e-2  # likely crashed/ close to off track
    
    waypoint_yaw = waypoints[closest_waypoint][-1]
    
    # penalize reward if orientation of the vehicle deviates way too much when compared to ideal orientation
    if math.abs(car_orientation - waypoint_yaw) >= math.radians(5):
        reward *= 0.5
    
    return float(reward)
```

### AWS sagemaker & AWS robomaker 환경 적응하기
- 익숙해지면 공부한 내용 정리해서 발표
- 연습 Model 만들어보기.
