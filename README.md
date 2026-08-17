# shopping-listapp

쇼핑 리스트 앱

`index.html` 파일 하나로 동작하는 HTML/CSS/JS 쇼핑 리스트 앱입니다. 데이터는 [Supabase](https://supabase.com) 데이터베이스(`shopping_items` 테이블)에 저장되어, 어떤 기기/브라우저에서 열어도 동일한 리스트를 볼 수 있습니다.

## 기능 요구사항

- **항목 추가**: 입력창에 물건 이름을 입력하고 "추가" 버튼 클릭 또는 Enter 키로 리스트에 추가한다.
- **항목 완료 체크**: 각 항목 왼쪽의 원형 체크박스를 클릭해 완료 여부를 토글한다. 완료된 항목은 취소선과 흐린 색으로 표시된다.
- **항목 삭제**: 각 항목 오른쪽의 × 버튼으로 개별 항목을 삭제한다.
- **완료 항목 일괄 삭제**: "완료 항목 지우기" 버튼으로 체크된 항목을 한 번에 제거한다.
- **항목 개수 표시**: 상단에 전체 항목 수와 완료된 항목 수를 `N개 항목 (완료 M개)` 형식으로 표시한다.
- **빈 상태 표시**: 항목이 하나도 없을 때 "리스트가 비어 있습니다" 안내 문구를 표시한다.
- **데이터 저장**: 입력한 항목은 Supabase의 `shopping_items` 테이블에 저장되어, 브라우저를 새로고침하거나 다른 기기에서 열어도 유지된다.

## 비기능 요구사항

- **반응형 레이아웃**: 최대 너비 480px 기준으로 모바일/데스크톱 모두에서 자연스럽게 보이도록 한다.
- **다크 모드 지원**: 시스템 설정(`prefers-color-scheme: dark`)에 따라 자동으로 다크 테마가 적용된다.
- **외부 의존성**: 데이터베이스 연동을 위해 `@supabase/supabase-js`를 CDN으로 불러온다. 그 외 프레임워크나 빌드 도구는 사용하지 않는다.

## 데이터베이스 (Supabase)

`shopping_items` 테이블 구조:

| 컬럼         | 타입          | 설명                     |
| ------------ | ------------- | ------------------------ |
| `id`         | `uuid`        | 기본키, 자동 생성        |
| `text`       | `text`        | 항목 이름                |
| `checked`    | `boolean`     | 완료 여부 (기본 `false`) |
| `created_at` | `timestamptz` | 생성 시각 (기본 `now()`) |

Row Level Security가 활성화되어 있으며, `anon` 역할에 대해 select/insert/update/delete를 모두 허용하는 정책이 설정되어 있습니다.

## 실행 방법

`index.html` 파일을 브라우저에서 열면 바로 사용할 수 있습니다.

## GitHub Pages 배포

이 저장소는 GitHub Pages로 배포할 수 있습니다. 별도 빌드 과정이 없는 정적 파일이므로 브랜치 배포 방식을 사용합니다.

1. 저장소가 비공개(private)라면 GitHub Pages를 사용하기 위해 공개(public)로 전환합니다. (GitHub Free 플랜은 비공개 저장소에서 Pages를 지원하지 않습니다.)
2. **Settings → Pages** 로 이동합니다.
3. **Build and deployment → Source** 를 `Deploy from a branch` 로 설정합니다.
4. **Branch** 를 `main` / `/ (root)` 로 설정하고 저장합니다.
5. 잠시 후 `https://kasius63.github.io/shopping-listapp/` 주소에서 앱이 배포됩니다.

`main` 브랜치에 새로 push할 때마다 GitHub Pages가 자동으로 최신 내용을 반영합니다.
