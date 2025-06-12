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

### 2. 가장 상단의 셀은 리포트의 제목 및 형식 등을 할당하는 셀 (아래 YAML양식에 맞게 작성)
아래의 YAML 양식은 임의 설정 된 값. <br>
다음 링크 내용을 참고해서 작성 가능 : https://quarto.org/docs/websites/website-listings.html#yaml-listing-content
```
---
title: 제목
author: 작성자 명
date: 발간 일자
categories: [Report, personal project] # 카테고리는 리스트 형태로 추가
description: "섬네일에서 보여질 간단 설명"

format:
  html:
    self-contained: true
    theme: Flatly
    page-layout: full
    fontsize: 1.0em
    linestretch: 1.5
    toc: true
    toc-depth: 4
    toc-expand: true
    echo: false
    callout-appearance: default
jupyter: python3
---
```
다음은 기본적인 제목과 포맷정도만 지정하는 basic format
```
---
title: "리포트 제목"
format:
  html:
    code-fold: true
    code-block:
    echo: false
    callout-appearance: default
---

```

### 3. 코드 블럭을 아래 형식에 맞게 작성
YAML로 설정을 마쳤으면 Markdown을 아래 포맷에 맞게 작성해서 리포트의 전반적인 톤을 맞출 수 있다.<br>
사용할 수 있는 옵션에는 callout-note, callout-warning, callout-tip 등이 있다.
```
:::{.callout-note icon=false title="분석 목적"}
- 분석 목적 작성

::: 

:::{.callout-note icon=false title="데이터 기준"}
- 내용 작성
- 내용 작성
:::

:::{.callout-tip icon=false title="Summary"} 
>- **첫번째 Summary**
>    - 세부내용 1
>    - 세부내용 2

>- **두번째 Summary**
>    - 세부내용 1
>    - 세부내용 2
:::
```

### 4. 이후 시각화는 동일하게 진행
단, 노트북의 모든 출력이 html에 반영되기 때문에, DataFrame을 조회하는 셀 등 작업 시 필요하지만 리포트에 노출되지 않아야 하는 셀 들에 대해서는 주의가 필요하다. 또한 warning message도 출력 되기 때문에 warning message도 나타나지 않게 설정이 필요하다. 그리고 dw에 연결해서 작업하는 경우, 해당 내용도 전부 html에 포함되기 때문에 랜더링 전에 Clear cell output을 해야한다.
```
import warnings
warnings.filterwarnings("ignore")
```

### 5. 작업이 완료되면 랜더링을 통해 html로 변환 가능하다
어떻게 했었지??


### 추가 참고 사항
VS code에서 Plotly 사용 시 호환 문제가 발생하는 경우 renderer를 아래와 같이 변경하면 해결이 가능하다고 합니다. 
(jupyterlab에서는 필요하지 않다고 나오는데, 저는 가끔 랜더링 안될때 그냥 넣어보긴합니다…)
```
import plotly.io as pio
pio.renderers.default = "plotly_mimetype+notebook_connected"
```
