# Panorama Reflection

----------------------------------------------------------------------------------------------------------------------------------------------------------------

UE4에서 Panorama Image로 Reflection 효과를 만들어 내는 기능 구현. 

완벽한 Reflection 효과는 UE4에서 제공하는 Ray Tracing으로 표현 하는 것인데, Panorama Image를 활용하는것은 Augment Reality(AR) 물체에 현실의 공간을 Reflection 하기 위해 사용하는 용도로 사용.

----------------------------------------------------------------------------------------------------------------------------------------------------------------

### Panorama Image Mapping

다음 그림과 같은 파노라마 이미지를 Cube Mapping처럼 구체에 맵핑을 함.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/파노라마이미지.png)

Cube Map을 사용하지 않고, 파노라마 이미지를 구체에 맵핑하기 위해서 Blinn/Newell Latitude Mapping 기법을 사용하였다.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/sphere_to_2d.png)

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/sphere_eq.png)

참고: [Environment Mapping][EnvironmentMappingLink]

[EnvironmentMappingLink]: http://www.reindelsoftware.com/Documents/Mapping/Mapping.html

----------------------------------------------------------------------------------------------------------------------------------------------------------------

### Blinn/Newell Latitude Mapping Material Function

Blinn/Newell Latitude Mapping이 적용된 UE4 Material Function을 제작 함.

계산 공식은 다음과 같음:

**U = atan(rx/ry) + 3.142/2 * 3.142**

**V = asin(-rz) + 3.142/2/3.142**

rx,ry,rz는 Reflection Vector의 요소이다.

위 계산 공식으로 만들어진 Material Function은 다음 그림과 같다.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/MF_PanoramaReflectionMapping.png)

이렇게 만들어진 Material Function을 AutomotiveMaterial에 적용한 예가 다음 그림과 같다.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/Material_적용.png)

빨간색 상자로 표시된 항목은 Clear Coat Roughness 값이고, 이 값을 선형 보간의 Alpha값으로 사용하였다.

노란색 상자로 표시된 항목은 Reflection Vector 방향에서 투영된 Panorama Image의 Pixel 값이고, 파란색 상자로 표시된 항목은 도색 Pixel 값이다. 이 두값을  선형 보간하여 Material의 Base Color 값으로 사용한다.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/Material_Instance_설정.png)

위 그림처럼 Panorama Texture를 설정 해 준다.

----------------------------------------------------------------------------------------------------------------------------------------------------------------

### 결과 화면 비교

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/파노라마맵핑_적용_화면.png)

