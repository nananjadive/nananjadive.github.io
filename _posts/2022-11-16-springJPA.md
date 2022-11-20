---
date: 2017-05-11 12:00:00
layout: post
title: Grab your band and get out
subtitle: Lorem ipsum dolor sit amet, consectetur adipisicing elit.
description: Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559824822/theme15_oqsl4z.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559824822/theme15_oqsl4z.jpg
category: music
tags:
  - music
  - band
  - passion
author: mranderson
---

## 2.3 Spring Data JPA의 소개
>'Spring Data JPA'라는 것에 대해서 알아보고, 이를 활용하는 방법에 대한 학습 입니다. JPA(java Persistence API)는 Java 언어를 통해서 데이터베이스와 같은 영속 계 층을 처리하고자 하는 스펙입니다. JPA를 이해하기 위해서는 우선은 ORM(Object- Relational Mapping)이라는 기술에 대해서 먼저 설명해야만 합니다.



### ORM 과 JPA

ORM(Object Relational Mapping)은 단어에서 보듯이 객체지향과 관련이 있습니다
ORM은 간단히 말하자면 '객체지향 패러다임을 관계형 데이터베이스에 보존아는 기술'이라고 할 수 있습니다. 
패러다임 입장에서 생각하자면 '객체지향 패러다임을 관계형 패러다임으로 매핑(mapping)해 주는 개념'

객체지향의 구조가 관계형 데이터베이스'와 유사하다는점에서 시작합니다. 객체지향 언어 중에서 ’클래스(Class)’를 사용하는 언어는 특히 그러 한 경 우인데 예를 들어 '클래스' 장치를 사용하는 객체지향 프로그래밍 언어들은 어떠한 데이터의 구조를 잡기 위해서 우선적으로 클래스를 설계한다.

### 데이터베이스와 클래스 비교
- ’테이블(Table)를 설계한다. 새로운 테이블에는 칼럼을 정의하고 칼럼에 맞는 데이터 타입올 지정해서 데이터를 보관하는 를 만든다는 의미에서 클래스와 상당히 유사합니다.


```java
public class Member{
	private String id;
    private String pw;
    private String name;
    }
```
![](https://velog.velcdn.com/images/nananjadive/post/664dc5f6-62fa-434a-b128-166c20219575/image.png)


### ERD와 클래스 다이어그램 
객체지향에서는 클래스에서 인스턴스를 생성해서 인스턴스라는 '공간에 데이터를 보관하는데, 테이블에서는 하나의 ’Row’에 데이터를 저장하게 됩니다. 
여기서의 유일한 차이는 '객체'라는 단어가 '데이터 + 행위(메서드)라는 의미라면 'Row'는 '데이터만을 의미한다는 점이 다를 뿐입니다(데이터베이스에서는 **개체(entity**)'라는 용어를 사용합니다.


## 관계(relation)'와 '참조(reference)'
### -관계형 데이터베이스
테이블 사이의 관계를 통해서 구조적인 데이터를 '표현한다면，객체지향에서는 참조'를 통 해서 어떤 객체가 다른 객체들과 어떤 관계를 맺고 있는지를 표현한다.

ORM의 시작-'객체지향을자동으로 관계형 데이터베이스에 맞게’ 처리해 주는 기법
-객체지향과 관계형’사이의 변환 기법

JPA- ORM을Java 언어에 맞게 사용하는 '스펙'입니다. 따라서 ORM이 좀 더 상위 개념이 되고，JPA는 Java라는 언어에 국한된 개념

가장 유명 한 것은 Hibernate framework
![](https://velog.velcdn.com/images/nananjadive/post/c1534f35-658e-42a0-a9b3-e61d741b814a/image.png)

•  JPA를 통해서 관리하게 되는 객체（이하 엔티티객체（Entity Object））를 위한 엔티티 클래스
•  엔티티객체들을 처리하는 기능을 가진 Repository

Repository-Spring Data JPA에서 제공하는 인터페이스로 설계하는데 스프 링 내부에서 자동으로 객체를 생성하고 실행하는 구조

Spring Data JPA- 자동으로 생성되는 코드를 이용하므로 단순 CRUD나 페이지 처리 등의 개발에 코드를 개발하지 않아도 된다.


## 2.4.1 엔티티 클래스 작성
예제 프로젝트에 entity 패키지를 추가,
![](https://velog.velcdn.com/images/nananjadive/post/6b0fa6b3-bebf-49c1-a9df-7a381f3b069f/image.png)

### @Entity
해당 클래스가 엔티티를 위한 클래스이 며，해당 클래스의 인스턴스들 
이 JPA로 관리되는 엔티티 객체라는 것을 의미합니다.

### @Table
@Entity 어노테이션과 같이 사용할 수 있는 어노테이션
@Table(name="t_memo")와 같이 지정하는 경우에는 생성되는 테 이블의 이름이 t.memo' 테이블로 생성

### @ld 와 @GeneratedValue
@Entity가 붙은 클래스는 Primary Key(이하 PK)에 해당하는 특정 필드를 @Id로 지정해야만 합니다. 
@ld가 사용자가 입력하는 값을 사용하는 경우가 아니면 자동으로 생성되는 번호를 사용하기 위해서 

### @GeneratedValue라는 어노테이션을 활용
@GeneratedValue(strategy = GenerationType.lDENTITY) 부분은 PK를 자동으로 생 성하고자 할 때 사용합니다 키 생성 전략이라고 한다.

키생성 전략
- MySQL이나 MariaDB의 경우 auto increment 방식을 이용

### @Column
추가적인 필드（칼럼）가 필요한 경우에도 마찬가지로 어노테이션을 활용한다.

```java
package org.zerock.ex2.entity;
import lombok.*;

import javax.persistence.*; 
@Entity 
@Table(name= "tbl_memo") 
@ToString
@Getter
@Builder
@AllArgsConstructor @NoArgsConstructor public class Memo {
@Id


@GeneratedValue(strategy = GenerationType.IDENTITY) 
private Long mno;
@Column(length = 200, nullable = false) 
private String memoText;
```
>Lombok의  @Getter를  이용해서  Getter 메서드를  생성하고 @Builder를 이용해서 객체를 생성할수 있게 처리합니다. @Builder를 이용하기 위해서는 @AllArgsConstructor와  @NoArgsConstructor 사용해야합니다


>spring.jpa.hibernate.format_sql: 실제 JRA의 구현체인 Hibernate가 동작하면서 발생하는 SQL을 포맷팅
spring.jpa.show-sql： JRA 처리 시에 발생하는 SQL을 보여줄 것인지를 결정
spring.jpa.hibernate.ddl-auto: 프로젝트 실행 시에 자동으로 DDL(create, alter, drop 등)을 생성 할 것인지를 결정하는 설정입니다. 설정값은 create, update, create-drop, validate가 있습니다


![](https://velog.velcdn.com/images/nananjadive/post/29ceac9d-c626-484c-9df3-6a2a3094f8b7/image.png)

-MySQL의  Workbench는  MariaDB를  연동해서 사용할 수 있다.


## 2.4.3  JpaRepository 인터페이스
Spring Data JPA는  JPA의  구현체인  Hibernatef 이용하기  위한  여 러 API를 제공합니다. 그중에서 개발자가 가장 많이 사용할 것이 바로 JpaRepository라는 인터페이스입니다.

JPA관련 작업을 별도의 코드 없이 처리할 수 있게 지원합니다. 예를 들어 CRUD 작업이나 페이징，정렬 등의 처 리도 인터페이스의 메서드를 호출하는 형태로 처리하는데 기능에 따라서 상속 구조로 추 가적인 기능을 제공

![](https://velog.velcdn.com/images/nananjadive/post/1560ec94-edd5-4caa-bff6-2aa4d4beb20e/image.png)
JpaRepository는 인터페이스이고，Spring Data JPA는 이를 상속하는 인터페이스를 선언
하면 모든처리가 끝난다.

스프링이 내부적으로 해당 인터페이스에 맞는 코드를 생성하는 방식을 이용합니다. 프로젝 트 내에 repository 패키지를 생성하고，MemoRepository 인터페이스를 추가합니다，


```java
package org.zerock.ex2.repository;
import org.springframework.data.jpa.repository.DpaRepository; import org.zerock.ex2•entity.Memo;
public interface MemoRepository extends JpaRepository<Memo, Long> { }
```
Spring Data jPA는 인터페이스 선언만으로도 자동으로 스프링의 빈（bean）으로 등록된다

```java

package org.zerock.ex2.repository;
import org.springframework.data.jpa.repository.DpaRepository; import org.zerock.ex2•entity•Memo;
public interface MemoRepository extends JpaRepository<Memo, Long> { }
```
-Spring Data jPA는 인터페이스 선언만으로도 자동으로 스프링의 빈（bean）으로 등록
-（스프링이 내부적으로 인터페이스 타입에 맞는 객체를 생성해서 빈으로 등록합니다.）

## MemoReposiory
```java
package org.zerock.ex2.repository;
import org.springframework.data.jpa.repository.DpaRepository; import org.zerock.ex2.entity.Memo;
public interface MemoRepository extends JpaRepository<Memo, Long> { }
```
>JpaRepository를 사용할 때는 엔티티의 타입 정보（Memo 클래스 타입）와 @Id의 타입을 지정하게 됩니다. 이처럼 Spring Data jPA는 인터페이스 선언만으로도 자동으로 스프링（bean）으로 등록됩니다

### 테스트코드를통한 CRUD 연습

•  insert 작업: save（엔티티 객체）
•  select 작업 : findByld（키 타입）, getOne（키 타입）
•  update 작업: save（엔티티 객체）
•  delete 작업: deleteByld（키 타입）, delete（엔티티 객체）


### MemoRepositoryTests 
```java
package org.zerock.ex2.repository;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
@SpringBootTest
public class MemoRepositoryTests {
@Autowired
MemoRepository memoRepository; @Test
public void testClass(){System.out.printin(memoRepository.getClass().getName());}}
```

스프링이 내 부적으로 해당 클래스를 자동으로 생성(AOP기능) 
coin.sun.proxy.$ProxyXX와 같이 작성한 적이 없는 클래 스의 이름이 출력되는 것을 확인할 수 있습니다(동적 프록시라는 방식으로 만들어집 니다).

```java
package org.zerock.ex2.repository;
import org.junit.jupiter•api.Test;
import org.springframework.beans•factory.annotation•Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.zerock.ex2.entity.Memo;
import java.util.stream.IntStream;
@SpringBootTest
public class MemoRepositoryTests {
@Autowired
MemoRepository memoRepository;
@Test
public void testInsertDummies(){ 
IntStream.rangeClosed(lj100).forEach(i -> {
Memo memo = Memo.builder().memoText("Sample..."+i).build(); memoRepository.save(memo);
})；
}
```

-TestInsertDummies()의 내용은 K)0개의 새로운 Memo 객체를 생성하고 MemoRepository 를 이용해서 이를 insert 
-Memo의 memoText는 Not Null 조건이므로 반드시 데이터를 넣어주고 테스트를 
진행테스트가 실행되는 과정에는 JPA의 구현

![](https://velog.velcdn.com/images/nananjadive/post/f23f8be7-9837-4f95-9f6e-019d7ed7c007/image.png)
-Hibernate가 발생하는 insert 구문을 확인

조회작업테스트
findById()나getOne()을 이용해서 엔티티 객체를조회
![](https://velog.velcdn.com/images/nananjadive/post/07c02a9c-7d36-4da3-9739-3b9041128bcd/image.png)

실행되는 결과를 보면 findById()를 실행한 순간에 이미 SQL은 처리가 되었고，'====’ 부분은 SQL 처리 이후에 실행된 것을 볼 수 있습니다. getOne()의 경우는 조금 다른 방 식으로  동작하는데  @Transactional 어노테이션이  추가로  필요

![](https://velog.velcdn.com/images/nananjadive/post/3362f133-7a72-41c5-85e4-1eab3f28839a/image.png)
getOne()을 호출한 후에 '===' 부분이 먼저 실행되고 System.out.println()이  실행되면서  실제  객체를  사용하는  순간에  SQL이  동작

### 수정작업 테스트
@Id값이 일치하는지를 확인해서 insert 혹은 update 작업을 처리함


### @Test
public void testUpdate() {
Memo memo = Memo.builder().mno(100L)ㅣ.memoText("Update Text").build(); System.out.printin(memoRepos丄tory.save(memo));
}
 100번의 Memo 객체를 만들고，save()를 호출, elect 쿼리로 해당 번호의 Memo 객체를 확인하고，이를 update 
 ![](https://velog.velcdn.com/images/nananjadive/post/5c27fa36-0710-4c3c-8410-8ff4e5b7a7ff/image.png)
-@Id를 가진 엔티티 객체가 있다면 update, 그렇지 않다면 insert를 실행

### 삭제 작업 테스트

@Test
public void testDelete() {
Long mno = 100L; memoRepository.deleteByld(mno);
}

>Hibernate: select
memo0_.mno as mnol_0_0__,
memo0一.memo_text as memo一tex2_0_0_ from
memo memo0_ where
memo0_.mno=? Hibernate:
delete from
memo where
mno=?
slect 이후에 delete구문이 실행되는방식

