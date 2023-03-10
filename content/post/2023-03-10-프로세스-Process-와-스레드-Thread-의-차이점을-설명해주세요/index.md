---
title: 프로세스(Process) 와 스레드(Thread) 의 차이점을 설명해주세요
date: 2023-03-10T22:06:15+09:00
categories: [""] #카테고리 설정
tags: [""] #태그 달기
author: "Me" #본인 이름 넣기  
description: "" # 부제목 넣기
# author: ["Me", "You"] # 공동저자 일 경우

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: true
disableHLJS: true 
disableShare: false
disableHLJS: false  
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowCodeCopyButtons : true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
ShareButtons: []
---

날짜: 2023/02/11
담당자: 동윤 이
상태: In progress
유형: 운영체제

### 프로그램 (Program)

![Untitled](images/Untitled.png)

ex. 카카오톡, 웹 브라우저 등

### 프로세스 (Process)

![Untitled](images/Untitled%201.png)

- 프로세스란
    - 운영체제로부터 자원을 할당받는 작업의 단위
    - 실행되고 있는 프로그램

- 특징
    - 각각 독립된 메모리 영역을 할당 받음 (Code, Data, Stack, Heap)
        - 코드 : 실행할 프로그램의 코드나 명령어들을 기계어 형태로 저장. 컴파일 → 메모리에 올린 것 (0100101..) 전체 일감
        - 데이터 : 생성자로 생성하지 않고 선언한 전역변수 ex. static, global
        - 힙 : 동적으로 생성된 데이터. 생성자로 만들어짐
        - 스택 : 호출된 함수, 지역변수 등 임시 데이터를 저장. 호출된 함수가 종료되었을 때 되돌아오기 위한 경로를 저장
    - 프로세스당 최소 1개의 스레드를 가짐
    - 한 프로세스가 다른 프로세스의 자원에 접근하려면 IPC(inter process communication)를 사용해야 함

### 스레드 (Thread)

![Untitled](images/Untitled%202.png)

- 스레드란?
    - 할당 받은 자원을 이용하는 실행 단위
    - 프로세스 내에 반드시 하나 이상 생성됨 (→ 여러 개 생길 수 있음)
    - 함수를 실행한 결과를 저장
- 특징
    - 프로세스 내에서 각각 Stack만 따로 할당 받고, Code, Data, Heap 영역은 공유

**[프로세스와 스레드 비유 : 요리](https://www.youtube.com/watch?v=iks_Xb9DtTM)**

- 프로그램 : 레시피
- 프로세서 : 요리사 (프로세스가 동작될 수 있도록 하는 하드웨어 (=cpu))
- 프로세스 : 대량 주문이 들어오는 식당에서 끊임없이 만들어내는 각각의 요리 메뉴
- 컴퓨터는 프로세스마다 자원을 분할해서 할당함 ex. 라면 끓이는 섹션, 김밥 마는 섹션, 햄버거 만드는 섹션
- 라면 끓이는 섹션에 버너 4개 있다면 스레드도 4개를 만들어서 라면이 최대 4개까지 동시에 끓여지도록 프로그래밍

### 프로세스 vs. 스레드

| 프로세스 | 스레드 |
| --- | --- |
| 자원을 공유하지 않음 (독립된 메모리 영역을 할당) | 자원을 공유 (Code, Data, Heap 영역) |
| ↓ | ↓ |
| 다른 프로세스와 정보 공유를 위해 IPC를 사용 | 다른 스레드와 정보 공유가 용이 |
| 하나의 프로세스에 문제가 생겨도 다른 프로세스에 영향을 미치지 않음 | 한 스레드에 문제가 생기면 전체 프로세스에도 영향을 미침 |