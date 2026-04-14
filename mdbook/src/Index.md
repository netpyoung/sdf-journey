# Software Design for Flexibility

- [Software Design for Flexibility: How to Avoid Programming Dead Ends](https://www.amazon.com/Software-Design-Flexibility-Programming-Yourself/dp/0262045494)
  - `S`oftware `D`esign for `F`lexibility
  - 유연한 소프트웨어를 만드는 설계 원칙, 막다른 골목 없이 진화하는 시스템 개발하기

``` txt
Review

“Most systems need to succeed over time, not merely at a point in time. A fascinating exploration of predicative dynamic dispatch, metadata, and other techniques for building flexible systems that can be enhanced without breaking.”
—Rich Hickey, author of Clojure and architect of Datomic
 
“Hanson and Sussman’s Software Design for Flexibility has introduced additive programming, a game changer. An additive style allows for making changes to existing designs without the programmer’s efforts looking like the work of a contortionist. With elegance, clarity, and care, they point out long-overlooked problems in software design and offer their Scheme-friendly, clever solutions. Enjoy!”
—Dan Friedman, Professor of Computer Science, University of Indiana; author of The Little Prover
```

- SICP(Structure and Interpretation of Computer Programs)를 재미있게 봤다면, 관심이 안갈래야 안갈 수가 없는 책일것이다.
- 하지만 책의 제목부터 낚시의 향기
  - 책의 제목만 봐선 SICP 같은 경우 Interpretation 이라는 단어가 뭐하는거지 하지만, SDF 같은 경우 Flexibility 가 뭐지라는 생각
  - 유연성(Flexibility)과 확장성(Extensibility)과 차이
    - Flexibility 기존 것을 바꾸기 쉬운가?
    - Extensibility 기능을 추가하기 쉬운가?
- 책을 보다보니 Datomic의 datalog가 생각나네
- 지은이
  - 크리스 핸슨 - <https://sites.google.com/a/chris-hanson.org/cph/home>
    - 시스템 엔지니어
    - [The Role of Community in Free Software](https://sites.google.com/a/chris-hanson.org/cph/community)
  - 제널드 제이 서먼스 Gerald Jay Sussman
   - SICP
   - MIT/GNU Scheme 만든 사람
- 도운이
  - Richard Stallman
  - Guy L. Steele Jr.
    - Scheme 언어 만든사람
  - Alexery Radul
    - <https://scholar.google.com/citations?user=d2gqmrUAAAAJ&hl=en>
  - <https://alexey.radul.name/>

## 준비

SICP를 봤다면 알겠지만, 이 책을 아무 준비도 안한상태서 보면 안된다. 이 책은 MIT 6.945 코스에서 쓰인다.

``` txt
너 전에도 이거(6.945) 들었냐?
SICP(6.001)는 알어?
AI(6.034)에 대해서는?
1000줄 이상 코딩해봤어?
어셈블리는 알어?
OOP 언어는?
Lisp 계열 언는?
함수형 언어는?
로직 언어는 다뤄봤어?

Are you registered for 6.5150 (6.945) or 6.5151 (6.905)? yes no
Have you written a program longer than 1000 lines? yes no
Have you used assembly language? yes no
Have you used an object-oriented language (e.g. Java)? yes no
Have you used a Lisp-based language (e.g. Scheme)? yes no
Have you used a functional language (e.g. Haskell)? yes no
Have you used a logic-programming language (e.g. Prolog)? yes no
Have you had 6.009 (or old 6.001) or equivalent? yes no
Have you had 6.034 or equivalent? yes no
```

- [6.5150 (6.945) or 6.5151 (6.905) - Adventures in Advanced Symbolic Programming](https://groups.csail.mit.edu/mac/users/gjs/6.945/index.html)
- [6.001 - Structure and Interpretation of Computer Programs](https://ocw.mit.edu/courses/6-001-structure-and-interpretation-of-computer-programs-spring-2005/)
- [6.005 - Software Construction](https://ocw.mit.edu/courses/6-005-software-construction-spring-2016/)
- [6.034 - Artificial Intelligence](https://ocw.mit.edu/courses/6-034-artificial-intelligence-fall-2010/)
- [6.101(6.009) - Fundamentals of Programming](https://py.mit.edu/spring26)

## 문제?

- 리뷰1 [Software Design for Flexibility: a review - Geoff Wozniak](https://wozniak.ca/blog/2022/03/01/1/index.html)
- mit-scheme 중심으로 작성됨
  - mit-scheme이 버전업되면서 윈도우 지원 안하니,
  - wsl + emacs + geiser + mit-scheme 설정으로 하는게 편한듯.
  - 아니면 Racket설정하든가
    - Language > Choose Language... > Other Languages > R5RS

``` scheme
(define ((hello x) y) ; mit-scheme에선 동작
  (/ x y))


(define (hello x)
  (lambda (y)
    (/ x y)))

((hello 1) 2) ;; => 1/2
```

- 책이 얇다. 각 장마다 책 한권 이상이 나올텐데, 다루는 내용이 많은데
  - 지도를 그려나간다 하면서 sicp랑 이런 책들을 읽으면 좋음
  - 참고 문헌
  - 저자가 누구인지
  - SICP는 그나마 친절하다

- 번역서 문제 용어
  - 번역자가 류광으로 SICP번역 보다는 훨씬 나음.
  - 하지만 류광 역시 역대 번역서 대대로 이어진 고질적인 아집이 있음
    - 맞는 말인데 쳐맞는말
    - 굳이 중요치 않은것에도 전문용어를 써야했었나
    - arity - 항수 / 인자 개수
      - <https://en.wiktionary.org/wiki/arity>
    - Pattern Matching - 패턴부합 / 패턴매칭 
- 연습문제 2.2 부분 누락
  - 이건 치명적인 검수문제. 리뷰도 돌렸을 이걸 못잡네.


## 참고자료

- <https://groups.csail.mit.edu/mac/users/gjs/6.945/>
  - <https://groups.csail.mit.edu/mac/users/gjs/6.945/sdf/manager/software-manager.pdf>
  - <https://groups.csail.mit.edu/mac/users/gjs/6.945/red-tape.pdf>

- Readings: Readings may be chosen from
  1. SDF: Hanson and Sussman; Software Design for Flexibility
  2. SICP: Abelson, Sussman, and Sussman; Structure and Interpretation of Computer Programs
  1. R5RS: Kelsey, et.al.; Revised 5 Report on the Algorithmic Language Scheme
  2. SOS: Hanson; Scheme Object System
  3. ART: Springer and Friedman; Scheme and the Art of Programming
  4. RZ: Zippel; Effective Polynomial Computation
  5. AOP: Radul and Sussman; The Art of the Propagator
  6. BPS: Forbus and deKleer; Building Problem Solvers
  7. CONS: Steele; Constraints, MIT PhD thesis
  8. LOGIC: Suppes; Introduction to Logic
  9. AMORD: deKleer, Doyle, Rich, Steele, and Sussman; AMORD: A Deductive Procedure System
  10. CMMR: Bundy; The Computer Modelling of Mathematical Reasoning

- ["We Really Don't Know How to Compute!" - Gerald Sussman (2011)](https://www.youtube.com/watch?v=HB5TrK7A4pI)
- [Gerald Jay Sussman on Flexible Systems, The Power of Generic Operations](https://www.youtube.com/watch?v=cblhgNUoX9M)
- [Three Directions in Design: Gerald Jay Sussman](https://www.youtube.com/watch?v=Tdwr9tweTDE)
- [Strange Loop Chat with Gerald Sussman, Julie Sussman, Chris Hanson](https://www.youtube.com/watch?v=YDQmbT62eZk)
  - 스트레인지 루프는 2009년 소프트웨어 개발자 알렉스 밀러에 의해 설립되었으며
    - Programming Clojure/Clojure Brain Teasers/Clojure Applied 공동저자
    - <https://github.com/puredanger>
    - <https://insideclojure.org/>

## 소스 

- <https://occamsrazr.net/tt/381>
- <https://occamsrazr.net/book/SoftwareDesignForFlexibility>
- <https://github.com/jeffhhk/SoftwareDesignForFlexibility>
- <http://groups.csail.mit.edu/mac/users/gjs/sdf.tgz>

``` scheme
(load ".../sdf/manager/load")
(manage 'new-environment 'term-rewriting)

mit-scheme -edit
```

## 요약

|                                             |                                                                                              |
| ------------------------------------------- | -------------------------------------------------------------------------------------------- |
| 2장 DSL                                     | 문제를 그 자체의 형태로 표현. / 표준화된 인터페이스와 조합                                   |
| 3장 Generic Procedure 소개                  | 동일한 연산자 하지만 다양한 데이터 타입을 처리                                               |
| 4장 패턴매칭                                | 선언적 / 제어 구조와 문제 영역을 분리                                                        |
| 5장 평가 - apply / eval / macro             | 언어 자체 확장 (eager vs lazy / deterministic vs nondeterministic / 아에 새로운 문법)        |
| 6장 계층화 - 및 메타데이터                  | 계층화로 역활분담 및 메타데이터를 사용하여 기존 데이터 유지하며 상황에 맞는 데이터 조작 가능 |
| 7장 전파 - dependency-directed-backtracking | 데이터 변경 전파/ 정보를 결합                                                                |

### 1장 오버뷰

1: Flexibility in Nature and in Design

- 문제
  - 설계자가 생각지도 못햇거나 의도하지 않았던 용도로 활용 가능한 시스템을 만드는것
  - 프로그램의 추가/수정이 어려워지고 있다
    - 비용을 최소화 하는 방법을 찾고 싶다.
  - 결정을 내리는 것 자체는 피할 수 없지만,
    - 이미 내린 결정을 변경하는 데 드는 비용을 최소화 하는 방법을 찾을 수 있을것이다.
- Additive programming
  - 요구사항의 변화에 수월하도록 시스템 구축
  - 새로운 코드 추가나 갈아 엎는 수준이아니라 약간의 기존 코드를 조정
- 일반적인 부품
  - 특정 프로젝트에 종속되지 않은
- 각장 설명
  - 특정 영역 - 2장 DSL
  - 유연성 - 3장 Generic Procedure - handler 처리 부분
  - 메타 추가로 기존 데이터 수정 방지 - 6장 계층화
  - 부족한 정보 속에서 복잡한 해답 산출 - 4장 패턴매칭
  - 부족한 정보 속에서 복잡한 해답 산출 - 7장 전파
- 유연성을 위한 시스템 구축시 고려
  - 메모리 사용량
  - 속도
  - 구축 시간
    - 유지보수 시간 포함
- degeneracy
  - 주어진 요구사항을 충족하는 방법이 하나가 아니라 여러개.(여러방향 접근 가능)
  - 물리: 서로 다른 상태인데도 같은 에너지 값을 갖는 경우
  - 축퇴(縮退)
    - 縮 (줄일 축) → 줄어든다
  	- 退 (물러날 퇴) → 뒤로 물러난다
	- 여러 개로 구분되던 상태가 "줄어들어 하나로 겹쳐진 상태"

### 2장 DSL

2: Domain-Specific Languages

SICP에서 2장

- 2.1 콤비네이터(Combinator / 조합자)
  - 함수의 조합
    - 제한 - 인수
  - 커링
- 2.2 정규표현식 - 메타프로그래밍
  - 문제 - 문법 - ex [a^] / [^] 
    - 조합으로 복잡한 표현식을 만들 수 있지만, 위치에 따라 의미가 크게 달라진다.
    - translator를 만드는게 어려움 - 정규표현식 문법 자체가 더 큰 조합을 만들 수 있는 능력이 떨어지기 때문에 
  - 조합 가능한 것들로 새 부품을 만드는 방식이라면 좀 더 단순하고 견고한 구현을 만들 수 있을것
    - 함수 조합으로 정규표현식을 만듬
- 2.3 래퍼(Wrapper)
  - 기존 프로그램을 수정/새로 재작성하는 대신 레이어를 두어 확장성 있게 만듬.
  - 유효성 검증에도 쓰일 수 있음
- 2.4 DSL로 문제 영역 추상화

## 3장 Generic Procedure 소개

3: Variations on an Arithmetic Theme

SICM 과 관련

- 동작은 하나인데, 적용 대상(type/structure)은 다양하다
- predicate dispatch는 비용 크다
  - 인자를 받아 dispatch
- 어떤 타입이냐가 아니라 어떻게 연결되어 있느냐가 중요
- 태그
  - dispatch비용을 줄이기 위해 데이터에 태그를 달아줌.
  - 여기선 데이터의 타입을 나타내기 위해서 사용
  - 접근제어나 추적 및 디버깅 정보에도 활용할 수 있을것임.

### 4장 패턴매칭( Pattern Matching - 패턴매칭 패턴부합)

4: Pattern Matching

PAIP - 11 Logic Programming

### 5장 평가

5: Evaluation

SICP 4장 복습

amb

### 6장 계층화

6: Layering

Layered Programming

바텀업 구조화

| 개념              | 역할      |
| ----------------- | --------- |
| Combinator        | 작은 조각 |
| Generic Procedure | 확장성    |
| Layer             | 구조화    |

### 7장 전파

7: Propagation

SICP 3.3.4 - 디지털 회로 시뮬레이터

- "프로그램을 '계산 절차'로 쓰지 말고, '제약(constraint)과 관계'로 표현하라. 그러면 값은 자동으로 전파(propagate)된다."
  - 엑셀같이

alert-propagators!

### 8장

8: Epilogue



---

## 연습문제

``` txt
2.1 ~ 12
3.1 ~ 20
4.1 ~ 25
5.1 ~ 24
  5.7 중위표기법을 전위표기법으로 전환
  5.15 peephole optimization / loop-invariant code motion
6.1 ~ 5
7.1 ~ 8
  7.1
  7.2
  7.3
  7.4
  7.5 요트 이름 구하기
  7.6 - amb - 5.4
  7.7 - 5.17
  7.8
```

2.1 compose / parallel-combine의 인자 갯수 맞추기

``` txt
2.2 연습문제 누락

<https://occamsrazr.net/book/SoftwareDesignForFlexibility>

spread-combine의 프로시저 f, g, h에 어떤 종류의 제약을 가해야 할까

(procedure-arity-min (procedure-arity +)) = 0
(procedure-arity-max (procedure-arity +)) = #f

(procedure-arity-min (procedure-arity atan)) = 1
(procedure-arity-max (procedure-arity atan)) = 2

Exercise 2.3: A quickie
Reformulate parallel-combine to be a composition of two parts
and to allow the parts to return multiple values
```