---
date: 2022-11-01T23:48:05.000Z
layout: post
title: Welcome to yejifolio
subtitle: '앞으로 더 업데이트 될'
description: >-
 study posting~11/15
 project 12~
image: >-
 ![image](https://user-images.githubusercontent.com/115096296/197876820-6ebede40-fcd9-4d35-b0e6-e8a5bedffe50.png)

optimized_image: >-
  https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559821647/theme6_qeeojf.jpg
category: blog
tags:
  - welcome
  - blog
author: yeji
paginate: true
---
 #study posting~11/15
 #project 12~
## 계층형 아키텍처의 이해
-SW도 실제 코드 개발 전에 최종 SW가 되어야 할 모습을 설계 함
■ SW 아키텍처란, SW의 구조를 정의한 것으로 SW를 구성하는 주요 요소들과
요소들의 관계를 정의한 것

### ■ SW를 서로 다른 역할을 하는 3 〜 4개 계층으로 구분
一 Presentation Layer
-   Application Layer
一 Business Layer
-   Data Access Layer

■Client（웹 브라우저, 모바일 앱）의 요청을 받고 
■Application Layer에 요청에 대한 처리를 위임하며 
■Client에 최종 응답을 하는 역할
-   view: Client가 요청에 대한 응답의 결과로 보게 되는 웹 페이지 -   data: Client가 요청에 대한 응답으로 받는 데이터


### Controller 코드
■ Spring Controller를 구현하기 위해서는 3개의 기본 Annotation이 사용 됨 ■ @Controller와 @RestController
一 Controller 역할을 하는 클래스를 지정, 클래스 상단에 명시 
■ @RequestMapping
- 특정 Request 처리하는 메소드를 지정, 클래스 또는 메소드 상단에 명시

### Annotation 이란
■ Java 소스코드에 추가적인 정보를 제공하는 방법
■ @으로 시작하며 클래스, 메소드, 멤버변수, 파라미터 등에 부착 가능 
■ 3가지 유형의 Annotation
-  자바 컴파일러에게 정보를 제공（에러 등을 찾아내기 우I해） 
-   SW 툴에 의해 사용되어 코드 생성이나 추가 작업을 진행
-   run-time 시 특정 동작을 추가적으로 실행


### Controller 코드
■ Framework 활용은 규칙을 지키는 것
■  약속 된 Annotatiorr들을 Spring Framework 스캔
■Annotation이 부착 된 코드들은 Spring Framework에 의해 관리 되며, Spring Framework에 의해서 특정 한 목적으로 사용 됨


```java
0Controller
public class HelloController { (SRequestMapping (value =
public String helloO { return "index";
I} }
```
```java
(3RestControHer
public class HelloControHer {
(^RequestMapping (value = /) public String hello() {
return "index"; }
}
```


## ©Controller vs @RestController
■  대부분의 동작은 유사
- 요청을 받아서 처리하고 응답을 한다 ■  응답하는 형태가 다름
一 Controller: view를 응답（html 파일 등）
一 RestController: data를 응답（문자열, Json, xml 등

■ Controller는 계층형 아키텍처에서 Presentation Layer의 요청과 응답 처리의 역할을 담당
■ @Controller, @RestController, @RequestMapping이 기본 Annotation으로 사용됨
■ Annotation은 SW 코드에 추가적인 정보를 제공하는 방식이며, Spring Framework은 약속 된 Amotation을 인식하여 특정 작업을 수행
■ @Controller은 HTML 파일과 같은 view를 @RestController는 문자열, JSON 등의 데이터를 응답 함

### @RequestMapping
■ RequestMapping이 붙어 있는 메소드 는 Client의 특정 요청이 왔을 때
Spring Framework에 의해 호출 됨
■ RequestMapping이 붙어 있는 메소드 가 여러 개 일 때는 어떤 메소드가 호출 될까?

Controller 클래스에 @RequestMapping 활용
■ 특정 Controller 클래스 내부의 모든 메소드에 Path를 적용

## HTTP API의 개념

### API(Application Programming Interface)
■ Interface란 두 개체 간의 정보를 공유하기 위한 방법（규약）

■ API는 컴퓨터（프로그램）간의 정보를 공유하기 위한 방법 -  함수나 메소드를 호출하는 형식의 API
-   HTTP등의 기술로 네트워크를 통한 원격 자원을 호출하는 API


### HTTP API vs REST API
■ HTTP(S)를 활용하여 원격의 데이터를 공유하기 위한 API
- HTTP API 
■ REST API

-  다양한 조건이 만족되어야 하며, 실무에서 모든 조건을 만족하여 구현하기 어려움 
-  주로 REST API 명칭이 사용 됨 -  엄밀하게는 서로 다른 개념


### HTTP API vs REST API
■ @RestController Annotation은 REST API, HTTP API를 위한 클래스를 명시 하는것
■ @RestController 클래스 내의
@RequestMapping이 붙은 개별 메소 드들이 하나의 REST API, HTTP API

Server에 요청 시에도 추가적인 Data가 필요


### Request 파라미터
■Client가 Server에 요청(Request)를 할 때 추가적으로 전송하는 데이터
■ 2가지 유형의 Request 파라미터
-   Query String -   Path Parameter
■ Spring Framework는 Request 파라미터를 메소드의 파라미터에 저장

### Request 파라미 터 - Query String의 활용
■  메소드 파라미터에 @ Request Pa ram Annotation 사용 
■ name 요소는 Query String에 key에 매핑 됨

### Request 파라미 터 - Query String의 활용
■ @RequstParam에 요소들
-   name: query string의 key, key와 변수명이 같을 경우 생략 가능 
-   required: 필수 여부
一 defaultvalue: 데이터가 없을 경우 기본 값


### Request 파라미 터 - Path Parameter
■ @RequestMapping value UR|O|| {}로 Path Param임을 표시
■ 메소드 파라미 터에 @PathVariable Annotation 사용
■ 선택적 데이터의 경우에는 Path Param을 잘 사용하지 않음


### Query String vs Path Parameter
■ 일반적인 추천 사항
-  특정 자원을 요청 하는 경우는 Path Param을, 정렬이나 추가 필터링을 위한 데이터는 Query String 사용
-   https://codepresso.kr/courses/spring?order=latest
■ 필수 데이터는 Path Param으로 선택적 데이터는 Query String 사용 一 Path Param이 포함 된 URI는 Client가 영향을 받기 때문에 변경 비용 높음 - Query String은 상대적으로 편하게 확장 가능
■ 조직（회사 또는 팀）마다 표준이 존재하고, 표준에 따라 개발

### Client와 Server
■Client가 Server에게 요청을 하면
■ Server는 요청에 대한 처리를 한 후 결과를 응답함
一 단순 문자열, 이미지, 영상, HTML 페이지, JSON 등

### 요청 (Request) 응답(Response)
문자열 이미지 영상
HTML, JSON, ..


### Spring Controller와 Response 데이터
■Controller Annotation은 HTML 파일과 같은 view를 응답 
■ RestController Annotation은 메소드 반환 값 자체를 응답
- 단순 문자열, JSON


```java
@RestController
public class HelloController 
RequestMapping (value = public String hello() {
return "index"; }
```

### controller의 응답
```java
Controller
public class HelloController { (BRequestMapping (value =
public String hello() { return "hello11;
} 
```

### RestController의 응답 - 객체
■ 신규 클래스 생성
-   com.codepresso.controllertest.dto. UserDto
-  모든 멤버 변수 초기화 하는 생성자 추가
-  모든 멤버 변수에 대한 getter 메소 드 추가


```java
public class UserDto { Integer id; String name; String email;
List<String> specialties;
public UserDto(Integer id, String name, String email, List<String> specialties) { this.丄d = id;
this.name = name; th丄s.email = ema丄
this.specialties = specialties; public Integer getld() {
return id;
public String getNameO { return name;
public String getEmailO { return email;
public List<String> getSpecialtiesO { return specialties;

```
RestController의 응답 - 객체
■ UserDto 객체를 생성한 후 객체를 반환
```java
RestController
public class Usercontroller {
gRequestMapping(value = 必v"/use「") public UserDto getllser() {
List<String> specialties = new ArrayList<>(); specialties.add("Java");
specialties .add("Spring Boot11);
return new Use「Dto(l, "Jin", "jinpcodepresso.krN, specialties)}}
```


RestController의 응답 - 객체
■ 객체를 반환하면 JSON 형식의 데이터가 응답 됨


```java
{
"id": 1,
"name": "Jin"，
"email": "jin@codepresso.kr" "specialties": [
"Java",
"Spring Boot"
}
```

### JSON 응답 데이터
■ 웹 개발 시 가장 일반적으로 사용하는 응답 데이터 포맷
■ 프론트엔드에서는 JSON 형식의 데이터를 응답 받아 화면을 구성 
■ 각 REST API 별로 어떤 JSON 데이터를 응답할 것인지 사전에 정함
- 프론트엔드와 백엔드 모두 정해진 JSON 데이터에 맞게 구현


### JSON
■ JSON - JavaScript Object Notation 
■JSON는 데이터를 교환하는 데 사용
■ 기존의 방법(XML) 보다 가벼움
■XML에 비해 상대적으로 사람이 읽고 이해하기가 쉬움

```java

"id": 1, "name”: {
“first": "Donghun", "last": "Lee"
}

```

### JSON 문법
■ JSON의 value에는 다양한 형태의 데이터 타입 가능
一 문자열, 숫자, Boolean, null
一 JSON 객체(Object), JSON 배열(Array)
```java
"id”: 1,
“specialties": [
“Java", "Python”, "Spring" 1

```


### JSON 문법
■JSON 배열(Array)은 순서가 있는 데이터의 나열
- 대괄호([])로 표현
■JSON 배열은 다양한 데이터 타입 포함 가능
一 문자열, 숫자, Boolean, null
一 JSON 객체(Object), JSON 배열(Array)


### JSON 응답 예제
■ SpecialtyDto 클래스 생성
```java
public class SpecialtyDto { String name; String level;
public SpecialtyDto(String name, String level) { this.name = name;
this.level = level; public String getNameO {
return name; }
public String getLevelO {
return level;
}
```
### JSON 응답 예제
■ UserDto의 specialties 멤버 변수를 List<SpecialtyDto>로 변경
一 생성자, getter 변경
  
```java
  public class UserDto { Integer id; String name;
IList<SpecialtyDto> specialties;
public UserDto(Integer id, String name, String email,|List<SpecialtyDto> specialties)|{
this.id = id;
this.name = name;
this.email = email;
this.specialties = specialties;
  
  ```
JSON 응답 예제
■ UserController.getUser 메소드 수정
一 specialties 리스트에 문자열이 아닌 SpecialtyDto 객체를 저장
  
  
■Client/Server 구조에서 Server는 Client의 요청에 따라 적절한 처리를 한 후에 결과를 응답
■ Server는 단순 문자열, HTML, 이미지, JSON 등 다양한 형태의 데이터를 응답할 수 있음
■  최신 웹 개발 시 가장 많이 사용 되는 응답 포맷은 JSON 데이터 
 ■ Spring Boot에서는 객체를 반환하면 적절한 JSON 형식으로 변환하여
Client로 최종 응답 함
■JSON은 Key/Value 형식이며, 객체와 배열 등의 표현도 가능
  
### RequestBody이해
Request Data
■Client가 서버에 요청 시 전달하는 추가적인 Data ■  우리가 알고 있는 2가지 방식의 데이터 전달 방식
一 Query String -   Path Parameter
■ 크기가 큰 데이터를 보내기 위해서는 다른 방식이 필요
-  게시판 글, 작성 된 Form 데이터 등
  
### Request Body
■ 일반적으로 데이터를 저장 및 수정하는 POST, PUT Method에서 사용 됨
- GET, DELETE는 Query String, Path Param이 주로 사용
■ Request Body에 다양한 포맷의 데이터 전송 가능
- JSON 데이터 형식이 주로 사용 됨
■ Client에서는 JSON 데이터를 전송하고, Spring에서는 JSON 데이터를 Java 객체 파라미터로 저장

### Request Body의 활용
■ Postman에서 JSON 데이터를 Request Body로 전송
  
```java
public String savePost|(aRequestBody] PostDto postDto) {
System.out.printin(postDto.getld());
System.out.printin(postDto.getTitle());
System. out. println(postDto. getContentO);
System. out. println(postDto. getUsernameO);
return "POST /post";
```
  
## REST API 문서의 활용

### API 문서화
■API는 정보를 주고 받기 위한 방법/약속
■API를 사용하기 위해서는 사용 방법을 알아야 함 ■ API 문서는 API를 사용하는 방법을 명세한 문서
  
  
### >Method Detail
sin
public static double sin(double a)
Returns the trigonometric sine of an angle. Special cases:
•  If the argument is NaN or an infinity then the result is NaN.
•  If the argument is zero, then the result is a zero with the same sign as the argument.
The computed result must be within 1 ulp of the exact result. Results must be semi-monotonic.
Parameters:
a - an angle, in radians.
Returns:
the sine of the argument.
  
  
### >REST API 문서화
■ 프론트엔드에서 호출 하기 위한 REST API의 정보가 명세 된 문서 
-  백엔드 개발자 주도로 프론트엔드 개발자가 함께 설계
- 프론트엔드 개발자는 약속 된 REST API 문서에 의존하여 프론트엔드를 개발
 ■ 프론트엔드 등 Client에서 호출하고 활용하는 데 어려움이 없도록 상세하게
작성 되어야 함

  
### REST API 문서가 담고 있어야 하는 정보
■ REST API 설 명 ■ URI
■ HTTP Method
■ Request 파라미터（필수 파라미터와 선택 파라미터）
■ Response 데이터（필수 응답 데이터와 선택 응답 데이터） 
■ 가능한 에러 코드 및 대응 방법
■ 호출 예시
  
예)
>>  앱의 사용자 회원번호 목록을 제공하는 API입니다. 이 API는 관리자를 위한 것으로，앱 어드민 키를 사용하기 때문에 반드시 서버에서만 호출해야 합니다.
앱 어드민 키를 헤더에 담아 GET 으로 요청하며，파라미터을 사용해 회원번호 조회 범위 및 정렬 순서를 지정할 수 있습니다. 응답은 JSON 객체로 전달되며 검색 조건에 맞는 사용자 회원번호 목록을 포함합니다. 사용자 수가 많아 한 번에 전달할 수 없을 경우，이전 또는 다음 페이지 URL을 포함합니다. 해당 URL을 통해 사용자 목록의 이전 또는 다음 페이지를 추가 확인할 수 있습니다.

  ```java
Q Request
URL
GET /v1/user/ids HTTP/1.1 Host: kapi.kakao.com
Authorization: KakaoAK {APP_ADMIN_KEY}
Content-type: application/x-www-form-urlencoded;charset=utf-8
```
  
  
### >>>다음 단계에 따라 Instagram 사용자에 대한 미디어 컬렉션을 가져옵니다.
1단계: 액세스 토큰 및 권한 가져오기
액세스 토큰 및 권한 가져오기 가이드에 따라 사용자의 Instagram 사용자 액세스 토큰을 가져오세요.
丄nstagram_graph_user_profile 및! instagram_graph_user_media permissions가 필요하므로 사용자로부터 인증 을 가져올 때 user_profile 및 user_media 범위를 요청합니다.
2단계: 사용자 미디어 에지 쿼리
다음 엔드포인트에 요청을 보냅니다.
GET /me/media?fields={fields}£acce3s_token={acce33-token}
{fields}는 응답에 포함된 각 미디어에 대해 반환받고자 하는 미디어 필드의 쉼표로 구분된 리스트로 교제하고（또는 ID만 원할 경우 fields 매개변수를 완전히 생략）, {access-token}은 사용자의 액세스 토큰으로 교체합니다. GET /me 엔드포인트는 토 큰에서 얻은 사용자 ID를 확인하고 요청을 사용자 노드로 리 디렉션할 것입 니다.
샘플요청

```java
curl -X GET \ 'https://graph.instagram.com/me/media?fields=id,caption&access_token=IGQVJ..
```
  
### REST API 문서의 활용
■ 프론트엔드 개발자와 백엔드 개발자 모두 REST API 문서를 읽고 이해할 수 있어야 함
■ 백엔드 개발자는 프론트엔드 등의 Client를 위해 REST API 문서를 작성 할 수 있어야 함
■ REST API 문서가 잘 작성 될 수록 Communication 비용이 줄어 듦
  
  출처- 코드프레소 spring 
  '강의에서 더 자세한 설명과 좋은자료들이 많아서 강추합니다!!'
