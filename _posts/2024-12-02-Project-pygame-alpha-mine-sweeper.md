---
layout: post
title: "Project-pygame-alpha-mine-sweeper 프로젝트 제작기"
categories: Project/Project-pygame-alpha-mine-sweeper
tags: [project, Git, pygame, python]
---

![image](https://github.com/user-attachments/assets/62db45b5-d558-4dd2-a996-695dc971f17d)

## 1. 프로젝트 개요
- 주제 : pygame을 이용한 **`윷놀이 게임`** 제작
- 프로젝트 기간 : 2024.09 ~ 2024.12.05
- 팀명 : alpha
- 팀원수 : 4
- 방법론 : 애자일
- 사용한 라이브러리 및 도구
  - `pytnon3`
  - `pygame 2.6.0`
  - VS Code
- git link : https://github.com/SKHU-OSS-2024-2/pygame-alpha-mine-sweeper

> 2024년 성공회대학교 [오픈소스SW개발] 강의 내 이루어진 게임 제작 프로젝트입니다. 저희 alpha 팀은 모두가 쉽게 즐길 수 있는 윷놀이 게임을 주제로 정하였습니다. 윷과 윷판이 없어도 언제 어디서든 친구 혹은 가족과 즐기실 수 있도록 제작하였습니다.

#### 프로젝트 목표
1. `pygame`을 사용하여 누구나 쉽게 즐길 수 있는 **윷놀이 게임**을 개발
2. 해당 코드를 **오픈소스**로 배포함으로써 학업을 진행하는 다른 학생들에게 코드 제

<br/>

## 2. 코드 분석 및 설계
 결과물 파일은 총 5개가 존재한다.
- `main.py` : 메인 실행 파일, 게임 실행의 진입점
- `Game.py` : 게임의 주요 로직
- `Player.py` : 플레이어 관련 로직
- `Node.py` : 
- `Horse.py` : 
- `gameboard.py` : 게임 보드와 관련된 기능 구현---
layout: post
title: "Project-pygame-alpha-mine-sweeper 프로젝트 제작기"
categories: Project
tags: [project, Git, pygame, python]
---

## 1. 프로젝트 개요
- 주제 : pygame을 이용한 **`윷놀이 게임`** 제작
- 프로젝트 기간 : 2024.09 ~ 2024.12.05
- 팀원수 : 4
- 방법론 : 애자일
- git link : https://github.com/SKHU-OSS-2024-2/pygame-alpha-mine-sweeper

> 2024년 성공회대학교 [오픈소스SW개발] 강의 내 이루어진 게임 제작 프로젝트입니다. 저희 alpha 팀은 모두가 쉽게 즐길 수 있는 윷놀이 게임을 주제로 정하였습니다. 윷과 윷판이 없어도 언제 어디서든 친구 혹은 가족과 즐기실 수 있도록 제작하였습니다.

<br/>

## 2. 코드 분석 및 설계
 결과물 파일은 총 5개가 존재한다.
- `main.py` : 윷놀이 게임의 주요 실행 흐름 정의
- `Game.py` : 게임의 전체적인 로직 관리
- `Player.py` : 플레이어 객체 정의
- `Node.py` : 이중 연결 리스트를 사용하여 윷놀이판의 노드 구조 정의 및 노드 간의 연결 설정
- `Horse.py` : 말 객체를 정의 및 말의 초기 위치와 현 위치 관리
- `gameboard.py` : 윷놀이판과 UI를 그리는 그래픽 처리 및 윷 던지기와 말 이동과 같은 주요 이벤트 관리

### 2-1. `main.py`
 윷놀이 게임의 주요 실행 흐름을 정의한다. 게임을 시작할 때에도 배포되어 있는 `exe` 파일 또는 `main.py` 파일을 실행시켜야 한다.

<br/>

#### 초기화
**1. pygmae 초기화**
```python
pygame.init()
```
`pygame`의 기능을 사용하기 위한 초기화 작업이다.

<br/>

**2. 화면 설정**
```python
window_size_x = 800
window_size_y = 600
screen = pygame.display.set_mode((window_size_x, window_size_y))
pygame.display.set_caption("윷놀이")
```
 게임의 화면 크기와 제목을 설정한다. **800x600** 해상도를 사용하며, 게임 이름은 `윷놀이`이다.

<br/>

#### 인트로 화면
```python
player_num_2_button_rect = pygame.Rect(button_size_x * 1, button_size_y * 1, button_size_x * 5, button_size_y * 13)
player_num_2_button_color = ORANGE
```
**다중 플레이어 버튼** : `Intro()` 함수는 게임 시작 시 인트로 화면에서 2인용, 3인용, 4인용 버튼을 생성하는 로직을 포함한다. 각 버튼은 PyGame의 `Rect`를 사용해 화면 상에 위치와 크기를 설정하고, 색상을 채워넣는다.

<br/>

```python
while running:
    screen.fill(WHITE)
    ...
    pygame.draw.rect(screen, player_num_2_button_color, player_num_2_button_rect)
    ...
```
PyGame의 메인 루프를 통해 버튼이 그려지고, 사용자의 입력을 기다린다.

<br/>

![image](https://github.com/user-attachments/assets/fdb59c85-a189-46cb-9dbb-f42475381fb2)
위와 같이 게임을 실행하면 플레이어수를 선택할 수 있는 창이 뜬다.

<br/>

### 2-2. `Game.py`
`Game.py` 파일은 게임의 주요 로직과 흐름을 담당한다.

<br/>

#### 클래스 정의
```python
class Game:
```
`Game` 클래스는 게임의 전체적인 구조를 관리한다. 보드 생성, 플레이어 설정, 게임 라운드 진행 등의 기능을 수행한한다.

<br/>

#### 초기화 메서드
```python
def __init__(self):
```
  - **보드 생성**
    - ```python
      self.board = Node.DoublyLinkedList()
      self.board.create_structure()
      ```
    - `Node` 모듈의 이중 연결 리스트를 사용하여 게임 보드를 설정한다.
  - **플레이어 수 입력**
    - ```python
      while True:
      num_players = int(input("Enter the number of players (2-4): "))
      ...
      ```
    - 유효한 플레이어 수(2~4명)를 입력받는다.
  - **플레이어 초기화**
    - ```python
      self.players = [Player.Player(i + 1, num_horses_per_player, self.board) for i in range(num_players)]
      ```
    - 각 플레이어 객체를 생성하고 보드와 연결한다.

<br/>

#### 라운드 진행
```python
def play_round(self):
    for player in self.players:
        dice_result = player.roll_dice()
        print(f"Player {player.player_id} 님의 차례입니다.")
        print(f"주사위의 값: {dice_result}")
```
- 각 플레이어가 주사위를 굴리는 과정을 처리하며 결과를 출력한다.
- 플레이어의 차례를 순차적으로 진행한한다.

<br/>

#### 재정의된 `__repr__` 메서드
```python
def __repr__(self):
    return f"Game with players: {self.players}"
```
게임 객체의 간단한 설명을 반환한다.

#### 코드 구조 요약
- **보드와 플레이어의 관계** : `Node`와 `Player` 모듈을 통해 게임 보드와 플레이어를 체계적으로 연결.
- **사용자 입력 처리** : 유효한 값만 입력받도록 반복문 활용.
- **주사위 결과 처리** : `roll_dice()` 메서드를 통해 각 플레이어의 이동 제어.

<br/>

### 2-3. `Player.py`
`Player.py` 파일은 게임의 각 플레이어와 관련된 기능을 구현한다.

<br/>

#### **클래스 정의**
```python
class Player:
```
`Player` 클래스는 각 플레이어의 속성과 동작을 정의한다.

<br/>

#### **초기화 메서드**
```python
def __init__(self, player_id, num_horses, board):
```
  - **플레이어 ID**
    - ```python
      self.player_id = player_id
      ```
    - 각 플레이어에 고유 ID를 부여하여 식별한다.
  - **말 객체 생성**
    - ```python
      self.horses = [Horse.Horse(i + 1, board) for i in range(num_horses)]
      ```
    - 플레이어가 보유한 말을 `Horse` 클래스를 통해 초기화한다. 말 객체는 보드와 연결된다.

<br/>

#### **주사위 굴리기**
```python
def roll_dice(self):
    return random.choice([-1, 1, 2, 3, 4, 5])
```
- 플레이어가 주사위를 굴리는 동작을 정의한다.
- 결과는 `-1`(패배), `1~5`의 값 중 하나로 무작위 선택된다.

<br/>

#### 재정의된 `__repr__` 메서드
```python
def __repr__(self):
    return f"Player {self.player_id} with horses: {self.horses}"
```
플레이어와 해당 말의 정보를 반환한다.

<br/>

#### 코드 구조 요약
- **객체 지향 설계** : `Player` 클래스는 말(Horse) 객체를 리스트로 관리하며, 유연한 설계 방식 채택.
- **주사위 로직** : 간단한 난수 생성 방식으로, 플레이어가 각 턴에서 이동할 거리 또는 특수 동작(-1)을 결정.

<br/>

### 2-4. `Horse.py`
`Horse.py` 파일은 게임에서 말 객체의 역할을 정의하는 간단한 구조를 가지고 있다.

<br/>

#### **클래스 정의**
```python
class Horse:
```
`Horse` 클래스는 각 말의 속성과 동작을 정의한다.

<br/>

#### 초기화 메서드
```python
def __init__(self, horse_id, board):
```
  - **말 ID**
    - ```python
      self.horse_id = horse_id
      ```
    - 각 말을 고유하게 식별하는 ID 설정
  - **초기 위치**
    - ```python
      self.position = board.nodes[0]
      ```
    - 말을 게임 보드의 시작 지점에 배치한다.

<br/>

#### 재정의된 `__repr__` 메서드
```python
def __repr__(self):
    return f"Horse {self.horse_id} at Node {self.position.value}"
```
말의 ID와 현재 위치를 반환하여 게임 진행 중 상태를 출력할 수 있다.

<br/>

#### 코드 구조 요약
- **객체 지향 설계** : `Horse` 클래스는 말을 게임 보드의 노드와 연결하며, 간단하지만 명확한 구조.
- **보드와의 연결** : `board.nodes[0]`을 통해 게임 보드의 첫 번째 노드와 말 연동.

<br/>

### 2-5. `Node.py`
`Node.py` 파일은 게임 보드의 구조를 정의하며, 각 노드가 연결된 이중 연결 리스트 형태로 설계되었다.

<br/>

#### `Node` 클래스
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        self.prev = None
```
- **노드 값** : 각 노드는 고유한 값을 가지며, 이를 통해 보드 상의 위치를 나타낸다.
- **연결 구조** : next와 prev를 사용해 다음과 이전 노드와의 연결을 설정한다.

<br/>

#### `DoublyLinkedList` 클래스
```python
class DoublyLinkedList:
    def __init__(self):
        self.nodes = {}
```
**노드 저장소** : `nodes` 딕셔너리를 통해 노드를 관리하며, 값으로 노드 객체를 저장한다.

<br/>

#### 노드 추가
```python
def add_node(self, value):
    new_node = Node(value)
    self.nodes[value] = new_node
    return new_node
```
주어진 값을 가진 노드를 생성하고, `nodes`에 추가한다.

<br/>

#### 노드 연결
```python
def connect_nodes(self, value1, value2):
    node1 = self.nodes.get(value1)
    node2 = self.nodes.get(value2)
    if node1 and node2:
        node1.next = node2
        node2.prev = node1
```
두 노드를 서로 연결하여 이중 연결 리스트를 구성한다.

<br/>

#### 보드 구조 생성
```python
def create_structure(self):
    for i in range(6):
        self.add_node(i)
        if i > 0:
            self.connect_nodes(i - 1, i)
    ...
```
- 게임 보드의 전체 구조를 생성한다.
- 순환 경로를 포함해 다양한 지점을 연결하며, 게임의 특수 규칙(예: 루프 구조)을 반영한다.

<br/>

#### 코드 구조 요약
- **유연한 설계** : DoublyLinkedList를 사용하여 게임 보드를 체계적으로 생성하고 관리.
- **순환 경로 구현** : 보드의 마지막 노드에서 첫 번째 노드로 연결되도록 설계.

<br/>

## 3. 결과물
- 시작 화면
  - ![image](https://github.com/user-attachments/assets/fdb59c85-a189-46cb-9dbb-f42475381fb2)
  - 플레이어의 인원을 2~4명까지 선택할 수 있다.

- 플레이 화면
  - ![image](https://github.com/user-attachments/assets/c6a4f94f-c4fd-4d56-acfb-312f6a37d32e)
  - 빨강 팀이 [윷 던지기] 버튼을 눌러 게임을 시작한다.

<br/>

|                          게임 설정                           |                           게임 룰                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| - PvP 형식입니다.<br />- Player는 2~4명입니다. <br />- 윷놀이의 말은 4개입니다.<br />- 말의 첫 시작 위치는 우측 하단입니다.<br />- 도착 지점을 초과해야 골인됩니다.<br />- 먼저 말이 4개 도착한 Player가 승리합니다. | - Player 1이 윷을 던집니다.<br />- Player 1이 나온 윷 만큼 이동합니다.<br />- Player 2가 윷을 던집니다.<br />- Player 2가 나온 윷 만큼 이동합니다.<br />- 윷 또는 모가 나올 경우 윷을 한 번 더 던집니다.<br />- 적군의 말을 잡을 경우 윷을 한 번 더 던집니다.<br />- 아군의 말과 마주친 경우 업힙니다.<br />- 윷판의 각 모서리, 혹은 정중앙에 도착할 경우 꺾어 움직일 수 있습니다.<br />- 윷판에 아군의 말이 존재할 경우 새로운 말을 꺼낼 건지, 본래 있던 말을 움직일 건지 선택할 수 있습니다. |

<br/>

#### 플레이 순서
- ![image](https://github.com/user-attachments/assets/7af16631-7628-4658-af10-7287b94cb9fa)
- 1. [윷 던지기] 버튼을 클릭하여 윷을 던진다.
   - [윷] 또는 [모]가 나올 경우, 말을 이동시키기 전 윷을 한 번 더 던진다.

<br/>

- ![image](https://github.com/user-attachments/assets/5602f599-b6dc-4ade-9275-6df5d7d19c5b)
- 2. 새로운 말을 출전시킬 거라면 [새 말] 버튼을 클릭하고 이동시킬 결과(빽도~모) 버튼을 클릭한다.

<br/>

- ![image](https://github.com/user-attachments/assets/a0d04559-b44c-4014-bfb0-2bf8e45baa56)
- 3. 이미 출전되어 있는 말을 움직일 거라면 [말 선택] 우측에 위치해 있는 이동시킬 말 번호를 클릭하고 이동시킬 결과(빽도~모) 버튼을 클릭한다.(해당 버튼은 숫자로 표기되어 있다.)

<br/>

- ![image](https://github.com/user-attachments/assets/5ecffd08-4b18-47e9-805d-2dafbf4adcdb)
- 4. 이동시킬 결과 버튼을 클릭하면 말이 갈 수 있는 위치에 주황색으로 표기된다. 이동하고 싶은 주황색 위치를 클릭하면 말이 움직인다.
  - 이 때에도 움직일 말을 변경하고 싶은 경우 2번을 참고하여 변경할 수 있다.

<br/>

- ![image](https://github.com/user-attachments/assets/b57a0aa7-f10c-41bb-9a87-66ae183ee726)
- 5. [출발] 지점 대각선의 위치하는 주황색 버튼을 클릭하면 골인한다.

<br/>

- ![image](https://github.com/user-attachments/assets/93037734-a4a6-45c6-aa60-0d893d1450a7)
- 6. 골인할 경우 우측에 존재하는 스코어가 올라간다.

<br/>

- 7. 1~5번을 반복하여 먼저 4개의 말을 골인시킨 플레이어가 승리한다.

<br/>

## 4. Github 협업 과정
 게임의 완성도보다도 어찌보면 더욱 신경쓰려 노력했던 Github 협업 과정에 대해 설명한다. 작성자는 Github를 사용한 프로젝트 경험이 있었지만, 운영을 해보는 것은 처음이었다.

<br/>

#### `README.md` 작성
 프로젝트의 주제와 실행 방법을 **공지**하기 위하여 `README.md`를 작성했다. 해당 내용은 너무 길기 때문에 상단에 지정해둔 Git 링크를 통하여 직접 확인하는 것이 좋다. `README.md`는 팀원 뿐만 아닌 제3자가 보기에도 게임을 어떤 식으로 실행시키고, 진행되는 지 알 수 있도록 다음과 같은 내용을 넣었다.
- **`README.md`에 들어가야 하는 내용**
  - 프로젝트 주제
  - 프로젝트 개요
  - 설치 방법
  - 실행 방법
  - 게임 설명
  - 게임 플레이 방식

<br/>

#### LICENSE
![image](https://github.com/user-attachments/assets/d0a0b4ad-adfb-447b-b975-bf10a94e0880)
 프로젝트의 코드를 **오픈소스**로 배포하기 위하여 **MIT**의 라이선스를 추가했다.

<br/>

#### 작업 환경 구성
 각 팀원은 프로젝트 레포지토리를 fork하여 개인 작업을 진행했다. 커밋 메시지 규칙을 정하여 통일감을 주었고, 가독성 또한 뛰어나도록 하였다.
- **커밋 메시지 규칙**
> **`[type] 파일명`** 형식
- `type`
  - `feat` : 새로운 파일 추가
  - `fix` : 기존 파일 수정

<br/>

#### Pull Request 관리
![image](https://github.com/user-attachments/assets/aed9f79a-5445-4038-a2e9-3120e5daf80b)
![image](https://github.com/user-attachments/assets/b37a13f5-e7dd-4ddb-b366-1c789e625036)
 PR 작성 시 `.github/pull_request_template.md`를 사용해 일정한 형식을 유지했다. 템플릿을 작성할 땐, 누가 쓰던 일정할 수 있도록 주석을 적극 활용하였다.
- **PR 템플릿**
> ![image](https://github.com/user-attachments/assets/b2a36b97-01dc-4bf6-9ef8-7dd7bbc19fbe)

 또한 모든 PR에 라벨을 붙이고 리뷰어를 지정한 뒤 팀원 모두가 확인 댓글을 작성하면 Merge를 진행했다. 따라서 정리된 PR 순서를 시각화하면 다음과 같다.
![image](https://github.com/user-attachments/assets/ebca5a20-cf52-4615-bf92-2dd1b7528ee8)

<br/>

#### ISSUE 활용
![image](https://github.com/user-attachments/assets/8734af99-c602-400c-8e60-c71fbf5d8227)
회의록, 문제점, 향후 계획 등을 기록하고 논의하는 데 사용했다. 이슈 또한 라벨을 붙여 내용을 찾기 쉽도록했다.

<br/>

![image](https://github.com/user-attachments/assets/9ae7870c-bc23-4169-843d-cddc4a04daa2)
체크리스트를 사용하여 무엇을 했고, 무엇을 해야하는 지 빠르게 확인할 수 있도록 했다.

<br/>

## 5. 결론 및 배운 점
 본 프로젝트는 Github를 중심으로 협업하는 환경에서 효과적인 팀워크를 구축하는 데 중점을 두었다. Github의 다양한 기능을 활용하며 여러가지를 배웠는데 그는 다음과 같다.

<br/>

1. 표준화된 워크플로우의 중요성
  - PR 템플릿과 커밋 메시지 규칙을 적용하므로써, 코드 리뷰 과정이 효율적으로 진행되었다. 팀원이 어떤 변경 사항을 제안했는지 명확히 이해할 수 있었고 리뷰 시간을 단축하는 데 크게 기여했다.

<br/>

2.  이슈 기반 소통
  - GitHub ISSUE를 통해 논의할 내용을 구조화하고, 회의록과 계획을 기록하는 습관을 형성했다. 이를 통해 모든 팀원이 동일한 목표와 진행 상황을 공유할 수 있었으며, 막힌 부분에 대한 신속한 협의가 가능했다.

<br/>

3. 라벨과 리뷰어 지정의 효율성
  - PR에 라벨을 붙이고 리뷰어를 지정함으로써, 어떤 작업이 진행 중인지 빠르게 파악할 수 있었다. 또한, 모든 팀원이 리뷰를 완료한 후에 Merge를 진행하는 규칙을 통해 정확성을 유지할 수 있었다.

<br/>

4. Fork 기반 개발의 장점
  - 팀원 개별 레포지토리에서 작업 후 PR로 팀 레포지토리로 병합하는 방식은 충돌을 최소화하면서도 자유롭게 실험하고 수정할 수 있는 환경을 제공했다.

<br/>

다음에도 힘내야겠다. 아자!
