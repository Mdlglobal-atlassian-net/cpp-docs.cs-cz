---
title: Cd2dlineargradientbrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: d86235893d1f238f4cba9c927fad17f29060e591
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258721"
---
# <a name="cd2dlineargradientbrush-class"></a>Cd2dlineargradientbrush – třída

Obálka pro ID2D1LinearGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Vytvoří objekt cd2dlineargradientbrush –.|
|[CD2DLinearGradientBrush::~CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destruktor. Volá se, když se likviduje objektu D2D štětec lineárního přechodu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DLinearGradientBrush::Create](#create)|Vytvoří cd2dlineargradientbrush –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Odstraní objekt cd2dlineargradientbrush –. (Přepíše [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DLinearGradientBrush::Get](#get)|Vrátí ID2D1LinearGradientBrush rozhraní|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Načte poslední souřadnice lineárního přechodu|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Načte výchozí souřadnice lineárního přechodu|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Nastaví souřadnice koncové v souřadnicového prostoru štětec lineárního přechodu|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Nastaví souřadnice počátečního v souřadnicového prostoru štětec lineárního přechodu|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::Operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Vrátí ID2D1LinearGradientBrush rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Počáteční a koncový bod přechodu.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Ukazatel ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dlineargradientbrush"></a>  CD2DLinearGradientBrush::~CD2DLinearGradientBrush

Destruktor. Volá se, když se likviduje objektu D2D štětec lineárního přechodu.

```
virtual ~CD2DLinearGradientBrush();
```

##  <a name="attach"></a>  CD2DLinearGradientBrush::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dlineargradientbrush"></a>  CD2DLinearGradientBrush::CD2DLinearGradientBrush

Vytvoří objekt cd2dlineargradientbrush –.

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*LinearGradientBrushProperties*<br/>
Počáteční a koncový bod přechodu.

*colorInterpolationGamma*<br/>
Místo barvou, které se provádí interpolaci mezi Přechodové zarážky.

*extendMode*<br/>
Chování přechodu mimo rozsah [0,1] normalizovaná.

*pBrushProperties*<br/>
Ukazatel na krytí a transformace štětce.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DLinearGradientBrush::Create

Vytvoří cd2dlineargradientbrush –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DLinearGradientBrush::Destroy

Odstraní objekt cd2dlineargradientbrush –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLinearGradientBrush::Detach

Odpojí prostředků rozhraní z objektu

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DLinearGradientBrush::Get

Vrátí ID2D1LinearGradientBrush rozhraní

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1LinearGradientBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getendpoint"></a>  CD2DLinearGradientBrush::GetEndPoint

Načte poslední souřadnice lineárního přechodu

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Návratová hodnota

Koncové dvojrozměrné souřadnice lineárního přechodu v souřadnicového prostoru štětec

##  <a name="getstartpoint"></a>  CD2DLinearGradientBrush::GetStartPoint

Načte výchozí souřadnice lineárního přechodu

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční dvojrozměrné souřadnice lineárního přechodu v souřadnicového prostoru štětec

##  <a name="m_lineargradientbrushproperties"></a>  CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Počáteční a koncový bod přechodu.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

##  <a name="m_plineargradientbrush"></a>  CD2DLinearGradientBrush::m_pLinearGradientBrush

Ukazatel ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

##  <a name="operator_id2d1lineargradientbrush_star"></a>  CD2DLinearGradientBrush::Operator ID2D1LinearGradientBrush *

Vrátí ID2D1LinearGradientBrush rozhraní

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1LinearGradientBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="setendpoint"></a>  CD2DLinearGradientBrush::SetEndPoint

Nastaví souřadnice koncové v souřadnicového prostoru štětec lineárního přechodu

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*point*<br/>
Koncové dvojrozměrné souřadnice lineárního přechodu v souřadnicového prostoru štětec

##  <a name="setstartpoint"></a>  CD2DLinearGradientBrush::SetStartPoint

Nastaví souřadnice počátečního v souřadnicového prostoru štětec lineárního přechodu

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*point*<br/>
Počáteční dvojrozměrné souřadnice lineárního přechodu v souřadnicového prostoru štětec

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
