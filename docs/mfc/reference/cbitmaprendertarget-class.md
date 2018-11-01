---
title: Cbitmaprendertarget – třída
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: ffead8d1f4a903fba79e4b22eefbf0a2955f56fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562237"
---
# <a name="cbitmaprendertarget-class"></a>Cbitmaprendertarget – třída

Obálka pro ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Vytvoří objekt cbitmaprendertarget –.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|Bude k obrazci existující vykreslení rozhraní cílového objektu|
|[CBitmapRenderTarget::Detach](#detach)|Odpojí vykreslování cílového rozhraní z objektu|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Načte rastrový obrázek pro tento cíl vykreslování. Vrácené rastrového obrázku je možné pro vykreslení operace.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Vrátí ID2D1BitmapRenderTarget rozhraní|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|Vrátí ID2D1BitmapRenderTarget rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Ukazatel na objekt ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Crendertarget –](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="attach"></a>  CBitmapRenderTarget::Attach

Bude k obrazci existující vykreslení rozhraní cílového objektu

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Existující rozhraní cíl vykreslování. Nesmí být NULL.

##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget

Vytvoří objekt cbitmaprendertarget –.

```
CBitmapRenderTarget();
```

##  <a name="detach"></a>  CBitmapRenderTarget::Detach

Odpojí vykreslování cílového rozhraní z objektu

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpojeném vykreslení cílové rozhraní.

##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap

Načte rastrový obrázek pro tento cíl vykreslování. Vrácené rastrového obrázku je možné pro vykreslení operace.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Parametry

*Rastrový obrázek*<br/>
Po návratu metody obsahuje platný rastrový obrázek pro tento cíl vykreslování. Tento rastrový obrázek slouží pro vykreslení operace.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget

Vrátí ID2D1BitmapRenderTarget rozhraní

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapRenderTarget nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget

Ukazatel na objekt ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *

Vrátí ID2D1BitmapRenderTarget rozhraní

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapRenderTarget nebo hodnota NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
