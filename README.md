# Panorama Reflection

----------------------------------------------------------------------------------------------------------------------------------------------------------------

UE4에서 Panorama Image로 Reflection 효과를 만들어 내는 기능 구현. 

완벽한 Reflection 효과는 UE4에서 제공하는 Ray Tracing으로 표현 하는 것인데, Panorama Image를 활용하는것은 Augment Reality(AR) 물체에 현실의 공간을 Reflection 하기 위해 사용하는 용도로 사용.

----------------------------------------------------------------------------------------------------------------------------------------------------------------

### Panorama Image Mapping

다음 그림과 같은 파노라마 이미지를 Cube Mapping처럼 구체에 맵핑을 함.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/파노라마이미지.png)

Cube Map을 사용하지 않고, 파노라마 이미지를 구체에 맵핑하기 위해서 Blinn/Newell Latitude Mapping 기법을 사용하였다.

![](https://github.com/Devcoder-IndieWorks/PanoramaReflection/blob/master/ScreenShots/sphere_to_2d.gif)

![](https://github.com/Devcoder-Indieworks/PanoramaReflection/blob/master/ScreenShots/sphere_eq.gif)

참고: [Environment Mapping][EnvironmentMappingLink]

[EnvironmentMappingLink]: http://www.reindelsoftware.com/Documents/Mapping/Mapping.html

