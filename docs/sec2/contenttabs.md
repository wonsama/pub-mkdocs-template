# Content tabs (탭)

다른 탭 아래에 대체 콘텐츠를 그룹화하는 것이 바람직할 때가 있습니다. 탭을 사용하여 코드 블록 및 기타 콘텐츠를 그룹화할 수 있습니다

## 설정 (mkdocs.yml)

```yaml
markdown_extensions:
  - pymdownx.superfences
  - pymdownx.tabbed:
      alternate_style: true
```

```yaml
theme:
  features:
    - content.tabs.link
```
