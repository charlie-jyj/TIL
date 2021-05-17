# vue 04



## Deploy

> 배포



https://www.notion.so/Deploy-e18d88c2f3ed4be8bb789e60d26ac871



### 준비사항

- 오류가 없고 완성된 프로젝트
- 의존성 저장
- 원격저장소 업로드
- cloud 9 
  - 원격 컴퓨터 접속을 위한 인터페이스
  - 컴퓨터를 하나 생성하는 것
  - 클라우드 9 을 통해 접속하면 EC2 가 켜진다



### AWS

#### cloud 9

코드 작성을 위한 인터페이스



#### EC2

클라우드 컴퓨터 



#### 프로젝트 생성

- 기본설정

- 보안그룹

  - 인바운드
  - EC2 서비스 인스턴스에 도달할 수 있도록 수신 트래픽 제어
  - 들어오는 규칙
    - 클라우드 컴퓨터에 접근하기 위한 프로토콜
    - 접근 가능한 포트 설정 (80)
    - 0.0.0.0 은 모든 IP 가 접근 할 수 있음을 의미

- home ubuntu 에서 진행

- pyenv

  - 파이썬 설치가 필요하다
  - pyenv 라이브러리
  - 리눅스에서 관리를 편하게 하기 위해서
  - https://github.com/pyenv/pyenv

- venv 설정

  - 가상환경
  - source venv/bin/activate
  - pip install -r requirements.txt

- collectstatic

- nginx

  - ```
    server_name *.compute.amazonaws.com;
    
    location / {
    	uwsgi_pass unix:///home/ubuntu/{crud}/tmp/{crud}.sock;
    	include uwsgi_params;
    }
    
    location /static/ {
    	alias /home/ubuntu/{crud}/staticfiles/;
    }
    ```

  - django가 run server 를 하면 developer 용 작은 서버가 동작 

  - web server 가 동작하며 django applictation 이 동작

  - AWS 이용을 위해서는 nginx 를 통해 webserver 대체

  - 중재하는 uWSGI

  - nginx 가 url 요청을 받아 분기 처리 

    - root 주소는 django 로
    - static 주소는 static file 에 접근 하도록 중개

  - uwsgi 설치

    - 웹서버와의 중개
    - https://uwsgi-docs.readthedocs.io/en/latest/

  - 배포 완료 후 

    - 도메인 구매
    - HTTPS 인증서 발급
    - DEBUG = False





### Netlify

- vue 로 만든 프로젝트 배포하기
- 정적 호스팅
- https://app.netlify.com/teams/charlie-jyj/overview

https://clever-kirch-f81bae.netlify.app/







