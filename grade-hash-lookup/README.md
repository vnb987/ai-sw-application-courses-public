# 성적 확인용 해시(Hash) 조회기

성적을 "이름 — 점수" 형태로 공개하면, 내 점수를 확인하려는 사람도 다른 사람
점수를 구경하려는 사람도 똑같이 전체 명단을 보게 됩니다. 이 노트북은 **이름 +
학번을 넣으면 항상 똑같이 나오는 해시값**을 계산해줍니다 — 성적 게시판에는
이름 대신 이 해시값을 "해시값 — 점수" 형태로 공개하면, 각자 자기 이름과
학번으로 자기 줄만 찾을 수 있습니다.

다룹니다:
- 해시 함수의 세 가지 성질: 결정적(deterministic), 되돌릴 수 없음(one-way),
  눈사태 효과(avalanche effect) — 입력이 한 글자만 달라져도 해시값이 완전히
  달라지는 걸 직접 확인
- `ipywidgets`로 이름/학번을 입력하면 전체 해시값과, 게시판에 실제로 쓸 짧은
  해시값(앞 10자리)을 보여주는 인터랙티브 조회기
- 이 방식이 막아주는 것(지나가다 보게 되는 노출)과 막아주지 **못하는** 것(내
  이름·학번을 정확히 아는 사람은 똑같은 해시를 계산할 수 있음)에 대한 설명
- (선택) 강사가 전체 명단을 "해시, 점수"만 남은 공개용 표로 한 번에 변환하는
  예시 코드

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/grade-hash-lookup/project.ipynb)
