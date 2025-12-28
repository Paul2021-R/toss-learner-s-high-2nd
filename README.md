# 🚦 Traffic Dam
p(95) 응답시간 53초 → 200ms, SRE 기반 유량 제어 시스템 구축기 
~ 고가용성의 씨앗을 심어보자 ~

### 📊 핵심 성과
- 수치적인 걸로 압축해서 해야함 
- Traffic Dam 이 메인으로 Project Protostar 는 강조 하고 싶지만 조금 참을 것.

### 🎯 프로젝트 요약
- **Project Protostar**: HR 담당자와 개발자를 위한 Agentic AI 챗봇 Demo 서비스
- **Traffic Dam**: SRE 관점의 유량 제어 시스템 (Rate Limiting + Circuit Breaker)
- **1달 간의 사투**: 풀스택 구현 (NestJS + FastAPI + Redis + PLG 모니터링)

---

### 0. 🚩 계기: React2Shell 취약점을 보고 유량 제어의 필요성을 느끼다
- 기술블로그 링크 제시, 간단한 취지 설명

### 1. 🚨 문제: 1,100명이 몰리자 서버가 53초 동안 멈췄다
- 계기를 포함하여 설명 할 것. Before 테스트에 대한 내용의 단편만 제시

### 2. 📊 분석: k6 부하 테스트로 병목 지점을 찾다
- 여기서 제대로 문제가 뭔지, Before 테스트를 통해 온프레미스 서버 관련한 단위, SRE 라는 관점에서 설명 추가할 것

### 3. 🛡️ 해결: Traffic Dam - Rate Limiting + Circuit Breaker
- 어디에 어떤 걸 구축했나?

### 4. 📈 결과: Before vs After
- 결과 제시

### 5. 🚀 확장: 레플리카 2개로 1,200명 수용 
- 증명(제대로 계량한 대로 동작 하고 괜찮았는가?) 
    1. 1개 상태로 기준치 Max일 때, Max 이상일 때 결과 제시. 
    2. 2개 상태로 기준치 Max 이하일 때, 다시 Max 이상일 때 결과 제시. 

### 6. 🛠️ 추가 구현 내역 상세 
- SSE 연결 관리: Heartbeat Timeout, Max Duration TTL
- Nginx 방어: 단일 IP Rate Limiting (limit_req, limit_conn)
- 메시지 큐: Redis Pub/Sub 기반 비동기 처리
- 모니터링: PLG 스택 (Prometheus + Loki + Grafana)
- AI 챗봇: FastAPI + LLM 연동 (RAG 예정)

### 7. 🏗️ 아키텍쳐 & 기술 스택
- Project Protostar 간단 설명 
- 아키텍쳐 그림 및 구체적인 내용 제시(이미지 포함)

### 8. 🎬 데모
- 챗봇 구동 영상 / GIF
- 각 레포 링크
- 기술 블로그 링크