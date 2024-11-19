# 블로그 세부설정

<br/>

## 1. 댓글 기능 추가

- **utterances** 설치
	- https://github.com/apps/utterances
    - `configure`를 통해 본인 계정과 연동
    
<br/>
    
![image](https://github.com/user-attachments/assets/a0624335-0654-4c6e-a30e-744376cadc1d)
- `repo`에 본인 깃 블로그 repository명 작성

<br/>

![image](https://github.com/user-attachments/assets/069e7aae-1023-43e2-b94e-efeb1bf4f386)
- `Issue Label` (Option)
	- 댓글이 달릴 때 `Issue`에 달리게 됨
    - 이때 Label을 무엇으로 달 건지 선택하는 부분
    	- 기존에 없던 Label명을 적을 경우 새 Label이 생성

<br/>

![image](https://github.com/user-attachments/assets/f5aa0c36-f330-4872-94aa-9d0b9f5891ae)
- utterances 테마

<br/>

![image](https://github.com/user-attachments/assets/dc5d3d7d-df14-44ba-9bf5-73a70af97c7e)
![image](https://github.com/user-attachments/assets/0e08015d-6eb6-4601-9076-5e836e36c4ae)
- `Enable Utterances` 부분의 있는 코드를 참고하여 깃 허브의 `_config.yml` 중 `comments` 부분을 위와 같이 수정

<br/>

![image](https://github.com/user-attachments/assets/68589637-7058-496c-ae9b-e94a3e94bab6)
- `_layouts/post.html` 맨 아래에 `Enable Utterances` 복붙
- commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/5316abec-de48-4636-b617-ff809bdc3801)
- 댓글 기능은 활성화되었지만 댓글창이 2개인 것을 확인
- comments에서 중복 호출된 듯 보임

<br/>

![image](https://github.com/user-attachments/assets/5291bda8-41e1-42ee-82a3-03c1432c0508)
- `_config.yml`의 `comments` 부분에서 사용되고 있는 utterances를 제외한 disqus나 gitscus는 주석 처리
- commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/ac40342e-cc58-4ddb-ba35-c63831619478)
- 정상적으로 댓글 기능이 1개만 호출

<br/>

## 2. 조회수

- **GoatCounter** 설치
	- https://www.goatcounter.com/
    - Sing up으로 회원가입
    
<br/>

![image](https://github.com/user-attachments/assets/e4741d63-d60a-4a9b-a161-e4c998950e3c)
- code : 닉네임
- site domain : 깃허브 주소
- fill in 9 here : 9 입력

<br/>

- 로그인 후 우측 상단바의 `Settings` 진입
![image](https://github.com/user-attachments/assets/8f01df42-33a2-4c0a-bb25-51e33220e00a)
- `Allow adding visitor counts on your website` 체크
	- 맨 밑 `Save`

<br/>

![image](https://github.com/user-attachments/assets/e3376681-d63d-4f84-b368-15913cea6f80)
- 깃허브의 `config.yml`에서 위와 같이 수정
	- `id`에 GoatCounter 회원가입할 때 입력한 `Code` 입력
    - `provider`에 `goatcounter` 입력

<br/>

![image](https://github.com/user-attachments/assets/aeb05761-4a6b-4e22-bed9-9a5c3c199569)
- `_includes/pageviews/goatcounter.html` 맨 밑줄에 GoatCounter 로그인 당시 나온 코드를 복붙
- commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/b9eac74e-3264-400b-8c80-d3928f1200af)
- GoatCounter에서 조회수 확인 가능

<br/>

## 3. 검색노출
### 3-1. Google 검색 엔진 노출

- **Google Search Console** 등록
	- https://search.google.com/search-console/about
    - `시작하기`

<br/>

![image](https://github.com/user-attachments/assets/85612e26-fb40-4655-8bd5-cd37d83461e1)
- URL 접두어
	- 본인의 깃 블로그 주소를 입력

<br/>

![image](https://github.com/user-attachments/assets/c9077504-bc4f-4a7c-9fea-5968504b9507)
- **HTML 태그** 방식을 사용해 소유권 확인
- 1번에 존재하는 코드를 복사
- `확인` 버튼은 누르지 말 것

<br/>

![image](https://github.com/user-attachments/assets/4228e563-788e-426c-9704-c968f63433e6)
- 깃허브 `_config.yml`에서 `webmaster_verifications` 부분의 `google`에 복사한 내용 중 **content**에 해당하는 내용을 입력
	- 입력 당시 꼭 **`" "`**로 묶어줘야 함
    - `" "`을 사용하지 않을 경우 인식하지 못하여 소유권 확인 불가
- commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/e53d5762-f0b0-4bdd-8722-d042896a42be)
- Google Search Console로 돌아와 `확인` 버튼 클릭
- 소유권 확인 완료
- `속성으로 이동` 클릭

<br/>

![image](https://github.com/user-attachments/assets/ea953e4a-2e60-49d1-abda-d2875910edbf)
- 좌측 `Sitemaps` 진입
- `새 사이트맵 추가`에 본인의 사이트맵 URL를 추가
	- `본인 블로그 주소/sitemap.xml`
- `제출` 버튼 클릭

<br/>

![image](https://github.com/user-attachments/assets/a0248e22-f9f4-42f3-9895-56181cf30ae8)
- 제출 완료

<br/>

![image](https://github.com/user-attachments/assets/67ddf1fb-692c-457b-8e8b-f524806b0cff)
- 하지만 상태가 빨간 것을 보아하니 뭔가 잘못된 것 같이 보이지만 정상적으로 작동 중
- 상태가 초록색으로 변할 때까지 시간이 필요

<br/>

![image](https://github.com/user-attachments/assets/36b2b788-5fc0-4cae-b4eb-5efa52de0825)
- 작성자는 Chirpy 테마를 사용하고 있기 때문에 `feed.xml`도 추가 (Option)

<br/>

![image](https://github.com/user-attachments/assets/8b5d687f-928b-4e49-b733-ab1097883af5)
- 시간이 소요됨

<br/>

![image](https://github.com/user-attachments/assets/6c907a5b-6e33-4c99-b7f8-2dfa307c48a6)
- 상단의 `URL 검사`를 사용하여 본인 깃 블로그 주소를 입력
- 뜨기까지 시간이 걸릴 뿐 잘 등록되어 있는 것을 확인
- Google 검색 엔진 노출 완료

<br/>

### 3-2. Naver 검색 엔진 노출

- **NAVER Search Advisor** 등록
	- https://searchadvisor.naver.com/

<br/>

![image](https://github.com/user-attachments/assets/dd29d20f-221f-40a0-9d2c-f92cd1d9f9cc)
- 스크롤하면 위와 같은 부분이 등장
- `웹마스터 도구 사용하기` 클릭

<br/>

![image](https://github.com/user-attachments/assets/29a18cd9-ec1d-483f-9057-cacc7247dfa9)
- 깃 블로그 URL 입력 후 확인

<br/>

![image](https://github.com/user-attachments/assets/06cf06d8-7eff-437f-92fc-e567e2eec168)
- **HTML 태그** 사용
- `content` 부분에 있는 것을 복사
	- **`" "`**까지 복사
- 아직 `소유확인` 버튼은 누르지 말 것

<br/>

![image](https://github.com/user-attachments/assets/b914d6f8-f534-4817-9bdf-b19a8d829b97)
- 깃허브 `_config.yml` 중 `webmaster_verifications`에서 `naver` 있다면 해당 부분에 복사한 것을 붙여넣고, 없다면 직접 추가한 후 복붙
- commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/4c9a22e0-22f9-4e41-8210-6affb3a58439)
- 다시 NAVER Search Advisor로 돌아와 `소유확인` 버튼 클릭
- **에러 발생**
- 이는 `config.yml`에 `naver`를 직접 추가했기 때문에 발생

<br/>

![image](https://github.com/user-attachments/assets/f3fabba1-5b8b-4a18-a6eb-05cb4b9755fc)
- 잘 보니 이 내용을 `<head>` 섹션에 넣으라고 알려줌
- 이번엔 `meta name`과 `content`를 전부 복사

<br/>

![image](https://github.com/user-attachments/assets/67d95313-4ac7-4121-b74b-455890d36a03)
- 깃허브 `_includes/head.html`에서 아무 곳에 복붙
- `_config.yml`에 추가했던 `naver` 부분은 삭제
- commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/6566dca7-ae2e-4167-9fef-79642a974906)
- 다시 NAVER Search Advisor로 돌아와 `소유확인`클릭
- 소유 확인 완료
- 본인의 URL를 클릭

<br/>

![image](https://github.com/user-attachments/assets/fa95b0db-22a6-49ba-9d31-ec4ce0b5ee1a)
- 좌측 메뉴에서 `요청`-`사이트맵 제출`로 진입
- 사이트맵 URL 입력
	- `본인의 블로그 주소/sitemap.xml`
- `확인` 버튼 클릭

<br/>

![image](https://github.com/user-attachments/assets/1d598df4-7f72-45a8-9fb9-e1f928af9c6e)
- 제출 완료
- Google과 같이 적용엔 시간이 걸림
