# Quarto

## Quarto를 이용하여 리포트 작성하는법

> 해당 폴더에서 소스파일(SerieATIM_report_240222.ipynb)과 결과파일(SerieATIM_report_240222.html)을 통해 작업물과 결과물을 확인할 수 있다.

## Quarto가 뭐지? 그거 왜 씀?
Qaurto는 오픈 소스 문서작성 도구.<br>
Notebook 환경에서 작업한 내용을 리포트화 할 때, markdown 부분을 깔끔하게 할 수 있다. <br>
리포트에 코드를 접어서 포함할 수도 있다.



### 0. Quarto 설치<br>
https://quarto.org/docs/get-started/ 에서 설치를 먼저 해야 한다.

### 1. IDE 환경에서 리포트 작성 작업(데이터 시각화 작업)진행<br>
Jupyter Notebook, VS Code 뭐든 상관없음. 그런데 VS Code의 경우 plotly와 호환 문제가 생기는 경우가 있다고 합니다. 그 경우 Jupyter Notebook으로 작업하면 해결됨

### 2. Markdown 부분을 아래 포맷에 맞게 작성
```
---
title: "서울시 '전문과목미표시의원' 현황 분석"
format:
  html:
    code-fold: true
    code-block:
    echo: false
    callout-appearance: default
---



```
