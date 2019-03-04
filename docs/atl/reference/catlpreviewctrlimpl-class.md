---
title: CAtlPreviewCtrlImpl Class
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
ms.openlocfilehash: 71c50771889381ad2288637c23930103b5925a2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283266"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl Class

Tato třída je implementace knihovny ATL okna, které se umístí do hostitelského okna poskytnutého shellem pro náhled ve formátu RTF.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](#dtor)|Destructs objekt ovládacího prvku ve verzi preview.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Vytvoří objekt ovládacího prvku ve verzi preview.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Create](#create)|Volá obslužnou rutinou náhledu k vytvoření okna Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Když je nutné odstranit tento ovládací prvek volány obslužné rutiny náhledu.|
|[CAtlPreviewCtrlImpl::Focus](#focus)|Nastaví vstupní fokus na tento ovládací prvek.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Zpracovává zprávu WM_PAINT.|
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Říká tento ovládací prvek pro překreslení.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Nastaví novou nadřazenou položku pro tento ovládací prvek.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Volá obslužnou rutinou náhledu když je nutné nastavit vizuální znázornění bohaté možnosti ve verzi preview obsahu.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Nastaví nové ohraničující obdélník tohoto ovládacího prvku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Volá se rozhraním vykreslit v náhledu.|

### <a name="protected-constants"></a>Chráněné konstanty

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Písmo použité k zobrazení textu v okně verze preview.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Barva pozadí okno náhledu.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Barva textu okno náhledu.|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpreviewctrlimpl.h

##  <a name="catlpreviewctrlimpl"></a>  CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Vytvoří objekt ovládacího prvku ve verzi preview.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Poznámky

##  <a name="dtor"></a>  CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl

Destructs objekt ovládacího prvku ve verzi preview.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Poznámky

##  <a name="create"></a>  CAtlPreviewCtrlImpl::Create

Volá obslužnou rutinou náhledu k vytvoření okna Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač okna hostitele zadaný shellem pro náhled ve formátu RTF.

*prc*<br/>
Určuje počáteční velikost a pozice okna.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="destroy"></a>  CAtlPreviewCtrlImpl::Destroy

Když je nutné odstranit tento ovládací prvek volány obslužné rutiny náhledu.

```
virtual void Destroy();
```

### <a name="remarks"></a>Poznámky

##  <a name="dopaint"></a>  CAtlPreviewCtrlImpl::DoPaint

Volá se rozhraním vykreslit v náhledu.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parametry

*hdc*<br/>
Popisovač pro kontext zařízení pro kreslení.

### <a name="remarks"></a>Poznámky

##  <a name="focus"></a>  CAtlPreviewCtrlImpl::Focus

Nastaví vstupní fokus na tento ovládací prvek.

```
virtual void Focus();
```

### <a name="remarks"></a>Poznámky

##  <a name="m_clrback"></a>  CAtlPreviewCtrlImpl::m_clrBack

Barva pozadí okno náhledu.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_clrtext"></a>  CAtlPreviewCtrlImpl::m_clrText

Barva textu v okně verze preview.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_plf"></a>  CAtlPreviewCtrlImpl::m_plf

Písmo použité k zobrazení textu v okně verze preview.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Poznámky

##  <a name="onpaint"></a>  CAtlPreviewCtrlImpl::OnPaint

Zpracovává zprávu WM_PAINT.

```
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
Když se tato funkce vrátí, obsahuje hodnotu TRUE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

##  <a name="redraw"></a>  CAtlPreviewCtrlImpl::Redraw

Říká tento ovládací prvek pro překreslení.

```
virtual void Redraw();
```

### <a name="remarks"></a>Poznámky

##  <a name="sethost"></a>  CAtlPreviewCtrlImpl::SetHost

Nastaví novou nadřazenou položku pro tento ovládací prvek.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač do nového nadřazeného okna.

### <a name="remarks"></a>Poznámky

##  <a name="setpreviewvisuals"></a>  CAtlPreviewCtrlImpl::SetPreviewVisuals

Volá obslužnou rutinou náhledu když je nutné nastavit vizuální znázornění bohaté možnosti ve verzi preview obsahu.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parametry

*clrBack*<br/>
Barva pozadí okno náhledu.

*clrText*<br/>
Barva textu v okně verze preview.

*PLF*<br/>
Písmo použité k zobrazení textu v okně verze preview.

### <a name="remarks"></a>Poznámky

##  <a name="setrect"></a>  CAtlPreviewCtrlImpl::SetRect

Nastaví nové ohraničující obdélník tohoto ovládacího prvku.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parametry

*prc*<br/>
Určuje novou velikost a pozice ovládacího prvku ve verzi preview.

*bRedraw*<br/>
Určuje, zda by měl překreslit ovládací prvek.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
