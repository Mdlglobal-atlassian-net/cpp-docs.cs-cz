---
title: Třída CBitmapRenderTarget
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
ms.openlocfilehash: 6249c121f7bcca0675a8138baef0e2cdc9e632d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352605"
---
# <a name="cbitmaprendertarget-class"></a>Třída CBitmapRenderTarget

Obálka pro ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Vytvoří objekt CBitmapRenderTarget.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::Připojit](#attach)|Připojí k objektu existující cílové rozhraní vykreslení.|
|[CBitmapRenderTarget::Detach](#detach)|Odpojení vykreslení cílového rozhraní od objektu|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Načte bitmapu pro tento cíl vykreslení. Vrácenou bitmapu lze použít pro operace kreslení.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Vrátí rozhraní ID2D1BitmapRenderTarget.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::operátor ID2D1BitmapRenderTarget*](#operator_id2d1bitmaprendertarget_star)|Vrátí rozhraní ID2D1BitmapRenderTarget.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Ukazatel na objekt ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Cíl CRender](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a>CBitmapRenderTarget::Připojit

Připojí k objektu existující cílové rozhraní vykreslení.

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pCíl*<br/>
Existující rozhraní cíle vykreslení. Nelze získat hodnotu NULL.

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a>CBitmapRenderTarget::CBitmapRenderTarget

Vytvoří objekt CBitmapRenderTarget.

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a>CBitmapRenderTarget::Detach

Odpojení vykreslení cílového rozhraní od objektu

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpojené rozhraní cíle vykreslení.

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a>CBitmapRenderTarget::GetBitmap

Načte bitmapu pro tento cíl vykreslení. Vrácenou bitmapu lze použít pro operace kreslení.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Parametry

*Bitmapové*<br/>
Když tato metoda vrátí, obsahuje platný bitmap pro tento cíl vykreslení. Tuto bitmapu lze použít pro operace kreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a>CBitmapRenderTarget::GetBitmapRenderTarget

Vrátí rozhraní ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapRenderTarget nebo NULL, pokud objekt ještě není inicializován.

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a>CBitmapRenderTarget::m_pBitmapRenderTarget

Ukazatel na objekt ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a>CBitmapRenderTarget::operátor ID2D1BitmapRenderTarget*

Vrátí rozhraní ID2D1BitmapRenderTarget.

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapRenderTarget nebo NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
