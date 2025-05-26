# O'Kitchen

</br>
</br>

### 🔍 주요특징
1. 모바일 메뉴
* 탭 클릭 시 모바일 메뉴와 배경 dim 효과 활성화.
* dim 영역 또는 닫기 버튼 클릭 시 모바일 메뉴 비활성화.

2. 슬라이더 기능
* 메인 슬라이더: 이전 및 다음 네비게이션 버튼과 분수 형태의 페이지네이션 제공.
* 서브 슬라이더: 반응형 디자인으로 다양한 화면 크기에 맞춰 슬라이드 수 조정.

3. 지도
* Google Maps API를 사용하여 지정된 위도 및 경도에 마커를 추가.
* 지도 제어 요소를 비활성화하여 사용자 경험 최적화.

</br>

### 🛠️ 사용 기술

![My Skills](https://skillicons.dev/icons?i=js,html,css,github,vercel)

<img src="https://img.shields.io/badge/Javascript-f7df1e?style=flat-square&logo=Javascript&logoColor=000000"/> <img src="https://img.shields.io/badge/HTML5-F05032?style=flat-square&logo=HTML5&logoColor=FFFFFF"/> <img src="https://img.shields.io/badge/CSS3-007ACC?style=flat-square&logo=CSS3&logoColor=FFFFFF"/> <img src="https://img.shields.io/badge/GitHub-000000?style=flat-square&logo=github&logoColor=FFFFFF"/> <img src="https://img.shields.io/badge/vercel-F2F2F2?style=flat-square&logo=vercel&logoColor=000000"/> <img src="https://img.shields.io/badge/Respond web -302683?style=flat-square&logo=htmlacademy&logoColor=FFFFFF"/>

</br>

### ⚙️ 기능 상세 설명

### ☂ 1. 모바일 메뉴
기능:
-
탭 버튼 클릭 시 모바일 메뉴를 열고 배경 dim 효과를 활성화합니다.

작동 방식:
-
* e.preventDefault(): 기본 클릭 동작을 방지합니다.
* document.body.classList.add("fixed"): 페이지 스크롤을 고정합니다.
* mobile.classList.add("active"): 모바일 메뉴를 표시합니다.
* dim.classList.add("active"): dim 효과를 적용합니다.


 ``` JavaScript
tab.addEventListener("click", function(e) {
    e.preventDefault();

    document.body.classList.add("fixed");
    mobile.classList.add("active");
    dim.classList.add("active");
});
```

---

</br>

### ☂ 2. 초기화 및 섹션 리스트 설정
- 페이지 로드 시 signature ID를 제외한 섹션을 pageList 배열에 추가하여 
- 나중에 사용할 섹션 리스트를 준비합니다.

``` JavaScript
	window.dispatchEvent(new Event('resize'));
	sectionList.forEach(function(item){
		if(item.getAttribute("id")!= "signature"){
			pageList.push(item);
		}
	});
```
---

</br>

### ☂ 3. 스크롤 이벤트 처리
- 사용자가 스크롤할 때 헤더의 고정 상태를 조정합니다.
- 스크롤 위치가 0보다 크면 헤더에 fixed 클래스를 추가하고,
- 최상단일 경우 클래스를 제거합니다.

<img src="images/heder.fixed.png" width="100%" alt="스크롤 이벤트 처리">

 ``` JavaScript
	window.addEventListener("scroll", function(){
		if(window.scrollY > 0){
			header.classList.add("fixed");
		}
		else{
			header.classList.remove("fixed");
		}
	});
```

---

</br>

### ☂ 4. 탭 클릭 이벤트
- 탭을 클릭할 때 기본 동작을 방지하고,
- 모바일 뷰일 경우 탭의 상태를 변경하여 메뉴를 열거나 닫습니다.
- 탭 클릭 시 관련 클래스를 추가하거나 제거합니다.

<img src="images/mobile_tab.gif" width="320px" alt="탭 클릭 이벤트">

 ``` JavaScript
	let topPos=0;

	tab.addEventListener("click", function(e){
		e.preventDefault();
		if(isMobile == true){
			if(tab.classList.contains("close") == false){
				tab.classList.add("close");
				gnb.classList.add("active");
				dim.classList.add("active");
			}
			else{
				tab.classList.remove("close");
				gnb.classList.remove("active");
				dim.classList.remove("active");
			}
		}
	});
```

---

</br>

### ☂ 5. 메뉴 항목 클릭 이벤트
- 메뉴 항목 클릭 시 해당 섹션으로 부드럽게 스크롤 애니메이션을 진행합니다. 
- 스크롤이 완료되면 탭과 내비게이션 바의 상태를 초기화합니다.

 ``` JavaScript
	menuList.forEach(function(item, i){
		menuList[i].addEventListener("click", function(e){
			e.preventDefault();
			topPos=pageList[i].offsetTop;
			gsap.to(window, { scrollTo: topPos, duration: 0.4, onComplete: function(){
				tab.classList.remove("close");
				gnb.classList.remove("active");
				dim.classList.remove("active");
			}});
		});
	});
```

---

</br>

### 📱 모바일 반응형 이미지

| 모바일 메인페이지 | 모바일 메뉴 | 구단의 역사 |
|------------------|------------|-------------|
| ![](images/mobile_slider.png) | ![](images/mobile_menu.png) | ![](images/mobile_history.png) |


| 챔피언스컵 위너 | 발롱도르 위너 | 비지니스 구축 |
|------------------|------------|-------------|
| ![](images/mobile_champs.png) | ![](images/mobile_winners.png) | ![](images/mobile_business.png) |

</br>

### 🧾 Review

사이트 특징<br>
|---------------------|
탐색 용이성: 메뉴가 잘 구성되어 있어 사용자가 원하는 정보를 쉽게 찾을 수 있습니다.
모바일 최적화: 다양한 디바이스에서 접근할 수 있도록 반응형 디자인이 적용되었습니다.
빠른 로딩 속도: 사이트의 로딩 속도가 빠르며, 사용자에게 긍정적인 경험을 제공합니다.
상호작용 요소: 소셜 미디어 연동 등 팬과의 상호작용을 촉진하는 요소가 포함되어 있습니다.

</br>


이 프로젝트는 AC 밀란의 공식 웹사이트를 기반으로 하여<br> 클럽의 브랜드 아이덴티티를 반영한 사용자 친화적인 디자인을 제공합니다.

### 🧾 View
https://ac-milan-custom-site.vercel.app/
