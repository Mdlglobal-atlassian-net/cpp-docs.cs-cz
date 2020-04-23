---
title: CDCRenderTarget – třída
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 8c07962c017d160cb3ce5841a75f1ae8a8761641
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753391"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget – třída

Obálka pro ID2D1DCRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Vytvoří objekt CDCRenderTarget.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::Připojit](#attach)|Připojí k objektu existující cílové rozhraní vykreslení.|
|[CDCRenderTarget::BindDC](#binddc)|Sváže cíl vykreslení s kontextem zařízení, do kterého vydává příkazy kreslení.|
|[CDCRenderTarget::Vytvořit](#create)|Vytvoří CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Odpojení vykreslení cílového rozhraní od objektu|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Vrátí rozhraní ID2D1DCRenderTarget.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::operátor ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|Vrátí rozhraní ID2D1DCRenderTarget.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Ukazatel na objekt ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Cíl CRender](../../mfc/reference/crendertarget-class.md)

[CÍL CDCRender](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Připojit

Připojí k objektu existující cílové rozhraní vykreslení.

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pCíl*<br/>
Existující rozhraní cíle vykreslení. Nelze získat hodnotu NULL.

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC

Sváže cíl vykreslení s kontextem zařízení, do kterého vydává příkazy kreslení.

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Kontext zařízení, na který cíl vykreslení vydává příkazy kreslení

*Rect*<br/>
Rozměry popisovače kontextu zařízení (HDC), ke kterému je cíl vykreslení vázán

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget

Vytvoří objekt CDCRenderTarget.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Vytvořit

Vytvoří CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parametry

*Rekvizity*<br/>
Režim vykreslování, formát pixelů, možnosti vzdálené komunikace, informace dpi a minimální podpora rozhraní DirectX požadovaná pro vykreslování hardwaru.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach

Odpojení vykreslení cílového rozhraní od objektu

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpojené rozhraní cíle vykreslení.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget

Vrátí rozhraní ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1DCRenderTarget nebo NULL, pokud objekt ještě není inicializován.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget

Ukazatel na objekt ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operátor ID2D1DCRenderTarget*

Vrátí rozhraní ID2D1DCRenderTarget.

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1DCRenderTarget nebo NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
