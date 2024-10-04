# Avatars 과제

## 목차

1. [코드 주요 설명](#코드-주요-설명)
2. [결과 화면](#결과-화면)
3. [과제 조건 확인](#과제-조건-확인)
<!-- 4. [결론](#결론) -->

## 코드 주요 설명

![표시](./../assets/images/labelled.jpg)

### title

> 'Avatars' 문구를 `span`으로 구현

### main-container

> - profile-container를 감싸는 전체 배경을 `div`로 구현
> - 안에 profile-container를 가운데로 오게 하기 위해 **flex 컨테이너**로 구현하여 `justify-content`와 `align-items`를 모두 center로 지정

### profile-container

> - 총 8개의 profile을 감싸는 큰 컨테이너를 `div`로 구현
> - 안에 profile들이 주어진 간격을 갖고 나열되도록 **flex 컨테이너**로 구현
> - 각 줄에 4개씩 배열되도록 적절한 width를 지정한 후 `wrap` 설정을 주어 5개째부터는 다음줄로 넘어가도록 구현
>   > 이를 `grid`로 구현할까 고민했으나 `flex`를 지원하는 브라우저가 반드시 `grid`도 지원한다는 보장이 없다고 생각하여 그냥 `flex`로 구현함 (아직 잘 모르겠음)

### profile

> - 각 프로필 이미지와 활동 상태를 표시하는 동그라미(status-info)를 감싸는 작은 컨테이너를 `div`로 구현
> - 활동 상태 동그라미의 위치 배열을 위해`relative`로 설정

#### img

> 프로필 이미지를 `img` 태그를 사용하여 첨부

#### status-info

> - 활동 상태인 동그라미의 class를 online, 비활동 상태를 offline이라 명명
> - `img` 위에 올라와 우측 하단에 위치할 수 있도록 `absolute`로 설정한 후 right, bottom 간격을 지정함

## 결과 화면

![전체화면](./../assets/images/full-screen.jpg)
![축소된 창](./../assets/images/shrinked-window.jpg)

첫 번째 이미지는 브라우저가 전체 화면 상태일 때, 두번째 이미지는 브라우저가 전체 화면 상태를 벗어나 축소된 상태일 때의 결과를 캡쳐한 것이다.

## 과제 조건 확인

- [x] 아바타 이미지는 배경 방식이 아닌 콘텐츠 이미지(\<img\> 요소)로 마크업한다. <br/>
- [x] 이미지 `성능 최적화` 방법에 대해 고민해본다. <br/>
  > 이미지 성능 최적화를 위해 강의 시간에 배운 `지연 로딩`을 각 img 태그에 적용함

```
<img src="./../assets/avatars/face7.jpg" loading="lazy" alt="" />
```

- [x] 아바타의 `상태 정보`를 알 수 있도록 정보를 제공한다. <br/>
  > 각 아바타 이미지 우측 하단에 상태 정보를 알리는 동그라미 div 구현
- [x] 아바타 이미지의 크기 - 64px X 64px <br/>

```
img {
  width: 64px;
  height: 64px;
  border-radius: 50%;
}
```

- [x] 아바타 이미지 간의 간격 - 20px <br/>
  > 아바타 이미지들을 감싸는 div에 gap을 지정

```
.profile-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  width: 316px;
}
```

- [x] 회색 원 배경색 - #DBDBDB <br/>

```
.offline {
  background-color: #dbdbdb;
}
```

- [x] 초록색 원 배경색- #4CFE88 <br/>

```
.online {
  background-color: #4cfe88;
}
```

<!--
## 성찰

주어진 과제는 크게 **두 가지** 였다. <br />

> 1. `float`를 사용하여 다음의 레이아웃을 구현해 본다.
> 1. `flex`를 지원하는 환경에서는 다음과 같이 배치되도록 레이아웃을 구현해 본다.

여기서 **`flex`를 지원하는 환경**이 무슨 말인지 생각해보던 중 [**caniuse**](https://caniuse.com/) 사이트가 떠올랐다.
![flex 지원 여부](./../assets/images/caniuse-flex.jpg)

`flex`를 지원하지 않는 일부 브라우저가 존재하기 때문에 이를 고려하여

> 1. 지원하지 않는 브라우저 -> `float` 사용
> 1. 지원하는 브라우저 -> `flex` 사용

이런 방식으로 구현하라는 뜻으로 해석했다.

그런데 어떻게 해야 각 브라우저에서 지원하는 방식을 채택할 수 있는지 모르겠어서 `flex`로만 구현했다.

---

브라우저 창이 더 축소되었을 때 가로줄에 4개였던 프로필 이미지의 배열이 3개, 2개, 1개로 줄어든다.
-->
