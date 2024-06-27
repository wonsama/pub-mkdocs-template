# Code Blocks

코드 블록에 대한 구문 강조를 설정하는 다양한 방법을 제공하며, 빌드 시간 동안 Pygments(python syntax highlighter)를 사용하거나 런타임 중에 JavaScript 구문 강조 표시기를 사용할 수 있습니다

## 설정 (mkdocs.yml)

```yaml
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences
```

## Code 복사기능 설정 (mkdocs.yml)

코드 블록 우측에 :material-content-copy: (복사 버튼) 을 추가하여 코드를 클립보드에 복사할 수 있습니다.

```yaml
theme:
  features:
    - content.code.copy
```

코드 주석은 코드 블록의 언어로 블록 및 인라인 주석에 숫자 마커를 추가하여 코드 블록의 특정 섹션에 임의의 콘텐츠를 첨부할 수 있는 편안하고 친숙한 방법을 제공합니다

## Code 주석 설정 (mkdocs.yml)

```yaml
theme:
  features:
    - content.code.annotate
```

## 사용방법

코드 블록은 백틱 3개가 포함된 별도의 두 줄로 묶어야 합니다. 이러한 블록에 구문 강조 표시를 추가하려면 여는 블록 바로 뒤에 언어 쇼트코드를 추가하세요. ([지원목록:octicons-link-external-16:](https://pygments.org/docs/lexers/){:target="\_blank"})

## 사용예시

### 기본

````txt
```py
import tensorflow as tf
```
````

```py
import tensorflow as tf
```

### 제목 추가

````txt title="제목을 추가한 코드블록"
```py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```
````

```py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

### 주석 추가

````txt title="주석을 추가한 코드블록"
``` yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.
````

```yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, **formatted
    text**, images, ... basically anything that can be written in Markdown.

```yaml
# (1)!
```

### 특정라인 강조

언어 단축코드 바로 뒤에 있는 hl_lines 인수에 줄 번호를 전달하여 특정 줄을 강조 표시할 수 있습니다. 줄 수는 라인넘버의 일부로 지정된 시작 줄 번호와 관계없이 1부터 시작한다는 점에 유의하세요

````txt title="특정라인 강조"
``` py hl_lines="2 3"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```
````

```py hl_lines="2 3"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

## 참조

- [사용자화 : 색상 변경 등](https://squidfunk.github.io/mkdocs-material/reference/code-blocks/#customization){:target="\_blank"}
