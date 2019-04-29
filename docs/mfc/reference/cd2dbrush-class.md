---
title: Cd2dbrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: 1d079ec6c96f96919fde39b73297580ed2a0ac75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391293"
---
# <a name="cd2dbrush-class"></a>Cd2dbrush – třída

Obálka pro ID2D1Brush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Vytvoří objekt cd2dbrush –.|
|[CD2DBrush::~CD2DBrush](#_dtorcd2dbrush)|Destruktor. Volá se, když se likviduje štětce objektu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DBrush::Destroy](#destroy)|Odstraní objekt cd2dbrush –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DBrush::Get](#get)|Vrátí ID2D1Brush rozhraní|
|[CD2DBrush::GetOpacity](#getopacity)|Získá stupeň neprůhlednosti tohoto štětce|
|[CD2DBrush::GetTransform](#gettransform)|Získá aktuální transformace cíle vykreslování|
|[CD2DBrush::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Nastavuje stupeň neprůhlednosti tohoto štětce|
|[CD2DBrush::SetTransform](#settransform)|Použije zadaný transformaci pro cíle vykreslování, nahraďte existující transformace. Všechny následné operace kreslení. Probíhá transformovaný místa|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::Operator ID2D1Brush *](#operator_id2d1brush_star)|Vrátí ID2D1Brush rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Uchovává ukazatel na objekt ID2D1Brush.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Vlastnosti štětce.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dbrush"></a>  Cd2dbrush –:: ~ cd2dbrush –

Destruktor. Volá se, když se likviduje štětce objektu D2D.

```
virtual ~CD2DBrush();
```

##  <a name="attach"></a>  CD2DBrush::Attach

Bude k obrazci existujících prostředků rozhraní objektu.

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nemůže mít hodnotu NULL.

##  <a name="cd2dbrush"></a>  CD2DBrush::CD2DBrush

Vytvoří objekt cd2dbrush –.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*pBrushProperties*<br/>
Ukazatel na krytí a transformace štětce.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="destroy"></a>  CD2DBrush::Destroy

Odstraní objekt cd2dbrush –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBrush::detach

Odpojí prostředků rozhraní z objektu.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DBrush::Get

Vrátí ID2D1Brush rozhraní

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Brush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getopacity"></a>  CD2DBrush::GetOpacity

Získá stupeň neprůhlednosti tohoto štětce

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota mezi 0 a 1, která určuje krytí štětce. Tato hodnota je konstantní násobitel, která se škáluje lineárně alfa všechny pixely sestavil stopy. Před jejich jsou navzájem vynásobeny, jsou hodnoty neprůhlednosti omezen v rozsahu od 0 do 1.

##  <a name="gettransform"></a>  CD2DBrush::GetTransform

Získá aktuální transformace cíle vykreslování

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Parametry

*transform*<br/>
Když to vrátí, obsahuje aktuální transformace cíl vykreslování. Tento parametr je předán bez inicializace.

##  <a name="isvalid"></a>  CD2DBrush::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_pbrush"></a>  CD2DBrush::m_pBrush

Uchovává ukazatel na objekt ID2D1Brush.

```
ID2D1Brush* m_pBrush;
```

##  <a name="m_pbrushproperties"></a>  CD2DBrush::m_pBrushProperties

Vlastnosti štětce.

```
CD2DBrushProperties* m_pBrushProperties;
```

##  <a name="operator_id2d1brush_star"></a>  CD2DBrush::Operator ID2D1Brush *

Vrátí ID2D1Brush rozhraní

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Brush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="setopacity"></a>  CD2DBrush::SetOpacity

Nastavuje stupeň neprůhlednosti tohoto štětce

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Parametry

*Míra průhlednosti*<br/>
Hodnota mezi 0 a 1, která určuje krytí štětce. Tato hodnota je konstantní násobitel, která se škáluje lineárně alfa všechny pixely sestavil stopy. Před jejich jsou navzájem vynásobeny, jsou hodnoty neprůhlednosti omezen v rozsahu od 0 do 1.

##  <a name="settransform"></a>  CD2DBrush::SetTransform

Použije zadaný transformaci pro cíle vykreslování, nahraďte existující transformace. Všechny následné operace kreslení. Probíhá transformovaný místa.

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Parametry

*transform*<br/>
Transformací, která se má použít pro cíl vykreslování

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
