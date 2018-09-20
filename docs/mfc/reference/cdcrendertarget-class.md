---
title: Cdcrendertarget – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc5903f50136aaffcb0358e1a60c99a71e67540e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447125"
---
# <a name="cdcrendertarget-class"></a>Cdcrendertarget – třída

Obálka pro ID2D1DCRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Vytvoří objekt cdcrendertarget –.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::Attach](#attach)|Bude k obrazci existující vykreslení rozhraní cílového objektu|
|[CDCRenderTarget::BindDC](#binddc)|Vytvoří vazbu cíle vykreslování do kontextu zařízení, na který vystavuje příkazy pro kreslení|
|[CDCRenderTarget::Create](#create)|Vytvoří cdcrendertarget –.|
|[CDCRenderTarget::Detach](#detach)|Odpojí vykreslování cílového rozhraní z objektu|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Vrátí ID2D1DCRenderTarget rozhraní|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Vrátí ID2D1DCRenderTarget rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Ukazatel na objekt ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Crendertarget –](../../mfc/reference/crendertarget-class.md)

[Cdcrendertarget –](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="attach"></a>  CDCRenderTarget::Attach

Bude k obrazci existující vykreslení rozhraní cílového objektu

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Existující rozhraní cíl vykreslování. Nesmí být NULL.

##  <a name="binddc"></a>  CDCRenderTarget::BindDC

Vytvoří vazbu cíle vykreslování do kontextu zařízení, na který vystavuje příkazy pro kreslení

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*řadič domény*<br/>
Kontext zařízení, ke kterému cíle vykreslování vysílá příkazy vykreslování

*Rect*<br/>
Dimenze popisovač kontextu zařízení (HDC), ke kterému je vázán cíle vykreslování

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget

Vytvoří objekt cdcrendertarget –.

```
CDCRenderTarget();
```

##  <a name="create"></a>  CDCRenderTarget::Create

Vytvoří cdcrendertarget –.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parametry

*Vlastnosti*<br/>
Režim vykreslování, formát pixelu, možnosti vzdálené komunikace, informace DPI a minimální podporu rozhraní DirectX vyžadované pro vykreslení hardwaru.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="detach"></a>  CDCRenderTarget::Detach

Odpojí vykreslování cílového rozhraní z objektu

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpojeném vykreslení cílové rozhraní.

##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget

Vrátí ID2D1DCRenderTarget rozhraní

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1DCRenderTarget nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget

Ukazatel na objekt ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget *

Vrátí ID2D1DCRenderTarget rozhraní

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1DCRenderTarget nebo hodnota NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
