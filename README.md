# 나울 (Mellow Touch)

서울·경기·인천 출장 마사지·홈타이·안마 안내. **정적 사이트**(빌드 과정 없음).

```
public/            구워진 HTML 3,242장
  ├ index.html         첫 화면
  ├ region/            시·도
  ├ {구}/              행정구 83곳
  ├ {구}/{동}/         대표 행정동 785곳
  ├ shop/{자리}/       업소 2,355곳
  ├ kind/{업종}/       업종 10갈래
  ├ price/ guide/ about/
  ├ sitemap.xml robots.txt favicon.svg s.css
wrangler.toml      클라우드플레어 설정
```

## 클라우드플레어 설정값

**Pages** 로 연결한다(Worker 아님).

| 칸 | 값 |
|---|---|
| 프로덕션 분기 | `main` |
| 프레임워크 미리 설정 | `없음` |
| **빌드 명령** | **비워 둔다** |
| **빌드 출력 디렉터리** | `public` |

★`wrangler.toml` 의 `pages_build_output_dir` 가 없으면 Pages 가
  이 파일을 Workers 설정으로 읽고 빌드를 거부한다.

## 고치는 법

내용은 손으로 고치지 않는다. 생성기(`/root/mellow/gen/`)를 고치고 다시 굽는다.

```
python3 regions.py          지역 자료
python3 shops.py            업소 자료
MT_OUT=…/public python3 build.py   전체 생성
```

## 적어 두는 원칙

- 게재된 업소 정보는 **안내를 위한 예시**이며 실제 영업장과 무관하다.
  그래서 `LocalBusiness` 스키마를 쓰지 않고 `Service` 로 적는다.
- 길 주소·별점·후기를 지어내지 않는다. 자리는 **행정동까지만** 적는다.
- 전화번호는 대표 번호 하나뿐이다.
- 순위·등수를 매기지 않는다.
