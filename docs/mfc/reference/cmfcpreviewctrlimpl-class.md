---
title: CMFCPreviewCtrlImpl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: f66ed8478023bd42e185da4f21740d1de2536140
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295744"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl Class

Tato třída implementuje okno, které se umístí do hostitelského okna poskytnutého shellem pro náhled ve formátu RTF.

## <a name="syntax"></a>Syntaxe

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl](#dtor)|Destructs objekt ovládacího prvku ve verzi preview.|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Vytvoří objekt ovládacího prvku ve verzi preview.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Create](#create)|Přetíženo. Volá obslužnou rutinou náhledu k vytvoření okna Windows.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Když je nutné odstranit tento ovládací prvek volány obslužné rutiny náhledu.|
|[CMFCPreviewCtrlImpl::Focus](#focus)|Nastaví vstupní fokus na tento ovládací prvek.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Vrátí dokument připojené na tento ovládací prvek ve verzi preview.|
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Říká tento ovládací prvek pro překreslení.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Volá obslužnou rutinou ve verzi preview k vytvoření vztahu mezi implementace dokumentu a ovládací prvek náhledu.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Nastaví novou nadřazenou položku pro tento ovládací prvek.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Volá obslužnou rutinou náhledu když je nutné nastavit vizuální znázornění bohaté možnosti ve verzi preview obsahu.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Nastaví nové ohraničující obdélník tohoto ovládacího prvku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Volá se rozhraním vykreslit v náhledu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Barva pozadí okno náhledu.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Barva textu okno náhledu.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Písmo použité k zobrazení textu v okně verze preview.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Ukazatel na dokument, jejíž obsah je zobrazen v ovládacím prvku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Vytvoří objekt ovládacího prvku ve verzi preview.

### <a name="syntax"></a>Syntaxe

CMFCPreviewCtrlImpl();

## <a name="create"></a> CMFCPreviewCtrlImpl::Create

Přetíženo. Volá obslužnou rutinou náhledu k vytvoření okna Windows.

### <a name="syntax"></a>Syntaxe

```
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc
);
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc,
   CCreateContext* pContext
);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač okna hostitele zadaný shellem pro náhled ve formátu RTF.

*prc*<br/>
Určuje počáteční velikost a pozice okna.

*pContext*<br/>
Ukazatel na vytvoření kontextu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla úspěšně vytvořena; v opačném případě FALSE.

## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy

Když je nutné odstranit tento ovládací prvek volány obslužné rutiny náhledu.

### <a name="syntax"></a>Syntaxe

```
virtual void Destroy();
```

## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint

Volá se rozhraním vykreslit v náhledu.

### <a name="syntax"></a>Syntaxe

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení pro kreslení.

## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus

Nastaví vstupní fokus na tento ovládací prvek.

### <a name="syntax"></a>Syntaxe

```
virtual void Focus();
```

## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument

Vrátí dokument připojené na tento ovládací prvek ve verzi preview.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, jejíž obsah je zobrazen v ovládacím prvku.

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor

Barva pozadí okno náhledu.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrBackColor;
```

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor

Barva textu v okně verze preview.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrTextColor;
```

## <a name="m_font"></a> CMFCPreviewCtrlImpl::m_font písmo použité k zobrazení textu v okně verze preview.

### <a name="syntax"></a>Syntaxe

```
CFont m_font;
```

## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument

Ukazatel na dokument, jejíž obsah je zobrazen v ovládacím prvku.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* m_pDocument;
```

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw

Říká tento ovládací prvek pro překreslení.

### <a name="syntax"></a>Syntaxe

```
virtual void Redraw();
```

## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument

Volá obslužnou rutinou ve verzi preview k vytvoření vztahu mezi implementace dokumentu a ovládací prvek náhledu.

### <a name="syntax"></a>Syntaxe

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Parametry

*pDocument*<br/>
Ukazatel na implementaci dokumentu.

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost

Nastaví novou nadřazenou položku pro tento ovládací prvek.

### <a name="syntax"></a>Syntaxe

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač do nového nadřazeného okna.

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals

Volá obslužnou rutinou náhledu když je nutné nastavit vizuální znázornění bohaté možnosti ve verzi preview obsahu.

### <a name="syntax"></a>Syntaxe

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Parametry

*clrBack*<br/>
Barva pozadí okno náhledu.

*clrText*<br/>
Barva textu okno náhledu.

*PLF*<br/>
Písmo použité k zobrazení textu v okně verze preview.

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect

Nastaví nové ohraničující obdélník tohoto ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Parametry

*prc*<br/>
Určuje novou velikost a pozice ovládacího prvku ve verzi preview.

*bRedraw*<br/>
Určuje, zda by měl překreslit ovládací prvek.

### <a name="remarks"></a>Poznámky

Při změně velikosti hostitelský ovládací prvek je obvykle nastavena nové ohraničující obdélník.

## <a name="dtor"></a> CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl

Destructs objekt ovládacího prvku ve verzi preview.

### <a name="syntax"></a>Syntaxe

```
virtual ~CMFCPreviewCtrlImpl();
```
