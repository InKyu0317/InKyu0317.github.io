---
layout: page
title: study note about ROS on AWS
---

### Research note about Amazon Deepracer

### Reference
[DeepRacer latest developer guide](https://docs.aws.amazon.com/deepracer/latest/developerguide/awsracerdg.pdf#%5B%7B%22num%22%3A565%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C72%2C416.96%2Cnull%5D)

[Deepracer workshops](https://www.slideshare.net/AmazonWebServices/new-launch-repeat-1-aws-deepracer-workshops-a-new-fun-way-to-learn-reinforcement-learning-aim206r1-aws-reinvent-2018)

[RoboMaker로 DeepRacer 자율주행차 만들기](https://www.youtube.com/watch?v=v5GBUpVkZbY)

### Deepracer 컨셉
- AWS deepracer
  - 1:18 스케일, mounted camera, on-board compute module
  - The module can run inference(추리) against a deployed reinforcement learning model in order to drive itself along a track. The compute module and the vehicle chassis are powered by dedicated batteries known as the compute battery and the drive batter
  - 시뮬레이터에서 강화학습 모델 만들기 -> 경주 트랙 시뮬레이션에서 모델을 평가 <br>-> 하이퍼파라메터를 튜닝, 훈련을 해 랩타임 줄이기 -> 딥레이서 리그 경기 출전
  - <img src="../images/ARC_1.png" alt="drawing" width="900"/>

### Reinforcement Learning (강화학습)

- [팡요랩 - 강화학습 강좌](https://www.youtube.com/playlist?list=PLpRS2w0xWHTcTZyyX8LMmtbcMXpd3s4TU)

- [Reinforcement-Learning Basic](https://www.youtube.com/watch?v=2xATEwcRpy8)

- Reinforcement Learning<br>
<img src="../images/RL_1.png" alt="drawing" width="600"/>

- Agent and Environment<br>
<img src="../images/RL_2.png" alt="drawing" width="600"/>

- Agent 는 Environment 에게 State 를 받고 Action 을 제출하게 되면 그에따른 보상을 제공 받는다.
- 그 보상을 최대치로 받는게 목표가 될수있다.

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

### AWS sagemaker & AWS robomaker 환경 적응하기

### Reinforment Learning 
