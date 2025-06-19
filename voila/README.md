# Voila


## About Voila
Jupyter Notebook을 활용해서 간단하게 대시보드를 띄울 수 있다.<br>
그 외에 다른 용도로도 쓰일 수 있는 것 같으나, 데이터 분석가로서 위의 목적을 위해 사용한다.
R Shiny를 생각하면 될 것 같다.<br>
https://voila.readthedocs.io/en/stable/index.html


## 1. 설치
일단 설치를 해야한다. <br>
다른 모듈과 마찬가지로 pip install을 통해서 설치를 하는데, 
나는 0.4.0버전을 설치했다. (좀 지난 얘기지만, 같이 일하시던 분께서 그 이후 버전은 로딩이 됐다 안됐다 한다고 하셔서 0.4.0으로 고정했는데, 이젠 많이 나아지지 않았을까..?)<br>
`pip install voila==0.4.0`으로 설치했다.
<br><br>
아, 참고로 나는 가상 환경을 세팅해서 사용하고 있기 때문에 경로를 신경써서 설치해야한다.(이건 파이썬 모듈을 설치할 때 항상 고려해야할 요소)

## 1-1. ipynb로 작업하고 저장하기
일단 ipynb파일이 있어야 이 파일을 대시보드화 할 수 있다.
내가 만들려고 하는 작업물을 열심히 만들어서 ipynb파일로 저장을 하자.
그리고 그 경로를 잘 알아두면 되겠다.

## 2. 파일을 웹에 띄우기
그냥 작업 파일을 `voila file_name.ipynb`를 이용해서 띄우면 된다.<br>
소소한 팁이지만 파일명에 공백이 있는 경우, 따옴표로 묶어주면 된다. `voila "file name.ipynb"` <br><br>
그 외 명령어<br>
`voila file_name.ipybn --theme=dark` 다크 모드로 열기 <br>
`voila file_name.ipybn --no-browser` 서버에 띄우긴 하는데 웹은 열지않기 <br>
`voila file_name.ipybn --port=8887` 다른 포트에다가 띄우기 <br>



### 추가: 그런데 이건 Jupyter Notebook에서 사용할 때 더 유용하게 사용된다.
이거 더 작성 그리고 위에 내용 잘 정리 필요. 그리고 나서 마무리할거임
그리고 파일을 하나 만들어야함.> voila 띄워볼 파일 intractive chart 지원 되는거.
https://github.com/voila-dashboards/voila?tab=readme-ov-file
