# Voila


## About Voila
내가 작업한 ipynb파일을 간단하게 대시보드 형태로 웹에 띄울 수 있는 도구이다.(당연히 py파일도 지원하지만, 주로 Jupyter Notebook기반 .ipynb파일에 특화되어 있다.)<br>
그 외에 다른 용도로도 쓰일 수 있는 것 같으나, 데이터 분석가로서 빠른 대시보드 공유의 목적을 위해 사용한다.<br>
R Shiny를 생각하면 될 것 같다.<br>
[공식문서 바로가기](https://voila.readthedocs.io/en/stable/index.html)


## 1. 설치
일단 설치를 해야한다. <br>
mamba나 conda로 설치해도 당연히 되지만, 나는 pip install을 통해서 설치를 했다.<br> 
나는 0.4.0버전을 설치했다. (좀 지난 얘기지만, 같이 일하시던 분께서 0.4.0 이후 버전은 로딩이 됐다 안됐다 한다고 하셔서 0.4.0으로 고정했는데, 이젠 많이 나아지지 않았을까..?)<br>
`pip install voila==0.4.0`
<br><br>
아, 참고로 나는 가상 환경을 세팅해서 사용하고 있기 때문에 경로를 신경써서 설치해야한다.(이건 파이썬 모듈을 설치할 때 항상 고려해야할 요소)

## 1-1. ipynb로 작업하고 저장하기
일단 ipynb파일이 있어야 이 파일을 대시보드화 할 수 있다.<br>
내가 만들려고 하는 작업물을 생성하고 ipynb파일로 저장을 하자.<br>
그리고 그 경로를 잘 알아두면 되겠다.

## 2. Voila를 이용해 파일을 웹에 띄우기
그냥 작업 파일을 아래와 같이 웹에 띄울 수 있다.<br> 
`voila file_name.ipynb`<br>
소소한 팁이지만 파일명에 공백이 있는 경우, 아래 처럼 따옴표로 묶어주면 된다. <br>
`voila "file name.ipynb"` <br><br>
그 외 명령어<br>
`voila file_name.ipybn --theme=dark` 다크 모드로 열기 <br>
`voila file_name.ipybn --no-browser` 서버에 띄우긴 하는데 웹은 열지않기 <br>
`voila file_name.ipybn --port=8887` 다른 포트에다가 띄우기 <br>
`voila file_name.ipybn --strip_sources=False` 노트북 내 코드 셀도 모두 보여주기 (default는 코드 숨김)<br>
`voila file_name.ipybn --host=0.0.0.0` 외부 접속 허용 (같은 네트워크 공유 시 필요) <br>

## 3. 웹 대시보드를 공유하기
사실 이 작업물을 웹에 띄운 이유는 다른 사람과 공유하기 위해서이다.<br><br>
### 같은 네트워크 내 공유
같은 네트워크 환경의 사람들에게는 내 ip와 port를 공유해주면 된다. 같은 와이파이 환경이나 사내 네트워크에 있으면 아마 될 것 같다. <br>
중요한 것은, 위에서 언급한 대로 서버에 띄울때 `--host=0.0.0.0` 옵션으로 실행을 해야한다. <br>
그리고나서, 대시보드를 플로팅 한 서버 컴퓨터의 IP주소와 포트번호를 알려준다. (cmd에서 ipconfig로 명령어로 확인 가능) <br>
그러면 같은 네트워크 환경에 있는 누구든 아래 경로로 접속하면 된다.(인터넷 창에서 아래 주소를 입력)<br>
`http://<ip주소>:<포트번호>`<br>
(그런데 이게 원활하게 공유가 안되면, 네트워크 방화벽이나 OS방화벽 등에서 설정이 필요함)<br><br>
*** +++ 추가내용<br>
`--host=0.0.0.0`이 동작 안할 때 대처법을 추가함<br>
위의 명령어 대신 `--Voila.ip=0.0.0.0`으로 명령어가 수정됨.<br>
터미널에서 `voila --help-all`명령어 참고.

### 외부 네트워크(인터넷)에서 공유
이건 나도 해 본 적은 없지만,<br>
같은 네트워크가 아니라 다른 환경의 사람과 공유하기 위해서는 ngrok 같은 터널링 도구를 사용한다. [ngrok 다운로드](https://ngrok.com/downloads/windows) <br>
그 외에도 다른 방법 및 자세한 deploy방법은 공식문서 참고. (https://voila.readthedocs.io/en/stable/deploy.html#)


## 추가: Voila는 Jupyter Notebook 환경에서 더 간단하게 사용할 수 있다.
Voila는 Jupyter Notebook 확장(extension)으로도 동작한다<br>
기본적으로 Jupyter Notebook을 처음 실행하면 Voila 아이콘 메뉴가 없는데, <br>
jupyter notebook을 실행할 때, 아래와 같은 옵션을 통해 Voila 아이콘 메뉴를 추가할 수 있다.<br>
`jupyter notebook --VoilaConfiguration.enable_nbextensions=True` <br>
이렇게 jupyter notebook을 실행하면 오른쪽 상단에 'Render with Voila'아이콘이 생긴다.![image](https://github.com/user-attachments/assets/5ac54295-91f0-4483-8495-e10d5783ad14) <br>
이 버튼을 클릭하면 대시보드를 확인할 수 있다.<br><br>
또는 터미널에 `Voila --enable_nbextensions=True`를 입력하면 jupyter notebook와 유사한 폴더 구조 인터페이스가 뜨는데 여기서 ipybn파일을 실행하면 대시보드를 띄울 수 있다.
<br><br><br>

## 실습 파일
해당 폴더의 voila_sample.ipynb파일은 voila를 이용해 작업물을 웹에 띄우기는 것을 해볼 수 있는 파일이다. <br>
interactive chart를 이리저리 만져볼 수 있다.
<br><br>
voila의 자세한 설명은 아래 깃헙에서 확인가능하다.
https://github.com/voila-dashboards/voila?tab=readme-ov-file
