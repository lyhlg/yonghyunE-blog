---
title: 'about'
date: 2020-10-06
lang: 'ko'
---

# 개발자 이용현

<div align="right"><a href="mailto:lyhlg0201@gmail.com"><h5>lyhlg0201@gmail.com</h5></a></div>

> 타인에게 **영감**이 되고,
>
> > 자신에 대해 **겸손**하며,
> >
> > > 항상 다른사람을 **배려**하며,
> > >
> > > > **소통**을 잘하는 개발자가 되자.

<br />
<br />

# <u>Career</u>

## (주)에어프레미아

<div align="right">
  <h4>2020.01 ~ 현재</h4>
</div>

**<u>웹/모바일 에어프레미아 항공권 예매 페이지 신규 구축 개발</u>**

### 웹/모바일 신규 프로젝트 개발

#### 웹 데스크톱 프로젝트

1. 프로젝트 초기 구축
   - NextJS, 컨벤션(Lint, Directory 구조, Core 모듈)
2. 페이지 개발 및 기능 구현
   - Auth
   - Ticket
   - Dark site
   - Notice

#### 웹 모바일 프로젝트

1. 프로젝트 초기 구축
   - React, Webpack, 컨벤션(Lint, Directory 구조, Core 모듈)
2. 페이지 개발 및 기능 구현
   - Auth
   - 안내 Page
3. CapacitorJS 도입

#### 공통

1. Design 시스템 구축 및 Atomic Architecture를 통한 컴포넌트 개발
   - Atom, Molecules, Organisms, Template, Page 구조 구축
   - 모든 컴포넌트를 Storybook과 1:1 매칭
2. 컴포넌트 최적화를 위해 useMemo와 useCallback 주로 활용
3. MVVM 패턴을 이용한 프로젝트 구성
4. 국제화 도입
   - React-i18next 셋업 및 적용
5. form 상태 관리
   - React-hook-form 셋업 및 적용
6. 마케팅 페이지 유지보수 (NextJS)

<br/>

##### 기술스택

```bash
$ NextJS, React, Redux, Redux-Saga, Storybook, Webpack, Typescript, Styled-component, Axios, React-i18next, CapacitorJS
```

<br />
<br />

## (주)팍스닥

<div align="right">
  <h4>2018.04 ~ 2020.12</h4>
</div>

**<u>현물 / 선물 비트코인 다국어 거래소 셋업 및 유지보수</u>**

### 웹/모바일 신규 프로젝트 개발 및 유지보수 및 팀 리딩 (Nexybit/MAP)

#### 데스크톱과 모바일 페이지의 현물, 선물, 채굴형거래소 개발 / 코인 세일 (IEO) 페이지 개발 - _Nexybit_

1. 실시간 데이터를 위한 Websocket 구축
   - Ticker / Depth / Confirm / Filled
2. 비지니스 로직과 UI 로직을 구분
   - 비지니스 로직과 UI 로직을 구분 짓기 위하여 React - Redux에 비지니스 로직에 맞게 분리
3. Webview (Cordova)를 통한 모바일 개발 및 유지보수
4. 웹과 모바일 프로젝트에서 공통으로 사용하는 데이터를 위해 GIT Submodule 도입
5. 디렉토리 구조를 비지니스 로직에 맞도록 재 설계 (Container Presenter Pattern 적용)
6. 다국어 기능 개발 (한국어, 영어, 일본어, 중국어)
7. 팀 Leader 업무 수행

#### M&A Platform 초기 셋업 구축 및 유지보수 - _MAP_

1. 신규 프로젝트로서 번들링 작업 부터 원활한 Coworking을 위한 Lint, git hook등을 구축
2. 데스크톱 및 모바일 환경 구축
3. 페이지 개발 및 기능 구현
   - Auth 기능 개발
   - M&A 프로젝트 기능 개발
4. 다국어 기능 개발 (한국어, 영어, 일본어, 중국어)
5. MVVM 패턴을 이용한 프로젝트 구성

<br />

##### 기술스택

```bash
$ React, Redux, Redux-Thunk, Redux-Saga, Websocket, Webpack, SCSS, Axios
```

<br />
<br />

## (주)파이오링크

<div align="right">
  <h4>2014.11 ~ 2017.11</h4>
</div>

**<u>L7 웹방화벽 네트워크 구축 및 유지보수 지원 엔지니어</u>**

### 웹방화벽 엔지니어 업무 수행

1. L2, L4, L7 기본 지식 학습 및 자사 장비를 통한 이해
2. 웹방화벽 장비 설치 및 장애시 장비 Trouble shooting
3. 자사 사내망 구축 및 유지보수
4. Lagacy 환경 구축 미팅 참여, 망 구성 협의, 운영자 교육 및 설치 사 유지보수 업무 수행
5. 웹방화벽 엔지니어로서 장비 웹 보안 설정, OWASP10에 의거한 장비 보안규칙 설정 수행
6. 웹방화벽 보안 로그 분석

<br />
<br />
<br />
<br />

# <u>Project</u>

## Havit

<div align="right">
  <h4>2018.02 ~ 2018.03</h4>
</div>

**<u>병원-고객간 피부과 웹 어플리케이션 중개 플랫폼 구축</u>**

### 웹 신규 프로젝트 개발

#### 고객 제품 구매 페이지 및 어드민 페이지 개발

- 서버구축 (Node+Express+GraphQL)
  - 서버 구축 및 GraphQL로 API Setting을 하여 CRUD 기능 구현
- 데이터베이스
  - CRUD를 위해 MongoDB를 사용하였고 Schema 를 정의 하기 위하여 Mongoose를 사용
- 배포
  - AWS EC2를 이용하여 프로젝트 배포
  - 각종 Image는 AWS S3 사용하여 관리
- 인증
  - 각종 Social Login 연동 (Kakao, Gogole, Naver, Facebook)
- 기획
  - 해당 프로젝트는 모든 기획부터 개발까지 진행함
  - Text로 구조잡기, Mock-up, Story board화 하는 기획 단계를 통해 프로젝트의 기반을 잡고 개발 진행

##### 기술스택

```bash
$ React, Node, Express, MongoDB, Mongoose, GraphQL, AWS EC2, AWS S3
```

<br />
<br />
<br />
<br />

# <u>Additional Learning</u>

## 코드스테이츠

<div align="right">
  <h4>2018.10.10 ~ 2019.03.16 (6개월)</h4>
</div>

## 학습내용

1. Hack Reactor 기반 교육 과정 수료 (Pre course / Immersive course)
2. 자료구조 (Stack, Queue, LinkedList, Tree 등) 학습
3. 자료구조로 배운 이론 뿐만 아니라 기본적인 알고리즘 학습
4. Javascript에 대한 기초 및 ES 문법에 대한 이해
5. React와 같은 Frontend 프레임 워크에 대한 이해
6. Backend 시스템에 대한 이해 (Restful, SQL, NoSQL, Data Fetching 등)
7. 8주 팀 프로젝트 진행 (havit project)

<br />
<br />
<br />
<br />

# <u>Tech Stack</u>

- HTML
- CSS, SCSS, CSS in JS (Styled-component)
- Typescript(Javascript)
- React, Redux, Redux-thunk, Redux-saga, NextJS
- Storybook
- Webpack
- GIT, GIT Submodule, GIT Flow
- Atomic Architecture
- Jest
- Zeplin, Bitbucket, Jira, Slack ...
