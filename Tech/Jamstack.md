# Jamstack

JavaScript, API, MarkUp Architecture.

## 장점

- Fast  
  : 보여줄 페이지가 미리 생성되어 있기 때문에 빠르게 렌더링할 수 있고, CDN이 제공하는 캐시의 이점도 누릴 수 있다.  
  : 브라우저에서 첫 응답을 받기까지 걸리는 시간인 TTFB(Time to First Byte)를 최소화하는 데에는 미리 빌드 된 파일을 CDN을 통해 제공하는 것보다 나은 방법이 없다.
- Secure  
  : 동적으로 변경되는 부분이 적고, 서버나 데이터베이스의 실행이 필요하지 않아 공격에 노출되는 범위가 적다.
- Easy to scale  
  : 전 세계 어디든 CDN을 통해 손쉽게 확장 가능하고, 정적인 HTML 페이지 호스팅 비용은 저렴한 편이다.
- Easy to automate  
  : 빌드 산출물이 단순한 정적 페이지들이라 배포 과정이 단순하다. 정적 자산을 호스팅 서비스에 제공하기만 하면 된다.

## 단점

- 빌드 속도  
  : 페이지 양이 많을수록 빌드 시간이 증가
- 실시간 변경 콘텐츠  
  : 콘텐츠 변경 사항을 반영하기 위해 빌드를 수행해야 함  
  → 이러한 단점을 개선하기 위해 Gatsby, Next.js에서는 '점진적 빌드'라는 실험적인 기능을 발전시켜 나가는 중 : 변경된 부분만 빌드해서 해당 페이지만 다시 생성하는 기술

## 비교

![jam_stack](assets/jam_stack.svg)

### 전통적인 웹 개발 구조

- Database나 CMS(Content Management System)를 사용하여 애플리케이션에 필요한 데이터를 조회하거나 저장한다.
- 앱 서버에서는 다양한 비즈니스 로직 처리를 한다.
- 웹 서버에서는 데이터를 사용하여 HTML 페이지를 만들거나 이미지나 폰트 같은 정적 자원을 브라우저에 전달하는 역할을 한다.

계층들이 강하게 결합되어 있어 의존성이 높고, 서버 운영에 들어가는 비용이 크다.  
→ 서버리스 등장

### 서버리스

서버 시스템을 가상의 클라우드 환경에 두고 운영하는 구조

- 비용 절감 및 필요한 API나 비즈니스 로직 개발에만 집중할 수 있어 개발 생산성 향상
- 웹 개발 구조가 각각의 계층이 독립적인 서비스 형태로 사용할 수 있게 변화
  - Database → DynamoDB, FaunaDB
  - App Server → AWS Lambda, Netlify
- AWS Lambda, Firebase 등 Function 단위의 서비스 등장
- Jamstack 역시 서버리스 개발 구조에서 파생된 개발 구조

### Jamstack

동적 생성이 아니라 정적 생성(페이지 사전 생성, Pre-Render)하여 서버 없이 배포 운영되는 모던 웹 개발 구조  
일반적으로 정적 사이트 생성기(Static Site Generator)를 사용해서 개발하고 빌드하여 정적인 페이지들을 생성  
생성된 결과물을 CDN(Content Delivery Network)을 통해 전송

React에 익숙하다면 Gatsby나 Next.js,  
Vue에 익숙하다면 Nuxt.js,  
VanilaJS에 익숙하다면 11ty,  
Go에 익숙하다면 Hugo,  
Ruby에 익숙하다면 Jekyll

## Gatsby

- React 기반의 정적 사이트 생성기
- 다양한 데이터 타입(JSON, CMS, Markdown...)으로 컨텐츠로 사용 가능
- 거대한 플러그인 시스템
- GraphQL 쿼리 언어를 통한 데이터 조회

### Data Flow

1. 데이터 소스(JSON, CMS, Markdown...)를 Gatsby 플러그인을 사용하여 GraphQL 노드로 변환
2. 변환된 GraphQL 노드 데이터는 GraphQL 쿼리로 조회하고, 조회된 데이터는 React 컴포넌트에서 props를 통해 콘텐츠로 사용
3. 빌드 시 React 컴포넌트들을 조합하여 페이지 생성

### Jamstack과 사용할 수 있는 서비스(생태계)

- CMS : contentful, SANITY
- Function : AWS Lambda, netlify
- Hosting : Azure, netlify, Firebase

검색, 쇼핑, 결제 등 다양한 Third party APIs : algolia(검색 API 서비스), shopify, PayPal  
예로, algolia plugin을 사용하면 빌드 시 검색 대상 콘텐츠들을 algolia 서비스의 검색 대상 레코드(필드)로 등록할 수 있다.  
검색 시에도 React 검색 컴포넌트를 통해 검색어가 입력될 때마다 algolia 서비스에 검색 쿼리 API를 요청하게 되고,  
API 결과로 검색된 결과를 받아 React 검색 결과 리스트 컴포넌트로 보여줄 수 있다.
