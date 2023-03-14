---
title: 메모리(Memory) 가 무엇인지 설명해주세요
date: 2023-02-20T22:54:22+09:00
categories: ["운영체제",] #카테고리 설정
tags: ["메모리",] #태그 달기
author: 박종호 #본인 이름 넣기  
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

## 메모리(Memory) 란?

![[https://information-factory.tistory.com/59](https://information-factory.tistory.com/59)](images/Untitled.png)

> CPU가 연산하기 위한 프로그램을 일시적으로 저장하는 공간


- 메모리란 원래 컴퓨터 시스템에 무언가를 저장하는 공간 (RA**M**, RO**M**의 마지막 글자는 **M**emory의 약자)
> Hardware 반도체 소자분야에서는 크게 휘발성인 RAM과 비휘발성인 ROM으로 나뉘고 SW 입장에서는 크게 CPU 캐시메모리 / CPU 레지스터(SRAM), **주기억장치(DRAM == 메모리)**, 디스크(SSD), 롬(ROM, 모니터 마우스 키보드 통신을 위한 BIOS), swap 메모리, 가상메모리, 플래시메모리(휴대저장장치인 USB메모리) 등이 있음

## 메모리(DRAM)의 특징

- 순차접근이 아닌 **임의접근(Random Access)** 방식으로 동작함
- DRAM 내부의 Capacitor 에 저장되는 전하는 빠르게 방전되기 때문에, 전력이 유지되지 않으면 데이터가 사라지는 **휘발성 메모리**임
- CPU 가 디스크(SSD) 에서 데이터 처리속도를 기다리게 되는 병목현상을 해결해주는 **빠른속도의 데이터 처리 중간지점 역할**

![[https://information-factory.tistory.com/59](https://information-factory.tistory.com/59)](images/Untitled1.png)

## MMU(Memory Management Unit) 란?

![[http://recipes.egloos.com/5232056](http://recipes.egloos.com/5232056)](images/Untitled2.png)


- 메모리 보호나 캐시 관리 등 CPU가 메모리에 접근하는 것(논리주소 → 물리주소)을 총 관리해주는 하드웨어
- 사용자에게 더 많은 메모리 공간을 제공하기 위해, 프로그램 상에서 사용자가 보는 주소 공간인 가상 주소에서 실제 데이터가 담겨 있는 곳에 접근하기 위해선 빠른 주소 변환을 도와줌

> MMU가 지원되지 않으면, Physical Address를 직접 접근해야 하기 때문에 부담이 있다.
→ MMU는 사용자가 기억장소를 일일이 할당해야 하는 불편을 없애준다. → 프로세스의 크기가 실제 메모리의 용량을 초과해도 실행될 수 있게 해준다.
> 

### MMU의 메모리 보호 방식

> 프로세스는 **독립적인 메모리 공간**을 가져야 하고, 자신의 공간만 접근해야 한다.
따라서 MMU는 한 프로세스에게 합법적인 주소 영역을 설정하고, 잘못된 접근이 오면 trap을 발생시키며 보호한다.
> 

### base와 limit 레지스터를 활용한 메모리 보호 기법

- **base 레지스터** : 메모리상의 프로세스 시작주소를 물리 주소로 저장
- **limit 레지스터** : 프로세스의 사이즈를 저장

P.S. 레지스터란? **프로세서가 바로 사용할 수 있는 데이터를 담고 있는 영역**

> 프로세스의 접근 가능한 합법적인 메모리 영역(`x`)은 `base <= x < base+limit` 이 된다.
따라서 이 영역 밖에서 접근을 요구하면 trap 을 발생시킨다.
또한 안전성을 위해 base와 limit 레지스터는 사용자 모드에서는 직접 변경할 수 없도록 **커널 모드에서만 수정 가능**하도록 설계되었다.
> 

![[http://recipes.egloos.com/5232056](http://recipes.egloos.com/5232056)](images/Untitled3.png)