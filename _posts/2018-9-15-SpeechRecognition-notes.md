---
layout: post
title: Speech Recognition notes
---

# Recent research about open source speech recognition libraries

## What is the issue?

the app i am developing requires
* a coustomized hotword(keyword) detection
* korean text to korean speech
* korea speech to korean text

## Hotword detection (Continuous Speech Recognition)

* Snowboy (KITT.AI)
  * customizable hotword detection engine for you to create your own hotword like "OK Google" or "Alexa"
  * DNN (deep neural networks)
  * can customize model(personal, private) from https://snowboy.kitt.ai/ (login, korean keyword is okay)
  * always listening (record thread can run on foreground service) https://stackoverflow.com/questions/50956228/thread-within-service-android-app
  * no internet required
  * Light-weight (if there noise around, CPU usage may increase) 
  * Supports various platforms and programming languages
  * Need a commercial license (Please contact snowboy@kitt.ai)
  * Android Demo https://github.com/Kitt-AI/snowboy/tree/master/examples/Android
  
* Porcupine (Picovoice) https://github.com/Picovoice/Porcupine
  * Alireza Kenarsari (Founder at Picovoice) says porcupine has lower miss rate than snowboy
  * https://github.com/Picovoice/wakeword-benchmark
  * https://medium.com/@alirezakenarsarianhari/yet-another-wake-word-detection-engine-a2486d36d8d4
  * but when i really try it, snowboy worked better on my development environment (I may need to try more models)
  * AAR style library
  * Provides (Standard, Tiny) version
  
* PocketSphinx
  * https://cmusphinx.github.io/wiki/tutorialandroid/
  * demo: https://github.com/cmusphinx/pocketsphinx-android-demo

## Speech to Text & Text to Speech (Korean)

* kaldi http://kaldi-asr.org/ Kaldi is a toolkit for speech recognition written in C++

* Zeroth Project https://github.com/goodatlas/zeroth (Kaldi based)
  * MoreCoin: a mobile app to collect voice data from various users https://play.google.com/store/apps/details?id=com.goodatlas.morecoin
  * Explanation of how korean speech recognition works: https://github.com/goodatlas/zeroth/tree/master/s5/data/local/lm
    * Multi layer structure to analyze voices
    * explain the difference between English and Korean
  * using AWS server, web crawler to collect 13GB pronounciation dictionary and language models

* KaKao API (Newton API) https://developers.kakao.com/docs/android/speech 20,000 requests free
  * provides both STT & TTS
  * reaserch of open source API(Korean): http://jse.or.kr/AJMAHS/papers/v7n8/38.pdf 
  * good quality of speech

* Naver Clova Speech Recognition API (STT): https://www.ncloud.com/product/aiService/csr , 4 Won / 15sec
* Naver Clova Speech Synthesis API (TTS): https://www.ncloud.com/product/aiService/css , 4 Won / 1000chars

* CMUsphinx
  * How to use other languages? https://cmusphinx.github.io/wiki/faq/#q-how-to-add-support-for-a-new-language 
  * Need Korean acoustic model, language model

* Amazon Lex (STT) & Polly (TTS)
  * Maybe we can use third party language translation soulution
  * IoT solution: https://www.dropbox.com/s/om0x7vgsenghfer/aws-iot-solution-example.PNG?dl=0

* IBM watson (SK NUGU use this API: http://www.newspim.com/news/view/20170206000145)
  * STT: https://console.bluemix.net/docs/services/speech-to-text/getting-started.html#gettingStarted
  * TTS: https://console.bluemix.net/docs/services/text-to-speech/getting-started.html#gettingStarted


 
