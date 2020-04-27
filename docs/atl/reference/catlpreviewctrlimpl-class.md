---
title: CAtlPreviewCtrlImpl – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: fd94d0d6fe43d80b45def3f747c7b7d558de31d4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167874"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl – třída

Tato třída je implementací okna ATL okna, které je umístěno v hostitelském okně poskytnutém prostředím pro bohatou verzi Preview.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destrukturuje objekt ovládacího prvku náhledu.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Vytvoří objekt ovládacího prvku náhledu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: Create](#create)|Volá se obslužnou rutinou s bohatou funkcí Preview, která vytvoří okno Windows.|
|[CAtlPreviewCtrlImpl::D estroy](#destroy)|Volána obslužnou rutinou s bohatou funkcí ve verzi Preview, pokud je potřeba zničit tento ovládací prvek.|
|[CAtlPreviewCtrlImpl:: Focus](#focus)|Nastaví fokus vstupu na tento ovládací prvek.|
|[CAtlPreviewCtrlImpl:: propaintt](#onpaint)|Zpracovává zprávu WM_PAINT.|
|[CAtlPreviewCtrlImpl:: redraw](#redraw)|Informuje tento ovládací prvek o překreslení.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Nastaví novou nadřazenou položku pro tento ovládací prvek.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Volá se obslužnou rutinou s bohatou sadou funkcí v případě, že potřebuje nastavovat vizuály obsahu s bohatou náhledovou verzí.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Nastaví nový ohraničující obdélník pro tento ovládací prvek.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::D oPaint](#dopaint)|Volá se rozhraním, aby se vykreslila verze Preview.|

### <a name="protected-constants"></a>Chráněné konstanty

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: m_plf](#m_plf)|Písmo použité k zobrazení textu v okně náhledu|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: m_clrBack](#m_clrback)|Barva pozadí okna náhledu|
|[CAtlPreviewCtrlImpl:: m_clrText](#m_clrtext)|Barva textu okna náhledu|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL:: CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpreviewctrlimpl. h

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Vytvoří objekt ovládacího prvku náhledu.

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl

Destrukturuje objekt ovládacího prvku náhledu.

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl:: Create

Volá se obslužnou rutinou s bohatou funkcí Preview, která vytvoří okno Windows.

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač hostitelského okna poskytovaného prostředím pro bohatou verzi Preview.

*ČLR*<br/>
Určuje počáteční velikost a polohu okna.

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::D estroy

Volána obslužnou rutinou s bohatou funkcí ve verzi Preview, pokud je potřeba zničit tento ovládací prvek.

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::D oPaint

Volá se rozhraním, aby se vykreslila verze Preview.

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parametry

*HDC*<br/>
Popisovač kontextu zařízení pro vykreslování.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl:: Focus

Nastaví fokus vstupu na tento ovládací prvek.

```cpp
virtual void Focus();
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl:: m_clrBack

Barva pozadí okna náhledu

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl:: m_clrText

Barva textu okna náhledu

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl:: m_plf

Písmo použité k zobrazení textu v okně náhledu

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl:: propaintt

Zpracovává zprávu WM_PAINT.

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Nastavte na WM_PAINT.

*wParam*<br/>
Tento parametr není používán.

*lParam*<br/>
Tento parametr není používán.

*bHandled*<br/>
Když tato funkce vrátí, obsahuje hodnotu TRUE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl:: redraw

Informuje tento ovládací prvek o překreslení.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Nastaví novou nadřazenou položku pro tento ovládací prvek.

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač nového nadřazeného okna.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Volá se obslužnou rutinou s bohatou sadou funkcí v případě, že potřebuje nastavovat vizuály obsahu s bohatou náhledovou verzí.

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parametry

*clrBack*<br/>
Barva pozadí okna náhledu

*clrText*<br/>
Barva textu okna náhledu

*plf*<br/>
Písmo použité k zobrazení textu v okně náhledu

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

Nastaví nový ohraničující obdélník pro tento ovládací prvek.

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parametry

*ČLR*<br/>
Určuje novou velikost a polohu ovládacího prvku náhledu.

*bRedraw*<br/>
Určuje, zda má být ovládací prvek překreslen.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
