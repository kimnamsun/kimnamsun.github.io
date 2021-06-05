---
layout: post
title: "Sunfume Project"
info: "향수, 바디용품 커머스 앱 제작 개인프로젝트"
tech: "HTML5, Tailwind.css, javascript(ES6+), Typescript, React, Framework7, Formik&Yup, React query, Recoil, Ruby on rails, Redis, Postgresql"
type: Frontend & Backend
---

![Sunfume](https://images.velog.io/images/nsunny0908/post/5eb6a541-4780-4d66-9d87-7de511375b91/E44111BF-44DF-407C-8ED5-1879F84BC96F-tile.png)
![Sunfume2](https://images.velog.io/images/nsunny0908/post/e16787a4-5899-4034-aa10-37d6b4169d92/09E6733B-9AB0-4244-8E52-B491664438B0-tile.png)

<br />

## Description

향수, 바디용품 커머스 앱 제작 개인프로젝트

<br />

## What did I do

### Frontend

- api config를 활용해 api요청 관리
- react query를 이용한 서버 상태 관리
- Typescript를 이용해 타입 강제
- Recoil를 이용한 전역 상태 관리
- Formik & Yup을 이용한 로그인 / 로그아웃
- Formik & Yup을 이용한 회원가입
- 마이페이지
  - 회원정보 수정
  - 주문 내역 조회
- 상품 리스트
  - 상품 정보
  - 인피니트 스크롤
- 상품 상세
  - 상품 정보 조회
  - 옵션 선택 후 장바구니 담기
  - 찜하기
  - 해당 상품에 달린 리뷰 조회
- 카테고리
  - 카테고리 리스트
  - 카테고리별 상품 모아보기
  - 최신순, 가격 낮은 순, 가격 높은 순 필터링
- 찜목록
  - 찜한 상품 리스트
- 장바구니
  - 장바구니에 담은 상품 리스트
  - Recoil atom과 selector를 이용한 수량 조절 및 주문 금액 표시 기능
  - 장바구니 상품 삭제 기능
- 주문
  - 다음 주소 api를 이용한 주문서 작성 기능
  - 주문 버튼 클릭 시 결제 및 주문 완료 처리

### Backend

- 데이터베이스 모델링

- 상품 리스트 조회
- 상품 상세
  - 상품 상세 정보 조회
  - 옵션 선택 후 장바구니 담기
  - 상품 찜하기, 찜삭제
  - 해당 상품에 달린 리뷰 조회
- 카테고리
  - 카테고리 리스트
  - 카테고리별 상품 모아보기
  - Ransack과 Ransacker를 이용한 최신순, 가격 낮은 순, 가격 높은 순 필터링
- 장바구니
  - 장바구니에 담은 상품 리스트 조회
  - 장바구니에서 수량 조절 시 lineItem update
  - 장바구니 상품 삭제 기능
- 회원정보 조회 및 수정
- 주문 내역 조회
- 찜한 상품 리스트 조회
- 주문
  - enum을 이용한 order의 상태관리 (주문중: pending, 주문완료: active, 주문취소: disabled)

<br />

## Tech Stack

### Frontend

- HTML5, Tailwind.css, javascript(ES6+), Typescript, React, Framework7, Formik&Yup, React query, Recoil

### Backend

- Ruby on rails, Redis, Postgresql

<br />

[Frontend Github](https://github.com/kimnamsun/sunfume_frontend)  
[Backend Github](https://github.com/kimnamsun/sunfume_backend)
