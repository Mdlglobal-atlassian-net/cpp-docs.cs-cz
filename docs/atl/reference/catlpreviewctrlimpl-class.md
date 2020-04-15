---
title: Třída CAtlPreviewCtrlImpl
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
ms.openlocfilehash: 1ccd01bc4d48dc088538f4799b595cce3fb910ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321359"
---
# <a name="catlpreviewctrlimpl-class"></a>Třída CAtlPreviewCtrlImpl

Tato třída je implementace ATL okna, které je umístěno v okně hostitele poskytované prostředí pro rich preview.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](#dtor)|Zničí objekt ovládacího prvku náhledu.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Vytvoří objekt ovládacího prvku náhledu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Vytvořit](#create)|Volána obslužnou rutinou Rich Preview k vytvoření okna systému Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Volána obslužnou rutinou rich preview, když potřebuje zničit tento ovládací prvek.|
|[CAtlPreviewCtrlImpl::Fokus](#focus)|Nastaví zaostření vstupu na tento ovládací prvek.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Zpracovává zprávu WM_PAINT.|
|[CAtlPreviewCtrlImpl::Překreslit](#redraw)|Říká tento ovládací prvek překreslit.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Nastaví nový nadřazený prvek pro tento ovládací prvek.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Nazývá rich preview obslužné rutiny, když potřebuje nastavit vizuály bohatého obsahu náhledu.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Nastaví nový ohraničovací obdélník pro tento ovládací prvek.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Volat rámci k vykreslení náhledu.|

### <a name="protected-constants"></a>Chráněné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Písmo použité k zobrazení textu v okně náhledu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Barva pozadí okna náhledu.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Barva textu okna náhledu.|

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

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Vytvoří objekt ovládacího prvku náhledu.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl

Zničí objekt ovládacího prvku náhledu.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl::Vytvořit

Volána obslužnou rutinou Rich Preview k vytvoření okna systému Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač do okna hostitele dodané prostředí pro rich preview.

*Člr*<br/>
Určuje počáteční velikost a umístění okna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy

Volána obslužnou rutinou rich preview, když potřebuje zničit tento ovládací prvek.

```
virtual void Destroy();
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint

Volat rámci k vykreslení náhledu.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
Popisovač kontextu zařízení pro malování.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl::Fokus

Nastaví zaostření vstupu na tento ovládací prvek.

```
virtual void Focus();
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack

Barva pozadí okna náhledu.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText

Barva textu okna náhledu.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf

Písmo použité k zobrazení textu v okně náhledu.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint

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
Nastaveno na WM_PAINT.

*wParam*<br/>
Tento parametr není používán.

*Lparam*<br/>
Tento parametr není používán.

*bManipulováno*<br/>
Když se tato funkce vrátí, obsahuje hodnotu TRUE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl::Překreslit

Říká tento ovládací prvek překreslit.

```
virtual void Redraw();
```

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Nastaví nový nadřazený prvek pro tento ovládací prvek.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač do nového nadřazeného okna.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Nazývá rich preview obslužné rutiny, když potřebuje nastavit vizuály bohatého obsahu náhledu.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parametry

*zpět*<br/>
Barva pozadí okna náhledu.

*clrText*<br/>
Barva textu okna náhledu.

*plf*<br/>
Písmo použité k zobrazení textu v okně náhledu.

### <a name="remarks"></a>Poznámky

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

Nastaví nový ohraničovací obdélník pro tento ovládací prvek.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parametry

*Člr*<br/>
Určuje novou velikost a umístění ovládacího prvku náhledu.

*bPřekreslit*<br/>
Určuje, zda má být ovládací prvek překreslen.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
