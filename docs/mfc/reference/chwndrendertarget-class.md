---
title: CHwndRenderTarget – třída
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
ms.openlocfilehash: 24cf4127c2f429f66143af3a0f49625f23a4e6ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372455"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget – třída

Obálka pro ID2D1HwndRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Vytvoří objekt CHwndRenderTarget z HWND.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CHwndRenderTarget::Připojit](#attach)|Připojí k objektu existující cílové rozhraní vykreslení.|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Označuje, zda hwnd spojené s tímto cílem vykreslení je uzavřen.|
|[CHwndRenderTarget::Vytvořit](#create)|Vytvoří cíl vykreslení přidružený k oknu.|
|[CHwndRenderTarget::Detach](#detach)|Odpojení vykreslení cílového rozhraní od objektu|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Vrátí HWND přidružené k tomuto cíli vykreslení.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Vrátí rozhraní ID2D1HwndRenderTarget.|
|[CHwndRenderTarget::Znovu vytvořit](#recreate)|Znovu vytvoří cíl vykreslení přidružený k oknu.|
|[CHwndRenderTarget::Změna velikosti](#resize)|Změní velikost cíle vykreslení na zadanou velikost obrazového bodu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CHwndRenderTarget::operátor ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|Vrátí rozhraní ID2D1HwndRenderTarget.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Ukazatel na objekt ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Cíl CRender](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRenderTarget::Připojit

Připojí k objektu existující cílové rozhraní vykreslení.

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pCíl*<br/>
Existující rozhraní cíle vykreslení. Nelze získat hodnotu NULL.

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState

Označuje, zda hwnd spojené s tímto cílem vykreslení je uzavřen.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která označuje, zda hwnd spojené s tímto cílem vykreslení je uzavřen.

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget

Vytvoří objekt CHwndRenderTarget z HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
HWND přidružená k tomuto cíli vykreslení

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRenderTarget::Vytvořit

Vytvoří cíl vykreslení přidružený k oknu.

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
HWND přidružená k tomuto cíli vykreslení

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget::Detach

Odpojení vykreslení cílového rozhraní od objektu

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na odpojené rozhraní cíle vykreslení.

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRenderTarget::GetHwnd

Vrátí HWND přidružené k tomuto cíli vykreslení.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Návratová hodnota

HWND přidružené k tomuto cíli vykreslení.

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget

Vrátí rozhraní ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1HwndRenderTarget nebo NULL, pokud objekt ještě není inicializován.

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget

Ukazatel na objekt ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operátor ID2D1HwndRenderTarget*

Vrátí rozhraní ID2D1HwndRenderTarget.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1HwndRenderTarget nebo NULL, pokud objekt ještě není inicializován.

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRenderTarget::Znovu vytvořit

Znovu vytvoří cíl vykreslení přidružený k oknu.

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
HWND přidružená k tomuto cíli vykreslení

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRenderTarget::Změna velikosti

Změní velikost cíle vykreslení na zadanou velikost obrazového bodu.

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Nová velikost cíle vykreslení v pixelech zařízení

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
