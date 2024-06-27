# Buttons (버튼)

모든 링크, 레이블 또는 버튼 요소에 추가할 수 있는 기본 및 보조 버튼에 대한 전용 스타일을 제공합니다. 이는 전용 `call-to-action` 이 있는 문서나 랜딩 페이지에 특히 유용합니다.

## 설정 (mkdocs.yml)

```yaml
markdown_extensions:
  - attr_list
```

## 사용법

링크를 버튼으로 렌더링하려면 중괄호로 접두사를 붙이고 `.md-button` 클래스 선택기를 추가합니다. 버튼은 활성화된 경우 선택한 기본 색상(primary color)과 강조 색상(accent color)을 받습니다.

## 사용예시

### 버튼추가

```txt
[Subscribe to our newsletter](#){ .md-button }
```

[Subscribe to our newsletter](#){ .md-button }

### 아이콘 버튼 추가

> [아이콘검색](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/#search)

```txt
[Send :fontawesome-solid-paper-plane:](#){ .md-button }
```

[Send :fontawesome-solid-paper-plane:](#){ .md-button }

:hatched_chick:
