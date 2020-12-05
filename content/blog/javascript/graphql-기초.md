---
title: graphQL 기초
date: 2020-12-05 17:12:56
category: javascript
thumbnail: { thumbnailSrc }
draft: true
---

# 기존 Rest API의 단점

1. Over-Fetching: 너무 많은 데이터 (원하지 않는 데이터)를 받아오게 된다.
2. Under-Fetching: 한 endpoint 호출에 대한 응답 데이터가 충분하지 않아 여러개의 API를 요청해야 할 수 있다.
3. Rest endpoint 관리: 여러 환경에서 필요한 정보들을 Resource별로 모두 endpoint작업하는 것이 번거롭고 어려움 추가로 Spec 문서화 작업도 매번 해줘야 하는 번거로움이 있음

# GraphQL 이란

1. Facebook의 오픈소스로서, 새로운 API 표준
2. 선언적인 데이터 fetching을 할 수 있다. (Query Language)
3. GraphQL 서버는 하나의 endpoint를 가지며 query들로 응답한다.

# 동작방식

1. client는 원하는 데이터를 받기 위하여 쿼리 형태로 작성하여 서버의 endpoint에 요청한다.
2. server는 client요청이 **Query(Read)**인지 **Mutation(Create, Update, Delete)** 인지를 판단하여, 각각의 요청을 Database를 통해 처리한다.
3. 처리후의 response를 Query 형태로 client에게 전송하게 된다.
