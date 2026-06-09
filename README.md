# 🎬 Movie Expert Agent

OpenAI GPT-4o-mini의 Function Calling 기능과 실제 Movie API를 활용하여 구현한 Movie Expert Agent입니다.

사용자의 자연어 질문을 분석하여 적절한 함수를 선택하고 영화 정보를 조회할 수 있습니다.


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

User: 지금 인기 있는 영화가 무엇인지 알려줘
AI: 현재 인기 있는 영화 목록은 다음과 같습니다:

1. **Obsession**
   - 개요: 소중한 사람의 마음을 얻기 위해 신비한 "원 위시 윌로우"를 깨뜨린 후, 절망적인 로맨티스트는 자신의 소원이 이루어지지만 일부 욕망은 어두운 대가를 치르게 된다는 이야기입니다.
   - 평점: 7.9
   - 개봉일: 2026-05-13
   - ![포스터](https://image.tmdb.org/t/p/w780/2G249T4Sgu8gXIZpaXWnxHYYNQV.jpg)

2. **Peddi**
   - 개요: 1980년대 안드라 프라데시 농촌에서, 한 열정적인 촌민이 스포츠를 통해 지역 사회를 단결시켜 강력한 라이벌에 맞섰다는 이야기입니다.
   - 평점: 6.3
   - 개봉일: 2026-06-03
   - ![포스터](https://image.tmdb.org/t/p/w780/kJAJNNBYlbqAcpTDxBNnaILSMTy.jpg)

3. **Lee Cronin's The Mummy**
   - 개요: 한 기자의 어린 딸이 사막에서 흔적 없이 사라지고, 8년 후 가족이 재회하지만 그 재회는 악몽으로 변하게 된다는 이야기입니다.
   - 평점: 8.1
   - 개봉일: 2026-04-15
   - ![포스터](https://image.tmdb.org/t/p/w780/1q308iixueCU4pFtSYugNOevtNx.jpg)

4. **The Mandalorian and Grogu**
   - 개요: 악당 제국이 무너지면서, 새로운 공화국이 자신의 안위를 위해 전설적인 맨달로리안 현상금 사냥꾼과 그의 어린 제자 그로구의 도움을 요청하게 되는 이야기입니다.
   - 평점: 6.8
   - 개봉일: 2026-05-20
   - ![포스터](https://image.tmdb.org/t/p/w780/5Vi8dSauVwH1HOsiZceDMbRr1Ca.jpg)

5. **Kara**
   - 개요: 한 도둑이 정직한 삶을 살고자 하지만, 그의 아버지가 빚에 시달리자 다시 범죄의 세계로 돌아가야 하는 이야기가 전개됩니다.
   - 평점: 6.3
   - 개봉일: 2026-04-30
   - ![포스터](https://image.tmdb.org/t/p/w780/6U6i4qhgHR1MWkUb6OGQwNpqcZC.jpg)

더 궁금한 점이 있으시면 알려주세요!

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

User: movie ID 550에 해당하는 영화가 무엇인지 알려줘
AI: 영화 ID 550에 해당하는 영화는 **격투기 클럽 (Fight Club)**입니다.

- **개요**: 잠을 잘 수 없는 남자와 미끄러운 비누 판매원이 원초적인 남성의 공격성을 새로운 형태의 치료에 적극 활용하면서 벌어지는 이야기입니다. 그들의 개념은 인기를 얻어 지하 "격투기 클럽"이 생겨나는데, eccentric한 인물이 개입하여 통제 불가능한 혼란으로 빠지게 됩니다.
- **개봉일**: 1999-10-15
- **예산**: 63,000,000 USD
- **수익**: 100,853,753 USD
- **상영 시간**: 139분
- **장르**: 드라마, 스릴러
- **평점**: 8.4
- **태그라인**: 장난. 혼란. 비누.
- [자세히 보기](https://www.20thcenturystudios.com/movies/fight-club)
- ![포스터](https://image.tmdb.org/t/p/w780/jSziioSwPVrOy9Yow3XhWIBDjq1.jpg)

더 궁금한 점이 있으시면 알려주세요!

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

User: movie ID 550에 해당하는 영화에 누가 출연하는지 알려줘
Calling function: get_movie_credits with {"id":550}
AI: 영화 **격투기 클럽 (Fight Club)**의 출연진은 다음과 같습니다:

1. **Edward Norton** - Narrator
   ![Edward Norton](https://image.tmdb.org/t/p/w185/8nytsqL59SFJTVYVrN72k6qkGgJ.jpg)

2. **Brad Pitt** - Tyler Durden
   ![Brad Pitt](https://image.tmdb.org/t/p/w185/m09Y1YfPPeNYYUSHnnVqahkrC1o.jpg)

3. **Helena Bonham Carter** - Marla Singer
   ![Helena Bonham Carter](https://image.tmdb.org/t/p/w185/hJMbNSPJ2PCahsP3rNEU39C8GWU.jpg)

4. **Meat Loaf** - Robert Paulson
   ![Meat Loaf](https://image.tmdb.org/t/p/w185/1zkohpaG3my4qQAZGVgzgPuXwZ6.jpg)

5. **Jared Leto** - Angel Face
   ![Jared Leto](https://image.tmdb.org/t/p/w185/ca3x0OfIKbJppZh8S1Alx3GfUZO.jpg)

6. **Zach Grenier** - Richard Chesler (Regional Manager)
   ![Zach Grenier](https://image.tmdb.org/t/p/w185/fSyQKZO39sUsqY283GXiScOg3Hi.jpg)

7. **Holt McCallany** - The Mechanic
   ![Holt McCallany](https://image.tmdb.org/t/p/w185/iRo9YUNMwZg4UCq7dapo0HydDmI.jpg)

8. **Eion Bailey** - Ricky
   ![Eion Bailey](https://image.tmdb.org/t/p/w185/3DW13W47cKk4LQZwS4EvRaNBoVu.jpg)

9. **Richmond Arquette** - Intern at Hospital
   ![Richmond Arquette](https://image.tmdb.org/t/p/w185/7byGiVac0GjBSVD1h6ylZlVXZK6.jpg)

10. **David Andrews** - Thomas at Remaining Men Together
    ![David Andrews](https://image.tmdb.org/t/p/w185/A3vP0a0CqmQSdslPRnEYDiyIZ3V.jpg)

이 외에도 여러 배우들이 출연하였습니다. 추가적인 정보가 필요하시면 말씀해 주세요!


## 👨‍💻 Author

**안시우**

