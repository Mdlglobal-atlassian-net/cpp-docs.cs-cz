---
title: Třída CHtmlEditView
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 20d4586c1ae45e5f3f56c0adbb1ecb1757084fd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752331"
---
# <a name="chtmleditview-class"></a>Třída CHtmlEditView

Poskytuje funkce platformy pro úpravy webového prohlížeče v kontextu architektury dokumentu a zobrazení knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Vytvoří `CHtmlEditView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHtmlEditView::Vytvořit](#create)|Vytvoří nový objekt okna.|
|[ChtmleditView::GetDHtmlDocument](#getdhtmldocument)|Vrátí `IHTMLDocument2` rozhraní v aktuálním dokumentu.|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Načte název výchozího dokumentu pro toto zobrazení.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxhtml.h

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView

Vytvoří `CHtmlEditView` objekt.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView::Vytvořit

Vytvoří nový objekt okna.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*název lpszClassName*<br/>
Odkazuje na řetězec znaků ukončený nulou, který pojmenovává třídu systému Windows. Název třídy může být libovolný název registrovaný globální funkcí [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) nebo funkcí systému `RegisterClass` Windows. Pokud null, používá předdefinované výchozí [CFrameWnd](../../mfc/reference/cframewnd-class.md) atributy.

*lpszNázev_okna*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null, který představuje název okna.

*dwStyl*<br/>
Určuje atributy stylu okna. Ve výchozím nastavení jsou nastaveny styly WS_VISIBLE a WS_CHILD systému Windows.

*Rect*<br/>
Odkaz na strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) určující velikost a umístění okna. Hodnota *rectDefault* umožňuje systému Windows určit velikost a umístění nového okna.

*pParentWnd*<br/>
Ukazatel na nadřazené okno ovládacího prvku.

*Nid*<br/>
ID číslo zobrazení. Ve výchozím nastavení nastavte AFX_IDW_PANE_FIRST.

*pKontext*<br/>
Ukazatel na [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). Null ve výchozím nastavení.

### <a name="remarks"></a>Poznámky

Tato metoda bude také volat obsažené `Navigate` WebBrowser metodu načíst výchozí dokument (viz [CHtmlEditView::GetStartDocument](#getstartdocument)).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>ChtmleditView::GetDHtmlDocument

Vrátí `IHTMLDocument2` rozhraní v aktuálním dokumentu.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument*<br/>
Rozhraní [IHTMLDocument2.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView::GetStartDocument

Načte název výchozího dokumentu pro toto zobrazení.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Viz také

[HtmlEdit ukázka](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
