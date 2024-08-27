# Content tabs (탭)

다른 탭 아래에 대체 콘텐츠를 그룹화하는 것이 바람직할 때가 있습니다. 탭을 사용하여 코드 블록 및 기타 콘텐츠를 그룹화할 수 있습니다

## 설정 (mkdocs.yml)

```yaml
markdown_extensions:
  - pymdownx.superfences
  - pymdownx.tabbed:
      alternate_style: true
```

> 앵커 가독성 증가 설정

```yaml
markdown_extensions:
  - pymdownx.tabbed:
      slugify: !!python/object/apply:pymdownx.slugs.slugify
        kwds:
          case: lower
```

> 이 기능을 활성화하면 전체 문서 사이트의 모든 콘텐츠 탭이 연결되고 사용자가 탭을 클릭하면 동일한 레이블로 전환됩니다.

```yaml
theme:
  features:
    - content.tabs.link
```
