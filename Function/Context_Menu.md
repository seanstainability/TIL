# Context Menu

팝오버 형태의 컨텍스트 메뉴

## 기능 요구사항

- 메뉴 목록이 존재한다.
- 각 메뉴를 클릭하면 해당 메뉴에 관련된 팝오버가 나타난다.
- 팝오버를 선택하거나 혹은 그 외의 부분 클릭 시 팝오버가 사라진다.
- 팝오버 상태에서 다른 메뉴를 클릭 시 해당 메뉴의 팝오버가 나타나고, 기존 팝오버는 사라진다.

## 키워드
- Document.querySelector()
- Document.querySelectorAll()

- EventTarget.addEventListener()
- EventTarget.removeEventListener()

- Element.classList : add, remove, toggle, contains

- Event.target
- Event.currentTarget

- Event.stopPropagation()
- Event.preventDefault()

- Element.removeAttribute()

- Node.parentElement
- Node.nodeName

- 이벤트 캡처링
- 이벤트 버블링
- 이벤트 위임
