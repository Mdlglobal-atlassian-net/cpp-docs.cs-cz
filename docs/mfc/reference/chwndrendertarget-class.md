---
title: Chwndrendertarget – třída
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: 439ff0152ec69575f21faa332d8fac4bbe779a16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551863"
---
# <a name="chwndrendertarget-class"></a>Chwndrendertarget – třída

Obálka pro ID2D1HwndRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Vytvoří objekt chwndrendertarget – od HWND.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|Bude k obrazci existující vykreslení rozhraní cílového objektu|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Určuje, zda je occluded HWND přidružené k tento cíl vykreslování.|
|[CHwndRenderTarget::Create](#create)|Vytvoří přidružený k oknu cíl vykreslování|
|[CHwndRenderTarget::Detach](#detach)|Odpojí vykreslování cílového rozhraní z objektu|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Vrací HWND přidružený k tomuto cíl vykreslování.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Vrátí ID2D1HwndRenderTarget rozhraní.|
|[CHwndRenderTarget::ReCreate](#recreate)|Znovu vytvoří cíl vykreslování přidružený k oknu|
|[CHwndRenderTarget::Resize](#resize)|Změní velikost cíle vykreslování na velikost zadané pixelů|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|Vrátí ID2D1HwndRenderTarget rozhraní.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Ukazatel na objekt ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Crendertarget –](../../mfc/reference/crendertarget-class.md)

[Chwndrendertarget –](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

Bude k obrazci existující vykreslení rozhraní cílového objektu

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Existující rozhraní cíl vykreslování. Nesmí být NULL.

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

Určuje, zda je occluded HWND přidružené k tento cíl vykreslování.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Návratová hodnota

Je occluded hodnotu určující, zda HWND přidružený k tomuto cíl vykreslování.

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

Vytvoří objekt chwndrendertarget – od HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
HWND přidružený k tomuto cíl vykreslování

##  <a name="create"></a>  CHwndRenderTarget::Create

Vytvoří přidružený k oknu cíl vykreslování

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
HWND přidružený k tomuto cíl vykreslování

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrací FALSE

##  <a name="detach"></a>  CHwndRenderTarget::Detach

Odpojí vykreslování cílového rozhraní z objektu

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpojeném vykreslení cílové rozhraní.

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

Vrací HWND přidružený k tomuto cíl vykreslování.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Návratová hodnota

HWND přidružený k tomuto cíl vykreslování.

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

Vrátí ID2D1HwndRenderTarget rozhraní.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1HwndRenderTarget nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

Ukazatel na objekt ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *

Vrátí ID2D1HwndRenderTarget rozhraní.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1HwndRenderTarget nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

Znovu vytvoří cíl vykreslování přidružený k oknu

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
HWND přidružený k tomuto cíl vykreslování

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="resize"></a>  CHwndRenderTarget::Resize

Změní velikost cíle vykreslování na velikost zadané pixelů

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Nová velikost cíle vykreslování v pixelech zařízení

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
