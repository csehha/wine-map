# WSET L2 포도 품종 지도

WSET Level 2 시험에 나오는 주요 포도 품종과 대표 산지를 세계 지도 위에 보여주는 단일 페이지 웹앱입니다.

## 기능

- 품종을 고르면 해당 산지가 지도에 표시되고, 바디·산도·탄닌 같은 특징과 지역별 스타일 설명이 나옵니다.
- 화이트 / 레드 필터, 지역 이름이나 점을 눌러 선택하기
- 확대·축소 버튼과 두 손가락 핀치로 지도 이동
- 라이트/다크 모드 자동 대응
- 홈 화면에 추가해 앱처럼 쓸 수 있고, Service Worker(`sw.js`)가 한 번 받은 리소스를 캐시해 오프라인에서도 열립니다.

## 구성

| 파일 | 설명 |
| --- | --- |
| `index.html` | 화면, 품종·산지 데이터, 지도 렌더링 코드 전체 |
| `sw.js` | 캐시 우선 Service Worker (캐시 이름 `wset-map-v3`) |

지도는 [D3](https://d3js.org/)와 [TopoJSON](https://github.com/topojson/topojson)으로 그리며, 라이브러리와 지도 데이터는 CDN에서 불러옵니다.

## 실행

빌드 과정이 없습니다. Service Worker는 `file://`에서 동작하지 않으므로 로컬 서버로 띄웁니다.

```bash
python3 -m http.server 8000
```

그다음 http://localhost:8000 을 엽니다. GitHub Pages 같은 정적 호스팅에 그대로 올려도 됩니다.

## 업데이트할 때

`index.html`을 고친 뒤에는 `sw.js`의 캐시 이름(`wset-map-v3`)의 버전을 올려야 기존 사용자에게 새 버전이 반영됩니다.
