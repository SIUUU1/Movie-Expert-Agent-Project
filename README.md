# 🎬 Movie Expert Agent

OpenAI GPT-4o-mini의 Function Calling 기능과 실제 Movie API를 활용하여 구현한 Movie Expert Agent입니다.

사용자의 질문을 분석하여 적절한 함수를 선택하고 영화 정보를 조회할 수 있습니다.


## 📌 프로젝트 소개

이 프로젝트는 OpenAI Function Calling을 활용하여 사용자의 요청에 따라 적절한 영화 API를 호출하는 AI Agent를 구현하는 과제입니다.

Agent는 다음과 같은 작업을 수행할 수 있습니다.

* 현재 인기 영화 조회
* 특정 영화 상세 정보 조회
* 특정 영화의 출연진 및 제작진 조회


## 🚀 사용 기술

* Python 3.12+
* OpenAI API
* GPT-4o-mini
* Requests
* Jupyter Notebook
* uv


## 📂 프로젝트 구조

```text
movie-expert-agent/
├── movie_agent.ipynb
├── README.md
├── pyproject.toml
├── uv.lock
├── .env
└── images/
    ├── test_popular_movies.png
    ├── test_movie_details.png
    └── test_movie_credits.png
```


## 🔗 Movie API

Base URL

```text
https://nomad-movies-2.nomadcoders.workers.dev
```

### API Endpoints

| Endpoint              | Description  |
| --------------------- | ------------ |
| `/movies`             | 인기 영화 조회     |
| `/movies/:id`         | 영화 상세 정보 조회  |
| `/movies/:id/credits` | 출연진 및 제작진 조회 |


## 🛠 구현한 함수

### 1. get_popular_movies()

현재 인기 영화 목록을 조회합니다.

```python
get_popular_movies()
```


### 2. get_movie_details(id)

영화 ID를 이용하여 상세 정보를 조회합니다.

```python
get_movie_details(550)
```


### 3. get_movie_credits(id)

영화 ID를 이용하여 출연진 및 제작진 정보를 조회합니다.

```python
get_movie_credits(550)
```


## 🤖 Function Calling

Agent는 아래 3개의 함수를 사용할 수 있습니다.

```text
get_popular_movies()
get_movie_details(id)
get_movie_credits(id)
```

시스템 프롬프트를 통해 사용자의 질문을 분석하고 가장 적절한 함수를 선택하도록 구현했습니다.

### System Prompt

```text
당신은 Movie Expert Agent 입니다.

사용자가 영화 정보를 요청하면
반드시 적절한 함수를 선택하세요.

사용 가능한 함수:

1. get_popular_movies()
- 현재 인기 영화 목록 조회

2. get_movie_details(id)
- 특정 영화의 상세 정보 조회

3. get_movie_credits(id)
- 특정 영화의 출연진 및 제작진 조회

사용자의 요청을 분석한 뒤
가장 적절한 함수와 인자를 선택하세요.
```


## 📋 테스트 결과

### Test 1

#### Input

```text
지금 인기 있는 영화가 무엇인지 알려줘
```

#### Function Call

```json
{
  "name": "get_popular_movies",
  "arguments": {}
}
```

#### Result

![Test1](./images/test_popular_movies.png)


### Test 2

#### Input

```text
movie ID 550에 해당하는 영화가 무엇인지 알려줘
```

#### Function Call

```json
{
  "name": "get_movie_details",
  "arguments": {
    "id": 550
  }
}
```

#### Result

![Test2](./images/test_movie_details.png)


### Test 3

#### Input

```text
movie ID 550에 해당하는 영화에 누가 출연하는지 알려줘
```

#### Function Call

```json
{
  "name": "get_movie_credits",
  "arguments": {
    "id": 550
  }
}
```

#### Result

![Test3](./images/test_movie_credits.png)


## 👨‍💻 Author

**안시우**

