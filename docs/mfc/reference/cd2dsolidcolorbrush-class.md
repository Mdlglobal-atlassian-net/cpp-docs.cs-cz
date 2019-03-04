---
title: Cd2dsolidcolorbrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 41d1d1b8c28335ae6207e41d696359295a83e646
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291233"
---
# <a name="cd2dsolidcolorbrush-class"></a>Cd2dsolidcolorbrush – třída

Obálka pro ID2D1SolidColorBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Přetíženo. Vytvoří objekt cd2dsolidcolorbrush –.|
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](#cd2dsolidcolorbrush__~cd2dsolidcolorbrush)|Destruktor. Volá se, když se likviduje štětec objektu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DSolidColorBrush::Create](#create)|Vytvoří cd2dsolidcolorbrush –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Odstraní objekt cd2dsolidcolorbrush –. (Přepíše [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DSolidColorBrush::Get](#get)|Vrátí ID2D1SolidColorBrush rozhraní|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Zjišťuje barvu štětec jednotné barvy|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Určuje barvu tohoto štětec jednotné barvy|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::Operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|Vrátí ID2D1SolidColorBrush rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Plnobarevné štětce.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Uchovává ukazatel na objekt ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dsolidcolorbrush"></a>  Cd2dsolidcolorbrush –:: ~ cd2dsolidcolorbrush –

Destruktor. Volá se, když se likviduje štětec objektu D2D.

```
virtual ~CD2DSolidColorBrush();
```

##  <a name="attach"></a>  CD2DSolidColorBrush::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::CD2DSolidColorBrush

Vytvoří objekt cd2dsolidcolorbrush –.

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*color*<br/>
Červené, zelená, modrá a alfa hodnoty barvy na stopu.

*pBrushProperties*<br/>
Ukazatel na krytí a transformace štětce.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

*nAlpha*<br/>
Neprůhlednost Barva stopy.

##  <a name="create"></a>  CD2DSolidColorBrush::Create

Vytvoří cd2dsolidcolorbrush –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DSolidColorBrush::Destroy

Odstraní objekt cd2dsolidcolorbrush –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DSolidColorBrush::detach

Odpojí prostředků rozhraní z objektu

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DSolidColorBrush::Get

Vrátí ID2D1SolidColorBrush rozhraní

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1SolidColorBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getcolor"></a>  CD2DSolidColorBrush::GetColor

Zjišťuje barvu štětec jednotné barvy

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva této štětec jednotné barvy

##  <a name="m_colorsolid"></a>  CD2DSolidColorBrush::m_colorSolid

Plnobarevné štětce.

```
D2D1_COLOR_F m_colorSolid;
```

##  <a name="m_psolidcolorbrush"></a>  CD2DSolidColorBrush::m_pSolidColorBrush

Uchovává ukazatel na objekt ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

##  <a name="operator_id2d1solidcolorbrush_star"></a>  CD2DSolidColorBrush::Operator ID2D1SolidColorBrush *

Vrátí ID2D1SolidColorBrush rozhraní

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1SolidColorBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="setcolor"></a>  CD2DSolidColorBrush::SetColor

Určuje barvu tohoto štětec jednotné barvy

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Barva této štětec jednotné barvy

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
