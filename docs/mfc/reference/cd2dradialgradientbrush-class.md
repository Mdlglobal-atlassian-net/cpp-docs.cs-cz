---
title: Cd2dradialgradientbrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 22029ebcf8cf519571e81e11c84de146c9d54b26
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277271"
---
# <a name="cd2dradialgradientbrush-class"></a>Cd2dradialgradientbrush – třída

Obálka pro ID2D1RadialGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Vytvoří objekt cd2dlineargradientbrush –.|
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destruktor. Volá se, když se likviduje objektu D2D štětec paprskového přechodu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DRadialGradientBrush::Create](#create)|Vytvoří cd2dradialgradientbrush –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Odstraní objekt cd2dradialgradientbrush –. (Přepíše [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DRadialGradientBrush::Get](#get)|Vrátí ID2D1RadialGradientBrush rozhraní|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Načte centra přechodu elipsa|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Načte posun počátek přechodu vzhledem k přechodu elipsa center|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Načte x poloměr elipsy přechodu|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Načte poloměr y přechodu elipsa|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Určuje centra přechodu elipsy v souřadnicového prostoru štětec|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Určuje posun počátek přechodu vzhledem k přechodu elipsa center|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Určuje poloměr x přechodu elipsy v souřadnicového prostoru štětec|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Určuje poloměr y přechodu elipsy v souřadnicového prostoru štětec|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::Operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Vrátí ID2D1RadialGradientBrush rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Ukazatel ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|System center, posun přechodu původu a x-radius a poloměr y štětce vaší přechodu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dradialgradientbrush"></a>  Cd2dradialgradientbrush –:: ~ cd2dradialgradientbrush –

Destruktor. Volá se, když se likviduje objektu D2D štětec paprskového přechodu.

```
virtual ~CD2DRadialGradientBrush();
```

##  <a name="attach"></a>  CD2DRadialGradientBrush::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::CD2DRadialGradientBrush

Vytvoří objekt cd2dlineargradientbrush –.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*gradientStops*<br/>
Ukazatel na pole D2D1_GRADIENT_STOP struktur.

*gradientStopsCount*<br/>
Hodnota větší než nebo rovna 1, která určuje počet Přechodové zarážky v poli gradientStops.

*RadialGradientBrushProperties*<br/>
System center, posun přechodu původu a x-radius a poloměr y štětce vaší přechodu.

*colorInterpolationGamma*<br/>
Místo barvou, které se provádí interpolaci mezi Přechodové zarážky.

*extendMode*<br/>
Chování přechodu mimo rozsah [0,1] normalizovaná.

*pBrushProperties*<br/>
Ukazatel na krytí a transformace štětce.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DRadialGradientBrush::Create

Vytvoří cd2dradialgradientbrush –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DRadialGradientBrush::Destroy

Odstraní objekt cd2dradialgradientbrush –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DRadialGradientBrush::detach

Odpojí prostředků rozhraní z objektu

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DRadialGradientBrush::Get

Vrátí ID2D1RadialGradientBrush rozhraní

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1RadialGradientBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getcenter"></a>  CD2DRadialGradientBrush::GetCenter

Načte centra přechodu elipsa

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Návratová hodnota

System center přechodu elipsy. Tato hodnota je vyjádřena v souřadnicového prostoru štětec

##  <a name="getgradientoriginoffset"></a>  CD2DRadialGradientBrush::GetGradientOriginOffset

Načte posun počátek přechodu vzhledem k přechodu elipsa center

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

Posun počátek přechodu z centra přechodu elipsy. Tato hodnota je vyjádřena v souřadnicového prostoru štětec

##  <a name="getradiusx"></a>  CD2DRadialGradientBrush::GetRadiusX

Načte x poloměr elipsy přechodu

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Návratová hodnota

X poloměr elipsy přechodu. Tato hodnota je vyjádřena v souřadnicového prostoru štětec

##  <a name="getradiusy"></a>  CD2DRadialGradientBrush::GetRadiusY

Načte poloměr y přechodu elipsa

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Návratová hodnota

Y poloměr elipsy přechodu. Tato hodnota je vyjádřena v souřadnicového prostoru štětec

##  <a name="m_pradialgradientbrush"></a>  CD2DRadialGradientBrush::m_pRadialGradientBrush

Ukazatel ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

##  <a name="m_radialgradientbrushproperties"></a>  CD2DRadialGradientBrush::m_RadialGradientBrushProperties

System center, posun přechodu původu a x-radius a poloměr y štětce vaší přechodu.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

##  <a name="operator_id2d1radialgradientbrush_star"></a>  CD2DRadialGradientBrush::Operator ID2D1RadialGradientBrush *

Vrátí ID2D1RadialGradientBrush rozhraní

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1RadialGradientBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="setcenter"></a>  CD2DRadialGradientBrush::SetCenter

Určuje centra přechodu elipsy v souřadnicového prostoru štětec

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*point*<br/>
System center přechodu elipsy v souřadnicového prostoru štětec

##  <a name="setgradientoriginoffset"></a>  CD2DRadialGradientBrush::SetGradientOriginOffset

Určuje posun počátek přechodu vzhledem k přechodu elipsa center

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parametry

*gradientOriginOffset*<br/>
Posun počátek přechodu z centra přechodu elipsa

##  <a name="setradiusx"></a>  CD2DRadialGradientBrush::SetRadiusX

Určuje poloměr x přechodu elipsy v souřadnicového prostoru štětec

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parametry

*radiusX*<br/>
X poloměr elipsy přechodu. Tato hodnota je v souřadnicového prostoru štětec

##  <a name="setradiusy"></a>  CD2DRadialGradientBrush::SetRadiusY

Určuje poloměr y přechodu elipsy v souřadnicového prostoru štětec

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parametry

*radiusY*<br/>
Y poloměr elipsy přechodu. Tato hodnota je v souřadnicového prostoru štětec

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
