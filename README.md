# README

## 설치

1. Dockerfile 작성
2. Dockerfile 빌드
3. Docker Compose 를 통한 실행
4. Mkdocs build

### 1. Dockerfile 작성

```Dockerfile
# 도커파일 생성 후 공식 이미지를 기반으로 플러그인을 추가한다.
FROM squidfunk/mkdocs-material
RUN pip install mkdocs-macros-plugin
RUN pip install mkdocs-glightbox
```

### 2. Dockerfile 빌드

```bash
# docker build: Docker 이미지를 빌드하는 명령입니다.
# -t squidfunk/mkdocs-material: 빌드된 이미지에 squidfunk/mkdocs-material이라는 태그를 부여합니다. 이 태그는 이미지를 참조할 때 사용됩니다.
# .: Dockerfile이 있는 디렉토리의 경로를 나타냅니다. 여기서는 현재 디렉토리를 나타냅니다.
docker build -t squidfunk/mkdocs-material .
```

### 3. Docker Compose 를 통한 실행

`mkdocs.yml` 을 파일을 생성하고 아래와 같이 작성한다.

```yaml
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

현재 작업 디렉토리를 사용하여 squidfunk/mkdocs-material 이미지를 기반으로 하는 컨테이너를 실행하고, 이 컨테이너를 호스트의 8000번 포트에 연결

### 3. Mkdocs start

Windows 의 경우 아래 커맨드를 cmd 가 아닌 `powershell` 에서 실행해야 한다.
cmd 또는 gitbash 등으로 실행하면 `Error: Config file 'mkdocs.yml' does not exist.` 와 문구를 볼수 있는데, `powershell` 에서 실행하면 정상적으로 실행된다.

```bash
# docker run: Docker 컨테이너를 시작하는 명령입니다.
# --rm: 컨테이너가 종료되면 자동으로 삭제하도록 설정합니다.
# -it: 컨테이너와 상호작용하는 터미널을 엽니다.
# -p 8000:8000: 호스트의 8000번 포트를 컨테이너의 8000번 포트에 연결합니다. 이렇게 하면 호스트 시스템에서 http://localhost:8000을 통해 컨테이너에 접근할 수 있습니다.
# -v ${PWD}:/docs: 현재 작업 디렉토리($PWD)를 컨테이너의 /docs 디렉토리에 마운트합니다. 이렇게 하면 컨테이너 내부에서 이 디렉토리의 파일을 읽고 쓸 수 있습니다.
# squidfunk/mkdocs-material: 실행할 Docker 이미지의 이름입니다. 이 이미지는 MkDocs와 Material 테마를 포함하고 있습니다.
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
```

### 5. Mkdocs build

```bash
# 아래 명령이 실행되면 site 폴더가 생성되며, 이 폴더에 정적 파일이 생성된다.
# build.sh 참조 / mac 에서는 그냥 해당 스크립트를 실행하면 됨
`docker run --rm -it -v ${PWD}:/docs squidfunk/mkdocs-material build`
```

## 참조링크

> 설정은 mkdocs 를 상속받은 `mkdocs-material` 을 통해 작업을 진행하면 된다

- [mkdocs-material : getting-started](https://squidfunk.github.io/mkdocs-material/getting-started/)
- [mkdocs-material : setup](https://squidfunk.github.io/mkdocs-material/setup/)
- [Working docker-compose.yml file for mkdocs-material?](https://www.reddit.com/r/selfhosted/comments/10okzo6/working_dockercomposeyml_file_for_mkdocsmaterial/)
- [PowerShell : releases](https://github.com/PowerShell/PowerShell/releases)
- [mkdocs : configuration](https://www.mkdocs.org/user-guide/configuration/)
