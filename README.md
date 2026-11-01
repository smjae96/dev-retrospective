# dev-retrospective

> 개발 이슈·작업·장애를 Problem / How to Solve? / Lesson 세 섹션의 회고록으로 정리해 주는 Claude 스킬

## 왜 만들었나
팀 개발 회고에는 백엔드 개발자뿐 아니라 프론트엔드 개발자, 기획자, 디자이너도 함께 참여한다.
그런데 회고록이 기술 용어 위주로 쓰이면 다른 직군은 "무슨 일이 있었는지"부터 따라오기 어려웠고, 해결 과정도 결과만 남아 왜 그 방법을 골랐는지가 드러나지 않았다.
누구나 읽을 수 있는 언어로, 판단 과정과 일반화된 교훈까지 담도록 형식을 고정했다.

## 언제 쓰나
- "이번 이슈 회고록 써줘"
- "개발 회고 작성해줘"
- "이번 작업 회고록 정리해줘"
- "트러블슈팅 정리해줘"
- "배운 점 정리해줘"

## 무엇을 하나
- 대화 맥락이 부족하면 제목·문제·원인·해결·교훈 중 필요한 것만 짧게 물어본다
- Problem: 배경과 구체적인 증상, 실제 피해·위험을 시나리오로 쓰고, 기술 원인은 비유나 흐름으로 풀어 쓴다
- How to Solve?: 조사 → 방법 선택 → 적용 결과 순으로 쓰고, 대안 비교와 트레이드오프, 검증 방법까지 포함한다
- Lesson: 번호 + 굵은 제목 형식으로, 다른 상황에도 적용 가능한 원칙으로 일반화한다
- 기술 용어는 처음 등장할 때 바로 옆에 쉬운 말로 설명하고, "~했다" 평서형으로 쓴다

## 출력 예시
```
캐시 서버 연결 주소 설정 오류

Problem
dev 서버에서 통계 조회 API를 호출할 때 Redis read 실패 로그가 발생했다. Redis 자체가 죽은 것은 아니었고, 애플리케이션이 Redis를 바라보는 주소가 실행 방식과 맞지 않았다. ...

How to Solve?
두 가지 방법을 고려했다. 첫 번째는 ... 두 번째는 ... 이번에는 두 번째 방법을 선택했다. 이유는 ... 다만 이 선택에는 한계도 있다.

Lesson
1. **같은 서버에 있어도 실행 위치에 따라 접속 주소는 달라질 수 있다**
Docker 컨테이너 안에서 127.0.0.1은 호스트가 아니라 컨테이너 자신을 가리킨다. ...
```

## 설치
Claude Code
```bash
mkdir -p ~/.claude/skills/dev-retrospective
curl -L https://raw.githubusercontent.com/smjae96/dev-retrospective/main/SKILL.md -o ~/.claude/skills/dev-retrospective/SKILL.md
```

Claude 앱(claude.ai): 이 레포 폴더를 zip으로 묶어 설정 > 기능 > 스킬에서 업로드

## 함께 쓰면 좋은 스킬
모음 레포: https://github.com/smjae96/claude-skills
- [work-summary](https://github.com/smjae96/work-summary) — 이슈가 아닌 기능 작업은 what / how / why로 정리
- [cross-project-root-cause](https://github.com/smjae96/cross-project-root-cause) — 회고 전에 FE/BE가 얽힌 버그의 원인을 데이터로 확정

## License
MIT
