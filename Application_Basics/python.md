# Python
### python3 설치
- CentOS 7 은 기본적으로 Python 2.x를 지원하므로 Python3을 쓰려면 설치해줘야됨
  ```bash
  # 버전 확인
  $ python -V
  Python 2.7.5

  $ yum -y install python3
  ```
- 파이썬 패키지 관리자 pip 설치
  ```
  $ yum -y install python3-pip

  $ pip3 -V
  ```
- CentOs7에서 python의 기본 버전을 python2에서 python3으로 변경하는 방법
  - `alternative` 는 RedHat(CentOS)계열의 리눅스 시스템에서 사용되는 명령어로, 여러 버전의 소프트웨어를 시스템에 설치하고, 그 중에서 `기본 버전`을 선택할 수 있게 하는 명령어
  - alternatives에 python2가 등록이 되어있을 경우
    ```bash
    # 등록이 되어 있는 경우
    # Python 버전 목록이 표시되며, 원하는 버전을 선택하면 됨
    $ alternatives --config python
    
    # 설정된 버전 확인
    $ python -V
    ```
  - alternatives에 python과 관련하여 아무것도 설치되어 있지 않은 경우
    ```bash
    # 아래의 명령어를 실행해도 아무것도 뜨지 않음
    $ alternatives --config python

    # python3 등록
    $ which python3
    /usr/bin/python3

    # /usr/bin/python을 python이라는 명령어로 등록하고, /usr/bin/python3으로 대체함
    # usage: alternatives --install <link> <name> <path> <priority>
    $ alternatives --install /usr/bin/python python /usr/bin/python3 1

    $ python -V
    Python 3.6.8
    ```
  - pip로 flask 설치해보기
    ```
    $ pip3 install flask
    $ pip3 show flask
    Name: Flask
    Version: 2.0.3
    Summary: A simple framework for building complex web applications.
    Home-page: https://palletsprojects.com/p/flask
    Author: Armin Ronacher
    Author-email: armin.ronacher@active-4.com
    License: BSD-3-Clause
    Location: /usr/local/lib64/python3.6/site-packages
    Requires: click, itsdangerous, Jinja2, Werkzeug
    ```
  - 여러 개의 패키지 설치 (requirements.txt 사용)
    ```
    # 방법 1)
    $ pip3 install flask
    $ pip3 install jinja2
    $ pip3 install markupsafe
    $ pip3 install Werkzeug
    ...

    # 방법 2)
    $ pip install flask jinja2 markupsafe Werkzeug

    # 방법 3)
    $ vi requirements.txt
    Flask
    Jinja2
    Markupsafe
    Werkzeug
    # 구체적인 버전을 지정해서 설치하는 방법
    Flask==0.10.1
    ...

    $ pip install -r requirements.txt
    ```
  - 패키지 업그레이드 및 삭제
    ```
    $ pip install flask --upgrade

    $ pip uninstall flask -y
    ```
