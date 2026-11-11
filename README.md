# Exchange Archive 2025

University of Bristol 에서의 기억을 아카이브한 개인 페이지입니다. 

**Live** → https://makadamianut.github.io/Atlas2025/


## 페이지

| 페이지 | 보여주는 것 |
|---|---|
| [Big Wheel](pages/big-wheel.html) | 런던아이에서 모티프를 얻은 관람차입니다. 휠이 돌며 다녀간 도시들이 하나씩 떠오르고, 브리스톨에 닿는 순간 색이 바뀝니다. |
| [Itinerary](pages/itinerary.html) | 여행을 예약하고 메일함에 itinerary가 도착하던 순간이 가장 설렜습니다. 그 단어만으로도 마음이 부풀던 기억을 담아, 한 학기의 여정을 지구본 위에 이었습니다. |
| [London](pages/london.html) | 하루에도 몇 번씩 구름이 몰려오고 소나기가 지나가던 도시였습니다. 커서로 우산을 움직여, 갑자기 쏟아지는 비로부터 근위병을 지켜 주세요. |
| [Atlas](pages/atlas.html) | 머문 곳은 모두 저마다의 의미로 남았습니다. 그중 가장 오래 기억하고 싶은 브리스톨 해협, 트롬쇠, 몽블랑, 레이콕을 지도로 조판했습니다. |
| [Prism](pages/prism.html) | 햇볕이 닿는 순간마다 장면이 무지갯빛으로 번지는 것을 느꼈습니다. 여행 중 만난 그 황홀한 빛깔의 사진들을 프리즘 하나에 모았습니다. |
| [Paper Weight](pages/paperweight.html) | 리버티 백화점에서 한참을 들여다보던 존 데리안의 문진은, 끝내 사지 못하고 영국에 두고 온 물건입니다. 볼록렌즈로 그 질감을 되살려, 디지털 공간에서나마 나만의 문진을 갖기로 했습니다. |
| [Underground](pages/underground.html) | 선명한 노선색, 재치 있는 역 이름까지, 런던에서 지하철의 매력에 다시 빠졌습니다. 노선도를 알파벳으로 잘라내어 UNDERGROUND를 완성했습니다. |
| [Lakes](pages/lakes.html) | 키프로스의 염호, 샤모니의 인공호, 블레드와 레만까지, QGIS로 호수의 윤곽을 추출해 담았습니다. 커서를 올리면 홀로그램처럼 빛납니다. |


## 데이터 흐름

```
QGIS 3.40에서 경로(LineString)·정류지(Point 22곳, 10개국) 작성
  → GeoJSON(CRS84)으로 내보내기          data/route.geojson, data/stops.geojson
  → Mapbox GL JS로 지구본 위에 표시
  → Turf.js로 슬라이더 위치만큼 경로를 잘라 그리고(lineSliceAlong),
    정류지를 경로에 스냅해(nearestPointOnLine) 지나간 곳을 켬
```

`data/*.qmd`는 QGIS 레이어 스타일 파일입니다. Atlas의 지도들은 QGIS에서 각 지역에 맞는 투영법(EPSG:3035, 27700, 3413)으로 제작했습니다.

## 기술

HTML · CSS · JavaScript, [GSAP](https://gsap.com/), [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/), [Turf.js](https://turfjs.org/), QGIS, GitHub Pages

## 구조

```
index.html        허브
pages/            각 페이지
assets/img/       사진·지도 (WebP, 긴 변 2000px 이하, EXIF 제거)
assets/thumb/     허브 썸네일
data/             GeoJSON, QGIS 스타일
docs/screenshots/ README용 스크린샷
```

## 로컬에서 보기

Itinerary가 `fetch`로 GeoJSON을 읽기 때문에 파일을 더블클릭(file://)하면 지도가 비어 보입니다. 간단한 서버로 여세요.

```bash
python -m http.server 8000
# http://localhost:8000
```

Itinerary의 Mapbox 토큰은 공개용(pk.) 토큰이며, Mapbox 계정에서 배포 도메인으로 사용 URL을 제한해 두었습니다. 다른 도메인에서 띄우려면 자신의 토큰으로 바꿔야 합니다.

---

Seohui Lim · 기획, 디자인, 개발, 배포
