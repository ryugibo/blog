---
title: "[노개북 TIL] IT 5분 잡학사전 #9"
date: 2023-01-25 13:30:00+0900
categories: [노마드코더, 북클럽]
tags: [nomadcoders, TIL, IT 5분 잡학사전]
---

## 오늘 TIL 3줄 요약

---

> - REST API를 구성할 땐 URL에서 동사를 제외하자
> - 도커 컨테이너를 구성해두면 서버 배포를 쉽게 확장할 수 있다.
> - 하이브리드 앱은 웹을 만드는 것처럼 앱을 만들수 있지만 기기를 활용하는데 한계가 있다.

## 오늘 읽은 범위

---

- 에피소드 39. 인공지능, 머신러닝, 딥러닝, 아직도 구분하기 힘들다고?
- 에피소드 40. REST API라니, 휴식 API인가? 이게 대체 뭐죠?
- 에피소드 41. 도커가 뭐지? 왜 필요할까?
- 에피소드 42. 암호화폐의 진실
- 에피소드 43. 하이브리드⋯앱? 뭐라고요?
- 에피소드 44. NFT가 도대체 뭐길래?
- 에피소드 45. 멀웨어, 바이러스, 웜 개념 몽땅 정리

## 책에서 기억하고 싶은 내용

---

### 에피소드 39. 인공지능, 머신러닝, 딥러닝, 아직도 구분하기 힘들다고?

- 현재 인공지능 기술은 좁은 인공지능으로 한가지 일만 잘한다.
- 머신러닝은 인공지능을 학습시키는 방법.
- 딥러닝은 비지도학습의 종류로 머신러닝의 한 종류.

### 에피소드 40. REST API라니, 휴식 API인가? 이게 대체 뭐죠?

- REST API는 API의 한 방식으로 URL을 특정 조건으로 구성한다.
  - URL에서 동사 제외하기
  - HTTP 메서드 도입하기
- 1개의 URL로 조회, 생성, 수정, 삭제 처리를 할 수 있고, 기능 확장하기 편해진다.
- 특정 조건을 주가하고자 하는 경우 쿼리 파라미터를 도입한다.

### 에피소드 41. 도커가 뭐지? 왜 필요할까?

- 도커는 어떤 컴퓨터에서도 같은 개발 환경을 준비할 수 있도록 해주는 도구이다.
- 도커가 준비한 환경을 컨테이너라고 한다.
- 도커 컨테이너를 준비해두면 서버를 쉽게 확장할 수 있다.

### 에피소드 42. 암호화폐의 진실

- 암호화폐는 네트워크라서 없애려면 모든 인터넷 연결이 끊어져야한다.
- 암호화폐는 사용자가 직접 은행이 되어 보관하는 역할을 스스로 해야한다.
- 암호화폐는 모든 정보가 공개된다.

### 에피소드 43. 하이브리드⋯앱? 뭐라고요?

- 하이브리드 앱은 사실 웹 사이트를 보여주는 웹 뷰를 말한다.
  - [장점] 네이티브 앱 개발 지식이 필요없다.
  - [단점] UI를 모두 직접 만들어야한다.
  - [단점] 기기의 모든 기능을 활용할 수 없다.
- 크로스 플랫폼 앱은 특정 언어로 만들면 나중에 iOS, 안드로이드로 변환해서 앱을 만든다.
  - [장점] 익숙한 코드로 로직읋 한번만 작성하면 된다.
  - [단점] 네이티브 앱보다 성능이 떨어진다.
- 네이티브 앱은 iOS나 안드로이드가 사용하는 언어로 개별로 만든다.
  - [장점] 기기의 성능을 최대로 사용할 수 있다.
  - [단점] iOS, 안드로이드 두가지 플랫폼에서 요구하는 언어를 모두 배워야 한다.

### 에피소드 44. NFT가 도대체 뭐길래?

- NFT는 non fungible token의 줄임말이고 대체 불가능하다는 것을 말한다.
- NFT는 유일한 원본이라는 보증을 하는 것으로 가치를 높여준다.

### 에피소드 45. 멀웨어, 바이러스, 웜 개념 몽땅 정리

- 멀뭬어(malware)는 malicious(악의 있는)과 software(소프트웨어)의 합성어이다.
- 멀웨어 중에선 바이러스(virus)와 웜(worm)이 가장 유명하다.
- 바이러스는 숙주가 되는 파일이 필요하다.
- 웜은 숙주가 필요 없이 스스로 복제하면서 전파된다.
- 웜은 미사일(missile)과 페이로드(payload)로 구성되어 미사일을 통해 침투하고 페이로드를 배포해서 컴퓨터를 파괴한다.

## 오늘 읽은 소감은?

---

- REST API에 대한 설명이 Request, Response에 대한 내용 없이 설명되어있어서 모르고 읽으면 무슨 소리지 싶을 것 같다.. 그래도 REST API를 이쁘게 구성하는 방법에 대한 간단한 설명은 좋다.