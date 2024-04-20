1. 알고리즘 문제 

python re 를 사용하여 앞의 수의 패턴을 파악, 이후 dynamic progmramming 으로 나열

2. API 만들기

request:

response:


## Endpoints

The base for the api is `/api/v1/`
Once we have other versions, the v1 wil be replaced by v2 and so on.
We will remove the versions from the api at some point, which should be communicated to any partners onboarding.

The endoints are namespaced by the user type. partners have their own space under `/api/v1/partners/`.
This is the only area the partner api keys should be able to access.

So far there is only one endpoint for partners, which is `/api/v1/partners/listings/`.

We support GET, POST, PUT and PATCH.

DELETE is disallowed but will be amended once we have the soft delete feature. It currently gives a 405.




## migrations 폴더에 자료를 insert 하는 파일 작성

당신의 프로젝트 README에 다음 내용을 추가하여 CRUD 및 검색 API에 대한 사용 방법을 설명할 수 있습니다.

---

# 음식 API 사용 방법

이 프로젝트는 음식 데이터에 대한 CRUD(Create, Read, Update, Delete) API 및 검색 기능을 제공합니다. 아래에서는 각 API의 사용 방법과 요청/응답 인자에 대해 설명합니다.

## CRUD API 사용 방법

### 음식 객체 생성 (Create)

- **엔드포인트:** `/api/foods/`
- **메서드:** POST
- **요청 인자 (Request Payload):**
  - `food_id`: 음식 ID (필수)
  - `food_cd`: 음식 코드
  - `group_name`: 음식 그룹 이름
  - `food_name`: 음식 이름 (필수)
  - `research_year`: 연구 연도
  - `market_name`: 시장 이름
  - `ref_name`: 참고 이름
  - 기타 필드들...
- **응답:** 생성된 Food 객체의 정보

### 음식 객체 조회 (Read)

- **엔드포인트:** `/api/foods/{food_id}/`
- **메서드:** GET
- **응답:** 해당 food_id에 해당하는 Food 객체의 정보

### 음식 객체 업데이트 (Update)

- **엔드포인트:** `/api/foods/{food_id}/`
- **메서드:** PUT
- **요청 인자 (Request Payload):**
  - 업데이트할 필드들 (예: food_name, research_year, 등)
- **응답:** 업데이트된 Food 객체의 정보

### 음식 객체 삭제 (Delete)

- **엔드포인트:** `/api/foods/{food_id}/`
- **메서드:** DELETE
- **응답:** 삭제된 Food 객체의 ID 및 성공 여부 메시지

## Search API 사용 방법

### 음식 검색 (Search)

- **엔드포인트:** `/api/food-search/`
- **메서드:** GET
- **쿼리 매개변수 (Query Parameters):**
  - `food_name`: 음식 이름으로 검색
  - `research_year`: 연구 연도로 검색
  - `maker_name`: 제조사 이름으로 검색
  - `food_code`: 음식 코드로 검색
- **응답:** 검색 결과에 해당하는 Food 객체들의 정보

## 요청 및 응답 인자

### 요청 인자 (Request Parameters)

- CRUD API:
  - 요청 Payload에 필드들을 전달하여 새로운 Food 객체를 생성하거나 업데이트합니다.
- Search API:
  - 쿼리 매개변수를 사용하여 검색 조건을 지정합니다. 필요에 따라 `food_name`, `research_year`, `maker_name`, `food_code` 등의 매개변수를 전달합니다.

### 응답 인자 (Response Parameters)

- 모든 API:
  - JSON 형식으로 응답이 반환됩니다.
  - 응답에는 Food 객체의 필드들이 포함됩니다. (예: food_id, food_cd, food_name, research_year 등)
  - CRUD API의 경우, 요청한 동작의 성공 여부에 대한 메시지도 포함됩니다.
  - Search API의 경우, 검색 결과로 반환된 Food 객체들의 정보가 포함됩니다.

---

이제 이 README를 프로젝트의 루트 디렉터리에 `README.md` 파일로 추가하고, 프로젝트의 사용자들이 API를 쉽게 이해하고 사용할 수 있도록 합니다.

참고자료

https://www.django-rest-framework.org/