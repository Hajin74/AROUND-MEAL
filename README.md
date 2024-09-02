## 프로젝트 개요

### 기술 스택
![java](https://img.shields.io/badge/Java-17-blue?logo=java)
![spring-boot](https://img.shields.io/badge/SpringBoot-3.3.3-grren?logo=springboot)
![postgresql](https://img.shields.io/badge/PostgreSQL-16.4-blue?logo=postgresql)
![redis](https://img.shields.io/badge/Redis-7.4-red?logo=redis)

### 요구사항
[위치 기반 맛집 추천 서비스](https://bow-hair-db3.notion.site/f2c5e47f67254726ba0ef8d894f7e8b9#f62425d8700b485da11338e3b0eb06c4)

### 팀 구성

| 이름  | 담당                                    |
|-----|-----------------------------------------|
| 유하진 | 데이터 파이프라인 구축(수집, 전처리, 저장, 자동화) |
| 김성은 | 통계 API (맛집 목록 조회), 점심 추천 Webhook   |
| 김연희 | 사용자 회원가입 API, 사용자 로그인 API, 사용자 정보 API, 인기있는 맛집만 캐싱|
| 안소나 | 시군구 목록 조회 API, 맛집 평가 생성 API         |
| 유서정 | 사용자 설정(좌표, 서비스 수신 여부) 업데이트 API, 맛집 상세정보 API, 조회수 N 이상만 캐싱|

</br>

## 프로젝트 관리

<details>
<summary><strong>일정</strong></summary>
  
| 날짜 | 활동 |
| --- | --- |
| 24.08.27 (화) | 역할 분담, 기술 선택  |
| ~ 24.08.30 (금) | 요구사항 기능 개발, 추가 요구사항 분담 |
| ~ 24.09.01 (일)| 추가 요구사항 개발 |
| 24.09.01 (월) | README.md 작성 및 추가 요구사항 점검|
</details>

<details>
<summary><strong>협업 라이프사이클</strong></summary>

1. 브랜치 생성
2. 코드 작성
3. PR 생성
4. 리뷰 요청
5. dev 브랜치로 Merge
</details>

<details>
<summary><strong>이슈 관리</strong></summary>
![issue](https://github.com/user-attachments/assets/f74c4fb2-15ac-4a68-b040-5241ce8d1e29)

</details>

<details>
<summary><strong>컨벤션</strong></summary>

- **Branch**
    - **전략**

      | Branch Type | Description |
      | --- | --- |
      | `dev` | 주요 개발 branch, `main`으로 merge 전 거치는 branch |
      | `feature` | 각자 개발할 branch, 기능 단위로 생성하기, 할 일 issue 등록 후 branch 생성 및 작업 |

    - **네이밍**
        - `{header}/#{issue number}`
        - 예) `feat/#1`

- **커밋 메시지 규칙**
    ```bash
    > [HEADER] : 기능 요약
    
    - [CHORE]: 내부 파일 수정
    - [FEAT] : 새로운 기능 구현
    - [ADD] : FEAT 이외의 부수적인 코드 추가, 라이브러리 추가, 새로운 파일 생성 시
    - [FIX] : 코드 수정, 버그, 오류 해결
    - [DEL] : 쓸모없는 코드 삭제
    - [DOCS] : README나 WIKI 등의 문서 개정
    - [MOVE] : 프로젝트 내 파일이나 코드의 이동
    - [RENAME] : 파일 이름의 변경
    - [MERGE]: 다른 브렌치를 merge하는 경우
    - [STYLE] : 코드가 아닌 스타일 변경을 하는 경우
    - [INIT] : Initial commit을 하는 경우
    - [REFACTOR] : 로직은 변경 없는 클린 코드를 위한 코드 수정
    
    ex) [FEAT] 게시글 목록 조회 API 구현
    ex) [FIX] 내가 작성하지 않은 리뷰 볼 수 있는 버그 해결
    ```

- **Issue**
    ```bash
    🍚 Description
    <!-- 진행할 작업을 설명해주세요 -->
    
    🍚 To-do
    <!-- 작업을 수행하기 위해 해야할 태스크를 작성해주세요 -->
    [ ] todo1
    
    🍚 ETC
    <!-- 특이사항 및 예정 개발 일정을 작성해주세요 -->
    ```

- **PR**
  - **규칙**
    - branch 작업 완료 후 PR 보내기
    - 항상 local에서 충돌 해결 후 remote에 올리기
    - PR 후 디스코드에 공유하기
    - 당일 PR은 당일에 리뷰하기
    - 최소 2명 이상의 동의를 받으면 merge하기
    - review 반영 후, 본인이 merge
    ```bash
        > [MERGE] {브랜치이름}/{#이슈번호}
        ex) [MERGE] setting/#1
    ```
  - **Template**
    ```bash
    🍚 Description
    <!-- 진행할 작업을 설명해주세요 -->
    
    🍚 To-do
    <!-- 작업을 수행하기 위해 해야할 태스크를 작성해주세요 -->
    [ ] todo1
    
    🍚 ETC
    <!-- 특이사항 및 예정 개발 일정을 작성해주세요 -->
    ```
</details>

</br>

## 기술 문서

### 아키텍처
<img width="707" alt="architecture" src="https://github.com/user-attachments/assets/bea07fac-77ae-4fee-8e85-9f0e20905882">


### API 명세서

▶️ [API 명세서 자세히보기](https://www.notion.so/API-197df8e5668f42baa79c96ffac873a47?pvs=21)

| API 명칭 | HTTP 메서드 | 엔드포인트 | 설명 |
| --- | --- | --- | --- |
| **사용자 회원가입** | POST | `/api/register` | 새로운 사용자를 등록합니다. |
| **사용자 로그인** | POST | `/api/login` | 사용자를 로그인시킵니다. |
| **사용자 로그아웃** | POST | `/api/logout`  | 사용자를 로그아웃시킵니다. |
| **맛집 목록 조회** | GET | `/api/posts` | 맛집 목록을 조회합니다. |
| **맛집 평가 생성** | GET | `/api/posts/{id}` | 특정 게시물의 상세 정보를 조회합니다. |
| **시군구 목록 조회** | PUT | `/api/posts/{id}/like` | 게시물에 좋아요를 추가합니다. |
| **사용자 설정 업데이트** | PUT | `/api/posts/{id}/share` | 게시물을 공유합니다. |
| **맛집 상세정보 조회** | GET | `/api/stats` | 게시물 통계 정보를 조회합니다. |

</br>

<details>
<summary><strong>ERD</strong></summary>

</details>

<details>
<summary><strong>디렉토리 구조 - 도메인이 많지 않아 기능별로 패키지를 나누었습니다.</strong></summary>


```bash
├── src
    ├── main
    │   ├── java
    │   │   └── com
    │   │       └── lucky
    │   │           └── around
    │   │               └── meal
    │   │                   ├── Application.java
    │   │                   ├── cache
    │   │                   │   ├── entity
    │   │                   │   │   └── RestaurantForRedis.java
    │   │                   │   ├── repository
    │   │                   │   │   └── RestaurantForRedisRepository.java
    │   │                   │   └── service
    │   │                   │       ├── RatingCountService.java
    │   │                   │       └── ViewCountService.java
    │   │                   ├── common
    │   │                   │   ├── WebClientConfig.java
    │   │                   │   ├── config
    │   │                   │   │   ├── CacheConfig.java
    │   │                   │   │   ├── GeometryConfig.java
    │   │                   │   │   ├── RedisConfig.java
    │   │                   │   │   └── SpringSecurityConfig.java
    │   │                   │   ├── redis
    │   │                   │   │   └── RedisRepository.java
    │   │                   │   ├── security
    │   │                   │   │   ├── details
    │   │                   │   │   │   ├── PrincipalDetails.java
    │   │                   │   │   │   └── PrincipalDetailsService.java
    │   │                   │   │   ├── filter
    │   │                   │   │   │   ├── JwtAuthenticationFilter.java
    │   │                   │   │   │   └── JwtAuthorizationFilter.java
    │   │                   │   │   ├── handler
    │   │                   │   │   │   ├── CustomAccessDeniedHandler.java
    │   │                   │   │   │   ├── CustomAuthenticationEntryPoint.java
    │   │                   │   │   │   ├── CustomLogoutHandler.java
    │   │                   │   │   │   └── CustomLogoutSuccessHandler.java
    │   │                   │   │   ├── record
    │   │                   │   │   │   └── JwtRecord.java
    │   │                   │   │   ├── redis
    │   │                   │   │   │   ├── RefreshToken.java
    │   │                   │   │   │   └── RefreshTokenRepository.java
    │   │                   │   │   └── util
    │   │                   │   │       ├── CookieProvider.java
    │   │                   │   │       └── JwtProvider.java
    │   │                   │   └── util
    │   │                   │       └── GeometryUtil.java
    │   │                   ├── controller
    │   │                   │   ├── LocationController.java
    │   │                   │   ├── MemberController.java
    │   │                   │   ├── RatingController.java
    │   │                   │   ├── RegionController.java
    │   │                   │   ├── RestaurantController.java
    │   │                   │   ├── dto
    │   │                   │   │   ├── GetRestaurantsDto.java
    │   │                   │   │   └── MemberDto.java
    │   │                   │   ├── record
    │   │                   │   │   ├── LoginRecord.java
    │   │                   │   │   ├── RegionRecord.java
    │   │                   │   │   └── RegisterRecord.java
    │   │                   │   ├── request
    │   │                   │   │   ├── MemberLocationRequestDto.java
    │   │                   │   │   ├── RatingRequestDto.java
    │   │                   │   │   ├── RestaurantDetailsRequestDto.java
    │   │                   │   │   └── StaticLocationRequestDto.java
    │   │                   │   └── response
    │   │                   │       ├── LocationResponseDto.java
    │   │                   │       ├── RatingResponseDto.java
    │   │                   │       ├── RestaurantDetailResponseDto.java
    │   │                   │       └── StaticLocationResponseDto.java
    │   │                   ├── datapipeline
    │   │                   │   ├── DataPipeLineService.java
    │   │                   │   ├── DataProcessService.java
    │   │                   │   ├── HashUtil.java
    │   │                   │   ├── RawDataLoadService.java
    │   │                   │   ├── RawRestaurant.java
    │   │                   │   └── RawRestaurantRepository.java
    │   │                   ├── entity
    │   │                   │   ├── Member.java
    │   │                   │   ├── Rating.java
    │   │                   │   ├── Region.java
    │   │                   │   ├── Restaurant.java
    │   │                   │   └── enums
    │   │                   │       ├── Category.java
    │   │                   │       └── MemberRole.java
    │   │                   ├── exception
    │   │                   │   ├── CustomException.java
    │   │                   │   ├── CustomExceptionHandler.java
    │   │                   │   └── exceptionType
    │   │                   │       ├── CommonExceptionType.java
    │   │                   │       ├── CsvRegionExceptionType.java
    │   │                   │       ├── DataExceptionType.java
    │   │                   │       ├── ExceptionType.java
    │   │                   │       ├── MemberExceptionType.java
    │   │                   │       ├── RegionExceptionType.java
    │   │                   │       ├── RegisterExceptionType.java
    │   │                   │       ├── RestaurantExceptionType.java
    │   │                   │       └── SecurityExceptionType.java
    │   │                   ├── repository
    │   │                   │   ├── MemberRepository.java
    │   │                   │   ├── RatingRepository.java
    │   │                   │   ├── RegionRepository.java
    │   │                   │   └── RestaurantRepository.java
    │   │                   └── service
    │   │                       ├── CsvRegionService.java
    │   │                       ├── JwtService.java
    │   │                       ├── LocationService.java
    │   │                       ├── MemberService.java
    │   │                       ├── RatingService.java
    │   │                       ├── RegionService.java
    │   │                       └── RestaurantService.java
    │   └── resources
    │       ├── application.properties
    │       ├── application.yml
    │       └── region
    │           └── sgg_lat_lon.csv
    └── test
        └── java
            └── com
                └── lucky
                    └── around
                        └── meal
                            ├── ApplicationTests.java
                            ├── cache
                            │   ├── RatingCountServiceTest.java
                            │   └── RestaurantRepositoryTest.java
                            ├── common
                            │   └── security
                            │       └── util
                            │           ├── CookieProviderTest.java
                            │           └── JwtProviderTest.java
                            └── service
                                ├── LocationServiceTest.java
                                ├── MemberServiceTest.java
                                └── RestaurantServiceTest.java
```
</details>

</br>

## 기능 구현

<details>
<summary><strong>RESTful API</strong></summary>
  
- 사용자 회원가입 api
- 사용자 로그인 api
- 사용자 설정 업데이트 api
- 사용자 정보 api
- 시군구 목록 api
- 맛집 목록 api
- 맛집 상세정보 api
- 맛집 평가 생성 api
</details>

<details>
<summary><strong>데이터 파이프라인</strong></summary>
  
- 공공데이터 수집
- 데이터 가공
- 데이터 저장
- 데이터 파이프라인 자동화
</details>

<details>
<summary><strong>Webhook</strong></summary>
  
- Discord Webhook 을 활용한 점심 추천 서비스
</details>

<details>
<summary><strong>기타</strong></summary>
  
- 시군구 데이터 업로드
- 인기있는 맛집 캐싱
- 조회수 N회 이상 맛집 캐싱
- 맛집 상세정보 캐싱
</details>

</br>

## 트러블 슈팅
- 캐싱 전략
- 데이터 파이프라인 전략
- postgis
