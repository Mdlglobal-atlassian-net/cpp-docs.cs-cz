---
title: Třída CMFCPreviewCtrlImpl
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
ms.openlocfilehash: 060e601901fa5725d7ca62f244f66784af3dc11d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375340"
---
# <a name="cmfcpreviewctrlimpl-class"></a>Třída CMFCPreviewCtrlImpl

Tato třída implementuje okno, které je umístěno v okně hostitele poskytované prostředí pro rich preview.

## <a name="syntax"></a>Syntaxe

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl](#dtor)|Zničí objekt ovládacího prvku náhledu.|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Vytvoří objekt ovládacího prvku náhledu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Vytvořit](#create)|Přetíženo. Volána obslužnou rutinou Rich Preview k vytvoření okna systému Windows.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Volána obslužnou rutinou rich preview, když potřebuje zničit tento ovládací prvek.|
|[CMFCPreviewCtrlImpl::Fokus](#focus)|Nastaví zaostření vstupu na tento ovládací prvek.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Vrátí dokument připojený k tomuto ovládacímu prvku náhledu.|
|[CMFCPreviewCtrlImpl::Překreslit](#redraw)|Říká tento ovládací prvek překreslit.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Volána obslužnou rutinou náhledu k vytvoření vztahu mezi implementací dokumentu a ovládacím prvkem náhledu.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Nastaví nový nadřazený prvek pro tento ovládací prvek.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Nazývá rich preview obslužné rutiny, když potřebuje nastavit vizuály bohatého obsahu náhledu.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Nastaví nový ohraničovací obdélník pro tento ovládací prvek.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Volat rámci k vykreslení náhledu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Barva pozadí okna náhledu.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Barva textu okna náhledu.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Písmo použité k zobrazení textu v okně náhledu.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Ukazatel na dokument, jehož obsah je zobrazen v ovládacím prvku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Vytvoří objekt ovládacího prvku náhledu.

### <a name="syntax"></a>Syntaxe

CMFCPreviewCtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFCPreviewCtrlImpl::Vytvořit

Přetíženo. Volána obslužnou rutinou Rich Preview k vytvoření okna systému Windows.

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
Popisovač do okna hostitele dodané prostředí pro rich preview.

*Člr*<br/>
Určuje počáteční velikost a umístění okna.

*pKontext*<br/>
Ukazatel na kontext vytvoření.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je vytvoření úspěšné; jinak FALSE.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy

Volána obslužnou rutinou rich preview, když potřebuje zničit tento ovládací prvek.

### <a name="syntax"></a>Syntaxe

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint

Volat rámci k vykreslení náhledu.

### <a name="syntax"></a>Syntaxe

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení pro malování.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFCPreviewCtrlImpl::Fokus

Nastaví zaostření vstupu na tento ovládací prvek.

### <a name="syntax"></a>Syntaxe

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument

Vrátí dokument připojený k tomuto ovládacímu prvku náhledu.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, jehož obsah je zobrazen v ovládacím prvku.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor

Barva pozadí okna náhledu.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor

Barva textu okna náhledu.

### <a name="syntax"></a>Syntaxe

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font Písmo použité k zobrazení textu v okně náhledu.

### <a name="syntax"></a>Syntaxe

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument

Ukazatel na dokument, jehož obsah je zobrazen v ovládacím prvku.

### <a name="syntax"></a>Syntaxe

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFCPreviewCtrlImpl::Překreslit

Říká tento ovládací prvek překreslit.

### <a name="syntax"></a>Syntaxe

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument

Volána obslužnou rutinou náhledu k vytvoření vztahu mezi implementací dokumentu a ovládacím prvkem náhledu.

### <a name="syntax"></a>Syntaxe

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Parametry

*pDokument*<br/>
Ukazatel na implementaci dokumentu.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost

Nastaví nový nadřazený prvek pro tento ovládací prvek.

### <a name="syntax"></a>Syntaxe

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač do nového nadřazeného okna.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals

Nazývá rich preview obslužné rutiny, když potřebuje nastavit vizuály bohatého obsahu náhledu.

### <a name="syntax"></a>Syntaxe

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Parametry

*zpět*<br/>
Barva pozadí okna náhledu.

*clrText*<br/>
Barva textu okna náhledu.

*plf*<br/>
Písmo použité k zobrazení textu v okně náhledu.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect

Nastaví nový ohraničovací obdélník pro tento ovládací prvek.

### <a name="syntax"></a>Syntaxe

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Parametry

*Člr*<br/>
Určuje novou velikost a umístění ovládacího prvku náhledu.

*bPřekreslit*<br/>
Určuje, zda má být ovládací prvek překreslen.

### <a name="remarks"></a>Poznámky

Obvykle nový ohraničovací obdélník je nastavena při velikosti ovládacího prvku hostitele.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl

Zničí objekt ovládacího prvku náhledu.

### <a name="syntax"></a>Syntaxe

```
virtual ~CMFCPreviewCtrlImpl();
```
