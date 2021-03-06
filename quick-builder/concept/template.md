# Template 준비하기

Quick Builder를 통해 ICS에 템플릿을 일괄 등록하기 위해, 아래와 같이 준비가 필요합니다. Template 내의 링크 및 리소스의 경로, 폴더 및 공통 영역에 대한 소스 등을 사전에 정의해두면 빠르게 쉽게 ICS를 위한 템플릿이 등록됩니다.



### Template 구성

Quick Builder로 사이트를 구축하기 위해 필요한 템플릿을 준비합니다. \*.html, \*.css, \*.js, resource files 로 구성되어있습니다.&#x20;

html, php, jsp, asp,css,js 등 또 그 외의 확장자를 가진 Template으로 등록하여 버전관리가 필요한 경우, 추가로 지정할 수 있습니다.

단, 템플릿만 등록한 Quick Builder에서는 템플릿으로 등록할 확장자를 지정할 수 없습니다.&#x20;



### Resource File 네이밍

Resource File의 네이밍이 ICS의 규격과 맞지 않는 경우 Quick Builder로 등록이 불가할 수 있습니다.  파일 내에 아래와 같은 파일명이 있다면, 다른 네이밍으로 변환하여 저장해주세요.

{% hint style="info" %}
Resource file에서 지원하지 않는 문자가 파일명에 있다면 변경되어야 합니다.&#x20;

특수문자(\~,!,#,$,%,^,&,\*,+)를 사용되고 있다면 반드시 변경해주세요. 특히 파일명이 한글이거나, 일본어로 된 경우도 반드시 영문으로 변경해야 합니다.
{% endhint %}



### Directory 구성&#x20;

Template 내 생성한 디렉토리는 향후 ICS의 카테고리(사이트 , 콘텐츠) 가 됩니다.&#x20;

ICS에서 관리 및 구축이 용이한 폴더 관리 방식은 메뉴별로 폴더가 구성되는 것이 좋습니다.&#x20;

메뉴별로 만들어진 폴더에 각각 HTML파일을 두게 되면, ICS의 사이트 카테고리에 HTML이 등록되므로, 콘텐츠 관리 측면에서 좋습니다.

> **주의사항 **
>
> 메뉴의 뎁스는 최대 9뎁스 이상을 초과할 경우 생성이 불가합니다.&#x20;
>
> 한 뎁스 내에 생성될 폴더는 최대 1156개를 초과할 경우, 퀵빌더를 통한 생성이 불가합니다.&#x20;

### Directory 내에 .ics\_cat\_info 구성

최상위 루트에서 생성 시, 사이트 카테고리 또는 컨텐츠 카테고리를 생성할 때 .ics\__cat_\_info 파일안에 아래와 같이 작성해두면, 생성할 때 카테고리 이름이나, 설명, 액션필드설정, 사이트카테고리 메타필드 정보를 설정할 수 있습니다.

카테고리를 생성할 디렉토리마다 해당 파일을 만들어 두면 됩니다.&#x20;

```
{
	catNm : '(카테고리 이름)',
	catExp : '(카테고리 설명)',
	afields : ['ActionField ID 1', 'ActionField ID 2'],
	metas : [{metaId:'(MetaField ID)', metaNm:'(Mefield Name)', typeCd:'(Metafield Type)', value:'(Metafield Value)'}]
}
```



### Link 설정&#x20;

파일 간의 경로는 “/” 또는 “../” 등의 절대경로, 상대경로로 링크가 되어야 합니다. 내 local 에서 열어보더라도 온전하게 링크가 되도록 하는 것이 가장 좋습니다.

```
<link href="/assets/css/style1.css" rel="stylesheet">
<link href="../../assets/css/style2.css" rel="stylesheet">

<img src="/assets/images/a.jpg">
<img src="../../assets/images/a.jpg">

<a href="/menu1/submenu1/index.html">Template</a>
<a href="../../menu1/submenu1/index.html">Template</a>
```

파일은 템플릿으로 등록할 파일과 리소스 업로드로 등록할 파일이 나눠지는데, 연결 시, 리소스 파일로 링크가 되는 부분은 \[\[--ImgRootDir--]]로 변환되며, 템플릿으로 링크가 되는 부분은 \[\[--CatAddress,(속성)--]]에 옵션이 추가된 상태로 변환됩니다.

만약, 내가 업로드할 위치에 Template에 리소스의 경로를 정확하게 맞춰, 경로 상에 실제로 리소스 파일이 위치한다면, Template의 경로도 변환됩니다. 때문에 한번에 Template과 리소스 파일을 꼭 같이 올려야 하는 것은 아닙니다. &#x20;

{% hint style="info" %}
만약, 경로 상에 링크되는 대상이 없는 경우에는 해당 링크 부분을 변환하지 않습니다. 이 경우, Quick Builder 생성 후, 직접 수정되어야 하므로, Template 만들 경우에 경로를 꼭 확인해주세요.
{% endhint %}



### Custom Tag 설정

헤더(header) 또는 푸터(Footer)와 같이 반복적으로 사용되는 소스는 커스텀택으로 추출되어 관리할 수 있습니다. 템플릿을 압축하기 전에 미리 영역을 지정해야 하며, 태그는 아래와 같이 정의합니다.

```
<!--CUSTOM_TAG_START[(custom tag name)]-->

Template Source

<!--CUSTOM_TAG_END[(custom tag name)]-->
```

custom tag name (괄호는 포함되지 않습니다) 을 동일하게 입력하게 되어야 템플릿 내에 해당 소스를 공통 소스 영역으로 인지하고 Custom Tag으로 추출됩니다.&#x20;

만약 , Quick Builder를 생성할 떄마다 커스텀택의 네이밍이 변경이 필요하다면 아래의 옵션을 적용해 볼 수 있습니다. custom tag name 에 "@"를 붙여서 네이밍을 다르게 하여 추출하는 방식입니다. 이 결과는 \[\[--site\_(등록할 사이트카테고리 아이디)\_header--]]로 생성됩니다.&#x20;

최상위 루트에서 생성할 때, 사이트마다 다른 아이디 체계를 가지고 있으면서, 커스텀태그도 각자 생성해야 할 경우에 이 방식을 사용할 수 있습니다. 다만, 사이트 카테고리 하위에서 생성할 때는 하위로 생성될 아이디를 따라가므로, 이 부분은 유의해주세요.

```
<!--CUSTOM_TAG_START[site_@_header]-->

Template Source

<!--CUSTOM_TAG_END[site_@_header]-->
```

&#x20;



### Zip file 압축&#x20;

템플릿의 준비가 모두 완료되면, 해당 파일과 모든 디렉토리를 ZIP파일로 압축합니다.

> **주의사항**
>
> Mac에서 압축을 하는 경우, Mac에서 생성된 hidden directory가 Zip파일 내에 함께 생성될 수 있습니다. Windows 내에서 압축하는 것을 권장합니다.
