---
layout: post
title: "Github Page 블로그 구축"
categories: Github-Page
---

## 1. Repository 생성

![image](https://github.com/user-attachments/assets/73b21b35-c0a4-45dd-a471-987d4d19d083)
- 공개를 `Public`으로 설정
- `Add a README file` 체크

- `Create repository`

<br/>

## 2. Githib Page Setting

![image](https://github.com/user-attachments/assets/7e1db4e8-10f1-40cd-9a2b-29ff2a107147)
- 생성한 repository로 이동하요 상단 바에 존재하는 `Settings` 진입

<br/>

![image](https://github.com/user-attachments/assets/4e46ef3e-a04d-421c-82f0-4888261f6128)
- `Pages`에서 Source가 `Deploy from a branch`로 설정되어 있는 지 확인

<br/>

![image](https://github.com/user-attachments/assets/d442178e-8cae-480c-822d-a5a38b8a28a0)
- `https://리포지토리명`으로 사이트에 접속이 가능한지 확인

<br/>

## 3. Repository Clone

![image](https://github.com/user-attachments/assets/0c36ffca-0e7c-40a3-bc73-6e6ec95e8b5a)
- VS Code를 사용하여 Clone
  - `F1`을 눌러 `Git: Clone`을 검색하고 선택

<br/>

![image](https://github.com/user-attachments/assets/242b5502-2364-42b3-bf2c-ffdd79ec8311)
- 생성한 repository를 입력하고 선택

<br/>

![image](https://github.com/user-attachments/assets/20fd35ef-dc52-4495-9182-a450d4c405f4)
- 클론할 위치를 선택
  - 한글이 포함된 경로는 위험

<br/>

![image](https://github.com/user-attachments/assets/57c32cdc-5d47-4617-aace-1d7f837b7ebf)
- 클론됨

<br/>

![image](https://github.com/user-attachments/assets/2ed80482-8c52-4451-b7b6-0d71277e06f5)
- `index.html` 파일을 생성하여 내용 입력

<br/>

![image](https://github.com/user-attachments/assets/ab397909-42dc-4465-997e-254890708b24)
- 좌측 바에 있는 `Source Control` 메뉴 선택
- `+` 버튼을 클릭

<br/>

![image](https://github.com/user-attachments/assets/999b088f-b79d-493e-85bf-3468296aa0be)
- 변경사항 추가 완료

<br/>

![image](https://github.com/user-attachments/assets/1229a483-6a0b-4d10-bdb1-70f312bdf5ae)
- commit 메시지 입력

<br/>

![image](https://github.com/user-attachments/assets/142d9e3f-0de6-4341-b084-be74334cc50d)
- `Sync Changes`를 클릭하면 위와 같은 창이 뜨는데 `OK`를 눌러 push

<br/>

## 4. 로컬 개발 환경 구축

- `Ruby` 설치
  - https://rubyinstaller.org/downloads/
  - 위 사이트에서 최신 버전 다운로드

<br/>

![image](https://github.com/user-attachments/assets/aa7d94c9-1c7b-42de-822b-8d8295de2b51)
- Window 메뉴에서 `Start Command Prompt with Ruby` 실행

<br/>

```ruby
cd C:\blog\roalzlwm.github.io
```

- `cd` 명령어를 이용하여 repository가 있는 위치로 이동
  - 만약 폴더명에 띄어쓰기가 존재한다면 경로를 `' '`으로 묶음

<br/>

```ruby
gem install jekyll bundler
gem install webrick
```

- `jekyll`, `bundler`, `webrick` 설치

<br/>

![image](https://github.com/user-attachments/assets/933cfcca-cab1-4560-a17c-1a07f10e9277)
- `-v`를 사용하여 설치가 되었는지 확인

<br/>

![image](https://github.com/user-attachments/assets/6e37d965-e8d8-437c-8faf-6bf5b7b7e4b4)
```ruby
jekyll new ./ --force
```

- 해당 폴더(repository 폴더)에 `jekyll` 생성

<br/>

![image](https://github.com/user-attachments/assets/27fc8079-ab63-4980-877b-fc3f71b9c53d)
```ruby
bundle install
```

- `bundle` 설치

<br/>

![image](https://github.com/user-attachments/assets/efb94583-deff-4009-9014-0ee356d7f018)
```ruby
bundle exec jekyll serve
```

- `jeckyll` 서버 실행 

- 서버 실행 중이라고 함

<br/>

![image](https://github.com/user-attachments/assets/0d7f27cd-fc9a-4b08-9cea-0c476edde636)
- `Server address`에 접속
- `index.html`에 입력한 내용이 뜸

<br/>

## 5. 테마 적용

- 테마는 여러가지가 있음 원하는 것은 다운로드하면 됨
  - 테마별 적용 방법이 다를 수 있음
  - [http://jekyllthemes.org](http://jekyllthemes.org/)
  - https://jekyllthemes.io/free
  - [https://themes.jekyllrc.org](https://themes.jekyllrc.org/)
  - https://github.com/topics/jekyll-theme

<br/>

- `chirpy` 테마를 적용하기로 결정
  - https://github.com/cotes2020/jekyll-theme-chirpy
  - Download ZIP으로 저장 및 압축 해제

<br/>

![image](https://github.com/user-attachments/assets/520dd40a-f4e4-41b2-abe5-b1e2325dda9e)
- 테마 폴더의 모든 파일 복사

<br/>

![image](https://github.com/user-attachments/assets/3ca8ec98-baca-4e6e-9926-4f44669284c5)
- 로컬 리포지토리에 붙여넣기
  - 이름이 같은 파일을 덮어씀

<br/>

![image](https://github.com/user-attachments/assets/ad8b520d-79e2-4c5f-b206-0c3d579bc8c3)
- 다시 `Start Command Prompt with Ruby`로 돌아가서 `bundle exec jekyll serve`로 돌아가고 있던 것을 `ctrl+c`를 사용해 중지

- 테마를 저장하기 위해 다시 실행

<br/>

```ruby
bundle install
```

- `bundle` 설치

<br/>

```ruby
bundle exec jekyll serve
```

- `jekyll` 서버 실행

<br/>

![image](https://github.com/user-attachments/assets/f3787205-6678-40ad-bc58-23c3cdb1e7d8)
- `Server address`로 들어가면 테마가 적용된 것을 확인할 수 있음

<br/>

![image](https://github.com/user-attachments/assets/ab561285-e997-47ff-ac29-b2d199c96d61)
- VS Code로 돌아가 변경사항은 commit 및 push

<br/>

![image](https://github.com/user-attachments/assets/375485ba-f47e-47d6-ba2d-c3628f04cb56)
- 변경할 commit 사항이 없다고 뜨는데, 무시하고 `Yes`를 클릭
- push도 진행

<br/>

![image](https://github.com/user-attachments/assets/48a22bcf-4adb-4ca8-a809-497828fb03d4)
- 원격 repository로 돌아가 다시 상단의 `Settings`로 이동
- 좌측 `Pages`에서 Source를 `Github Actions`로 변경

<br/>

![image](https://github.com/user-attachments/assets/b4dd547c-03b5-4dbf-8334-f4363bb3504c)
- `Configure` 클릭

<br/>

![image](https://github.com/user-attachments/assets/7ca63e57-4600-452d-b4a0-87a761db4d77)
- `Commit changes...` 클릭

<br/>

![image](https://github.com/user-attachments/assets/6a34b06e-d91f-4135-b21c-7a203afc4aed)
```bash
$ git pull
```

- `git bash`를 사용하여 local repository에 pull

<br/>

## 6. 테마 상세 설정

- Node.js 설치
  - https://nodejs.org/en/
  - `next`만 누르면 설치됨

<br/>

```ruby
npm install && npm run build
```

- `Start Command Prompt with Ruby`에서 위 명령어 실행
  - 실행이 안 될 경우 프롬프트 창을 껐다가 다시 실행
  - 잘 되고 있는지 모르겠다 싶을 때 `Enter`를 누르면 뜸

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/652a3502-08a9-414b-889f-0653494b587d/image.png)

- 설치 및 빌드 완료

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/7058da5b-f689-43a1-a2a9-3c66bd080f84/image.png)

```
# Misc
# _sass/dist
# assets/js/dist
```

- `.gitignore` 파일 중 Misc 부분을 주석 처리

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/d978c910-0743-4ed6-b618-851ea117fcea/image.png)

- `_config.yml` 파일을 위와 같이 수정
  - timezone : `Asia/Seoul`로 수정
  - url : `https://원격 리포지토리명`으로 수정
  - username : `유저명`으로 수정

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/e943707d-c17e-4e47-8cd4-a194daa37ec7/image.png)

- 변경 내용은 commit 및 push

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/be0d8328-6668-4924-8a3d-af88e5d4c6be/image.png)

- commit 도중 위와 같은 오류가 떴음
  - 해당 오류는 아래와 같을 때 뜸
    - Node.js가 제대로 설치되어 있지 않을 때
      - `-v`를 사용하여 설치가 되었는지 확인
      - `node -v`, `npm -v`
    - Node.js가 경로에 추가되지 않았을 때
    - Node.js가 설치되고 VS Code에 적용되지 않았을 때
      - VS Code를 재실행

- VS Code를 재실행하였더니 제대로 실행됨

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/62f68058-13d3-4e4f-aba7-25cbb5bab27a/image.png)

- 위와 같은 오류가 뜸

  - 아무래도 모르고 원격 리포지토리에서 먼저 `.gitignore`과 `_config.yml`를 커밋하고 로컬 리포지토리에서 다시 수정하고 커밋하려 하니 충돌이 일어난 것 같음

- 해결

  - `git bash` 혹은 VS Code에서 Terminal를 열음

  - 변경 사항 stash

    - 로컬에서 작업한 변경 사항을 임시로 저장

    - ```bash
      git stash
      ```

  - 원격 리포지토리에서 최신 변경 사항을 가져옴

    - ```bash
      git pull origin main
      ```

  - stash 적용

    - ```bash
      git stash pop
      ```

  - 변경 사항 커밋 및 푸시

    - ```bash
      git add .
      ```

    - ```bash
      git commit -m "fix: resolve conflicts and apply local changes" 
      ```

    - ```bash
      git push origin main
      ```

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/8d750ca1-e9d1-4a46-ab13-75f6ccb8c8f8/image.png)

- commit 및 push 완료

<br/>

![](https://velog.velcdn.com/images/parkm0708/post/f0b5654f-addd-46cf-9eca-65d612e60634/image.png)
- 적용될 때까지 기다리면 적용 완료
