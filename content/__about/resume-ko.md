---
title: 'about'
date: 2020-10-06
lang: 'ko'
---

# 개발자 이용현

<div align="right">
   <a href="https://github.com/lyhlg">
      <span>Github  </span>
   </a>
   <a href="https://ian-note.dev/">
      <span>Blog  </span>
   </a>
   <a href="mailto:lyhlg0201@gmail.com">
      <span>Mail</span>
   </a>
</div>

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

## (주)힐링페이퍼
<div align="right">
  <h4>2020.12 ~ 현재</h4>
</div>

### 강남 언니앱 내 한국/일본 이벤트 신청 웹뷰 개발
> 이벤트 신청 신규 기능 도입, 한국 일본 내 병원 중 예약병원 수 확보 및 지속적인 병원 유치를 위한 신규 및 보수 개발
1. 이벤트 예약 신청 페이지 개발
2. 이벤트, 병원 예약 상태에 따른 분기 페이지 제공
3. 앱과 웹의의 의존성을 제거하고, 앱/웹 개발자간의 종속을 최소화를 지향한 구조로 구현
4. 한국/일본 다국어 서비스 구축
5. 데이터 독을 이용한 디버깅 할 수 있는 환경을 구축
6. 앰플리튜드를 이용한 유저 행동 분석 및 예약까지의 퍼널 개선
   - 상담신청 이후 예약 전환을 가져가는 테스트에서도 고객이 실수로 이탈하는 문제가 발생하는 것을 발견하고 부분을 해결하고 약 10% 상승 효과를 봄
7. A/B Test를 통해 가설에 대한 지속적인 검증
   - 예약 가능 일정을 3개 제출 하는 것과 1개를 제출할 때, 예약까지의 여정을 완료하는 수치가 10% 상승하여 B안을 선택 하여 운영

### 강남 언니 병원 관리자 어드민 프로젝트 셋업, 신규 기능 도입 및 유지보수
> 어드민 페이지를 React로 개편 및 어드민 프로젝트에 맞도록 도메인 설계
1. 신규 도메인은 React로 개발하기 위하여 초기 셋업 진행
   - 신규 프로젝트의 infra 및 도메인 분기 구조 셋업
   - Frontend Service Model을 정의 및 구현
   - Test code 작성
     - UI component, Front Service Model, API Model
2. 한국/일본 예약(확정예약/대기예약 방식)신규 기능 도입
3. 데이터 독을 이용한 디버깅 할 수 있는 환경을 구축
4. 다국어 서비스 구축
5. 기존 Vue로 구성된 페이지 유지보수

### 강남언니 디자인시스템 참여 및 개발
> 고객 Product, 병원 Product에 사용되는 디자인 시스템 구축에 적극적인 드라이브 및 높은 기여
1. 강남언니 앱(ios / android)과 웹에서 공통으로 사용되는 cell 디자인 시스템 스펙 정의 및 구현
   - 디자인 스펙은 디자이너와 프런트엔드개발자가 동반되어 스펙 정의
2. 강남언니 어드민에서 사용되는 welchis 디자인 시스템 스펙 정의 및 구현
   - 개인적으로 Snackbar Component는 [npm 등록](https://www.npmjs.com/package/react-snackbar-ui-customizable)하여 관리
   - [Snackbar 구축 관련 블로그](https://ian-note.dev/developer/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%8A%A4%EB%82%B5%EB%B0%94-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%A0%9C%EC%9E%91%ED%95%98%EA%B8%B0/)
3. 작성되는 디자인 시스템 컴포넌트에 대해 테스트
   - Component unit test 진행 (jest, testing-library)
   - 디자이너분들의 QA를 위해 Storybook chromatic 으로 Feedback 채널 구축
4. 구축된 디자인 시스템(cell, welchis)은 npm private repository 운영

### 병원 웹 사이트 신규 구축
> 병원의 초기 구축에 필요한 Product 개발, 현재 개발 완료 되었고, 강남언니 내의 높은 랭크에 있는 병원으로 자리 잡음
1. Design system 구축 (fill Design system)
   - 초진 설문지와 평가시스템에 사용되는 공통 컴포넌트를 개발
   - vue 기반 병원 DS시스템 구축

2. 초진 설문지 구축
   - 기존 병원들은 병원에서 초진 설문지를 종이로 작성하는 과정을, 병원 고객이 방문전에 미리 초진 설문지를 웹 URL로 받고 방문시 빠르게 진료를 받을 수 있는 시스템을 구축
   - 미리 공통 컴포넌트를 구축된 Design system을 활용하여 개발

3. 평가 시스템 구축
   - 병원 고객의 피드백을 위해 서비스를 이용한 고객들에게 병원 평가 후기를 작성할 수 있도록 하는 시스템 구축
   - 미리 공통 컴포넌트를 구축된 Design system을 활용하여 개발

4.  병원 홈페이지 구축 (mobile) - https://gu.clinic
    -  병원 홈, 이벤트, 시술 예약, 둘러보기, 시술 카트 기능을 담은 웹 사이트 구축
    -  NextJS 프레임워크를 도입하여 SEO를 고려하여 개발
    -  MVVM 모델링을 하여서 전반적인 시스템을 구축
    -  View는 atomic design system을 이용하여 구축
    -  amplitude를 연동하여 사용자 행동 분석
       -  각종 product(이벤트 또는 시술 상품)에 대한 분석
       -  예약 완료 까지의 여정 분석
    -  서버와의 통신을 protobuf를 사용함으로서, api spec 문서를 proto interface로 정의하여 사용
    -  storybook을 이용한 UI 테스트 및 @testing-library/react를 이용하여 interface 테스트를 진행
    -  유저 로그인 정보 없이 카트 정보를 기억 하기위해 redux로 구축 하였고, localStorage를 이용하여 사용자가 담은 시술상품을 기억하도록 관리


### 프런트엔드 챕터 리드
> 챕터 구성원의 성장, 챕터내의 프로젝트가 성과로 반영 될 수 있는 계획 수립
1. 프런트엔드 챕터의 2022 목표를 중장기적으로 수립 및 수행
   - 신규 프로덕에 대해서 NuxtJS -> NextJS 전환 목표
   - 프런트엔드 배포 프로세스 개선
      - PR pre-build, pre-test, convention check, tag version 관리
   - 디자인 시스템 보완 및 재 구축
2. 공통 모듈 선 제작 및 공유
   - A/B Testing Component
   - 개발 환경에 필요한 파일 그룹을 자동으로 생성해주는 script
   - 신규 프로젝트 초기 구조 설계
   - 캘린더와 같은 자주 쓰이는 컴포넌트를 UI가 없는 Headless component로 구현 하여 기능 재사용을 할 수 있도록 제공
<br />
<br />
<br />
## (주)에어프레미아

<div align="right">
  <h4>2020.01 ~ 2020.11</h4>
</div>

**<u>웹/모바일 에어프레미아 항공권 예매 페이지 신규 구축 개발</u>**

### 웹/모바일 신규 프로젝트 개발
1. 웹 데스크탑 프로젝트
   - 프로젝트 초기 구축
     - NextJS, 컨벤션(Lint, Directory 구조, Core 모듈)
   - 페이지 개발 및 기능 구현
     - 인증화면, 티켓팅화면, 공지사항 등
2. 웹 모바일 프로젝트
   - 프로젝트 초기 구축
     - React, Webpack, 컨벤션(Lint, Directory 구조, Core 모듈)
   - CapacitorJS 도입을 통해 웹앱 개발

3. 에어프레미아 디자인 시스템 구축
   - Atomic Architecture를 기준으로 컴포넌트 단위를 설계
   - 모든 컴포넌트가 Storybook UI Testing이 될 수 있도록 구성
4. MVVM 패턴을 이용한 프로젝트 구성
5. 국제화 도입
   - React-i18next 셋업 및 적용

### 마케팅 페이지 유지보수
1. 마케팅에 사용되는 Nextjs로 구성된 페이지 유지보수

<br/>
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
4. 웹과 모바일 프로젝트에서 공통으로 사용하는 데이터를 위해 Git Submodule 도입
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
- React-query
- Recoil
- Storybook
- Webpack
- GIT, GIT Submodule, GIT Flow
- Atomic Architecture
- Jest, testing-library/react, MSW
- AzureDevOps, Figma, Zeplin, Bitbucket, Jira, Slack ...

