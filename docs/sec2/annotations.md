# Annotations (주석)

문서의 거의 모든 위치에 추가할 수 있는 작은 마커인 주석을 삽입하고, 클릭 또는 키보드 포커스 시 임의의 마크다운이 포함된 도구 설명을 펼칠 수 있는 기능입니다.

## 설정 (mkdocs.yml)

```yaml
markdown_extensions:
  - attr_list
  - md_in_html
  - pymdownx.superfences
```

### 아이콘 변경 (mkdocs.yml)

```yaml
theme:
  icon:
    annotation: material/arrow-right-circle
```

### 사용 가능한 아이콘 목록 (인기)

- :material-plus-circle: material/plus-circle
- :material-circle-medium: material/circle-medium
- :material-record-circle: material/record-circle
- :material-arrow-right-circle: material/arrow-right-circle
- :material-arrow-right-circle-outline: material/arrow-right-circle-outline
- :material-chevron-right-circle: material/chevron-right-circle
- :material-star-four-points-circle: material/star-four-points-circle
- :material-plus-circle-outline: material/plus-circle-outline

## 사용법

주석은 주석 클래스로 표시된 블록의 아무 곳에나 배치할 수 있는 마커와 마커가 포함된 블록 아래의 목록에 있는 콘텐츠로 구성됩니다.

## 사용예시

### 기본

```txt
Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
{ .annotate }

1. :man_raising_hand: I'm an annotation! I can contain `code`, **formatted
   text**, images, ... basically anything that can be expressed in Markdown.
```

Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
{ .annotate }

1. :man_raising_hand: I'm an annotation! I can contain `code`, **formatted
   text**, images, ... basically anything that can be expressed in Markdown.

### 중첩

주석 내에서, 수퍼펜스가 활성화되면 (pydownx.superfences) 주석 콘텐츠를 호스팅하는 목록 항목에 주석 클래스를 추가하고 이 과정을 반복하여 주석 내부에 주석을 중첩할 수 있습니다

```txt
Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
{ .annotate }

1.  :man_raising_hand: I'm an annotation! (1)
    { .annotate }

    1.  :woman_raising_hand: I'm an annotation as well!
```

Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
{ .annotate }

1.  :man_raising_hand: I'm an annotation! (1)
    { .annotate }

    1.  :woman_raising_hand: I'm an annotation as well!

### 훈계

훈계의 제목과 본문에도 인라인 블록의 작동 방식과 유사하게 유형 한정자 뒤에 주석 수정자를 추가하여 주석을 호스팅할 수 있습니다

```txt
!!! note annotate "Phasellus posuere in sem ut cursus (1)"

    Lorem ipsum dolor sit amet, (2) consectetur adipiscing elit. Nulla et
    euismod nulla. Curabitur feugiat, tortor non consequat finibus, justo
    purus auctor massa, nec semper lorem quam in massa.

1.  :man_raising_hand: I'm an annotation!
2.  :woman_raising_hand: I'm an annotation as well!
```

!!! note annotate "Phasellus posuere in sem ut cursus (1)"

    Lorem ipsum dolor sit amet, (2) consectetur adipiscing elit. Nulla et
    euismod nulla. Curabitur feugiat, tortor non consequat finibus, justo
    purus auctor massa, nec semper lorem quam in massa.

1.  :man_raising_hand: I'm an annotation!
2.  :woman_raising_hand: I'm an annotation as well!

### 탭

콘텐츠 탭은 주석 클래스를 전용 콘텐츠 탭의 블록에 추가하여 주석을 호스팅할 수 있습니다

```txt
=== "Tab 1"

    Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
    { .annotate }

    1.  :man_raising_hand: I'm an annotation!

=== "Tab 2"

    Phasellus posuere in sem ut cursus (1)
    { .annotate }

    1.  :woman_raising_hand: I'm an annotation as well!
```

=== "Tab 1"

    Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
    { .annotate }

    1.  :man_raising_hand: I'm an annotation!

=== "Tab 2"

    Phasellus posuere in sem ut cursus (1)
    { .annotate }

    1.  :woman_raising_hand: I'm an annotation as well!

### 기타 (html)

HTML의 마크다운 확장을 활용하여 임의의 요소를 주석 클래스가 있는 div로 감싸는 것은 언제나 가능합니다

```txt
<div class="annotate" markdown>

> Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.

</div>

1.  :man_raising_hand: I'm an annotation!
```

<div class="annotate" markdown>

> Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.

</div>

1.  :man_raising_hand: I'm an annotation!

## 참조

!!! warning "알려진 제약사항"

    데이터 테이블은 스크롤 가능한 요소이고 위치 지정이 매우 까다롭기 때문에
    현재 데이터 테이블에서는 주석이 작동하지 않습니다.
    이 문제는 향후 수정될 수 있습니다.
