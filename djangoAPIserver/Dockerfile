# aitube/Dockerfile

# python:3-slim 이미지 사용
FROM        python:3-slim

# 배포 서버 업데이트
RUN         apt -y -qq update & apt -y -qq dist-upgrade && apt -y -qq autoremove
# pip 업그레이드
RUN         pip install --upgrade pip
# ffmpeg 다운로드
RUN apt-get update
RUN apt-get install -y sudo
RUN sudo apt-get install -y ffmpeg
# /tmp 폴더에 requirements.txt 파일 복사
COPY        ./requirements.txt /tmp
# requirements.txt에 있는 라이브러리 설치
RUN         pip install -r /tmp/requirements.txt

# 현재 프로젝트를 / 폴더에 복사
COPY        . /src/
# Docker 이미지 실행시 경로
WORKDIR     /src/


EXPOSE 80

CMD ["python3", "manage.py", "runserver", "0:80"]