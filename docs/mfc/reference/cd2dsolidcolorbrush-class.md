---
title: Třída CD2DSolidColorBrush
ms.date: 03/27/2019
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
ms.openlocfilehash: d66a92e4801f7a13c62e2d83fdb94411d077ff53
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750254"
---
# <a name="cd2dsolidcolorbrush-class"></a>Třída CD2DSolidColorBrush

Obálka pro ID2D1SolidColorBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Přetíženo. Vytvoří objekt CD2DSolidColorBrush.|
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|Destruktor. Nazývá se při zničení objektu pevnéstopy D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DSolidColorBrush::Vytvořit](#create)|Vytvoří cd2DSolidColorBrush. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Zničí objekt CD2DSolidColorBrush. (Přepíše [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DSolidColorBrush::Získat](#get)|Vrátí rozhraní ID2D1SolidColorBrush.|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Načte barvu štětce plné barvy.|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Určuje barvu této plné barevné stopy.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::operátor ID2D1SolidColorBrush*](#operator_id2d1solidcolorbrush_star)|Vrátí rozhraní ID2D1SolidColorBrush.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Štětec plná barva.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Uloží ukazatel na objekt ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a>CD2DSolidColorBrush::~CD2DSolidColorBrush

Destruktor. Nazývá se při zničení objektu pevnéstopy D2D.

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a>CD2DSolidColorBrush::Připojit

Připojí k objektu existující rozhraní prostředků.

```cpp
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a>CD2DSolidColorBrush::CD2DSolidColorBrush

Vytvoří objekt CD2DSolidColorBrush.

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
Ukazatel na cíl vykreslení.

*color*<br/>
Hodnoty barvy stopy červené, zelené, modré a alfa.

*pVlastnosti brushu*<br/>
Ukazatel na krytí a transformaci stopy.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

*nAlfa*<br/>
Krytí barvy stopy.

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a>CD2DSolidColorBrush::Vytvořit

Vytvoří cd2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a>CD2DSolidColorBrush::Destroy

Zničí objekt CD2DSolidColorBrush.

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a>CD2DSolidColorBrush::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a>CD2DSolidColorBrush::Získat

Vrátí rozhraní ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1SolidColorBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a>CD2DSolidColorBrush::GetColor

Načte barvu štětce plné barvy.

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva tohoto štětce s plnou barvou

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a>CD2DSolidColorBrush::m_colorSolid

Štětec plná barva.

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a>CD2DSolidColorBrush::m_pSolidColorBrush

Uloží ukazatel na objekt ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a>CD2DSolidColorBrush::operátor ID2D1SolidColorBrush*

Vrátí rozhraní ID2D1SolidColorBrush.

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1SolidColorBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a>CD2DSolidColorBrush::SetColor

Určuje barvu této plné barevné stopy.

```cpp
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Barva tohoto štětce s plnou barvou

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
