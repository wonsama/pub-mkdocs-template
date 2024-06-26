# 설치 및 실행

> 빠른 시작을 위해 `Docker` 를 사용하여 설치하는 방법을 설명 드립니다.. `pip` 또는 `git` 을 사용하여 설치하는 방법은 [mkdocs-material : getting-started](https://squidfunk.github.io/mkdocs-material/getting-started/){:target="\_blank"}를 참조 하시길 바랍니다.

## 기본내용 작성하기

> 최소 구성으로 `mkdocs` 를 실행하기 위한 폴더 및 파일을 아래와 같이 생성합니다.

### 폴더 및 파일 구조

```tree
mkdocs
L docs
__L index.md
L mkdocs.yml
L Dockerfile
L docker-compose.yml
```

### index.md

```markdown
# Hello, MkDocs!
```

### mkdocs.yml

```yaml
site_name: My Docs
nav:
  - Home: index.md
```

## Dockerfile 만들기

기본 `squidfunk/mkdocs-material` 이미지에 포함 된 플러그인

- mkdocs-minify-plugin
- mkdocs-redirects

추가적인 플러그인을 설치하기 위해서는 아래와 같이 `Dockerfile` 을 작성하여 기본 이미지에 추가적으로 진행할 작업 정보를 추가합니다.

```Dockerfile
FROM squidfunk/mkdocs-material
RUN pip install mkdocs-macros-plugin
RUN pip install mkdocs-glightbox
```

### Docker 이미지 만들기

```bash
# 아래명령어를 실행하여 Docker 이미지를 생성한다.
docker build -t squidfunk/mkdocs-material .
```

### Docker 이미지 실행

```bash
# 아래명령어를 실행하여 `mkdocs` 를 실행한다.
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
```

## Docker Compose 로 실행

### yaml 파일 작성

```yaml
# docker-compose.yaml
version: '3'

services:
  mkdocs:
    container_name: mkdocs
    image: squidfunk/mkdocs-material
    restart: always
    ports:
      - '8000:8000'
    volumes:
      - '${PWD}:/docs'
```

### docker compose 실행

```bash
# 아래 명령어를 실행하여 `mkdocs` 를 실행한다.
docker compose up -d
```

## 접속확인

[http://localhost:8000](http://localhost:8000){:target="\_blank"} 에 접속하여 `Hello, MkDocs!` 가 표시되는지 확인합니다.

## 참조링크

- [mkdocs-material : getting-started](https://squidfunk.github.io/mkdocs-material/getting-started/){:target="\_blank"}
