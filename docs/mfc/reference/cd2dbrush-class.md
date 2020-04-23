---
title: Třída CD2DBrush
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
ms.openlocfilehash: 536d84fe2c2f68d62490e1ce2b65085426762e87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754191"
---
# <a name="cd2dbrush-class"></a>Třída CD2DBrush

Obálka pro ID2D1Brush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Vytvoří objekt CD2DBrush.|
|[CD2DBrush::~CD2DBrush](#_dtorcd2dbrush)|Destruktor. Volána při zničení objektu stopy D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DBrush::Destroy](#destroy)|Zničí objekt CD2DBrush. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DBrush::Získat](#get)|Vrátí rozhraní ID2D1Brush.|
|[CD2DBrush::GetOpacity](#getopacity)|Získá stupeň krytí této stopy|
|[CD2DBrush::GetTransform](#gettransform)|Získá aktuální transformace cíle vykreslení|
|[CD2DBrush::IsValid CD2DBrush:IsValid CD2DBrush::IsValid CD2D](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Nastaví stupeň krytí této stopy.|
|[CD2DBrush::SetTransform](#settransform)|Aplikuje zadanou transformaci na cíl vykreslení a nahradí existující transformaci. Všechny následné operace kreslení probíhají v transformovaném prostoru|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::operátor ID2D1Brush*](#operator_id2d1brush_star)|Vrátí rozhraní ID2D1Brush.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Uloží ukazatel na objekt ID2D1Brush.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Vlastnosti stopy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush::~CD2DBrush

Destruktor. Volána při zničení objektu stopy D2D.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush::Připojit

Připojí k objektu existující rozhraní prostředků.

```cpp
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nemůže být null.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush::CD2DBrush

Vytvoří objekt CD2DBrush.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*pVlastnosti brushu*<br/>
Ukazatel na krytí a transformaci stopy.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::Destroy

Zničí objekt CD2DBrush.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush::Získat

Vrátí rozhraní ID2D1Brush.

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Brush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush::GetOpacity

Získá stupeň krytí této stopy

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota mezi nulou a 1, která označuje krytí stopy. Tato hodnota je konstantní násobitel, který lineárně mění hodnotu alfa všech obrazových bodů vyplněných stopou. Hodnoty krytí jsou upnuty v rozsahu 0 až 1 před tím, než jsou vynásobeny společně.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush::GetTransform

Získá aktuální transformace cíle vykreslení

```cpp
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Parametry

*Transformace*<br/>
Když to vrátí, obsahuje aktuální transformace cíle vykreslení. Tento parametr se předává neinicializovaný.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush::IsValid CD2DBrush:IsValid CD2DBrush::IsValid CD2D

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush::m_pBrush

Uloží ukazatel na objekt ID2D1Brush.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush::m_pBrushProperties

Vlastnosti stopy.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::operátor ID2D1Brush*

Vrátí rozhraní ID2D1Brush.

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Brush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush::SetOpacity

Nastaví stupeň krytí této stopy.

```cpp
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Parametry

*Krytí*<br/>
Hodnota mezi nulou a 1, která označuje krytí stopy. Tato hodnota je konstantní násobitel, který lineárně mění hodnotu alfa všech obrazových bodů vyplněných stopou. Hodnoty krytí jsou upnuty v rozsahu 0 až 1 před tím, než jsou vynásobeny společně.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::SetTransform

Aplikuje zadanou transformaci na cíl vykreslení a nahradí existující transformaci. Všechny následné operace kreslení probíhají v transformovaném prostoru.

```cpp
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Parametry

*Transformace*<br/>
Transformace, která se má použít pro cíl vykreslení

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
