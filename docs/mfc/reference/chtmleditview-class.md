---
title: CHtmlEditView – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c79991b22814140f93672dca2e1a92938aabdac8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399147"
---
# <a name="chtmleditview-class"></a>CHtmlEditView – třída

Poskytuje funkce úprav platformy WebBrowser v rámci kontextu architektury dokumentu/zobrazení MFC.

## <a name="syntax"></a>Syntaxe

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Vytvoří `CHtmlEditView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHtmlEditView::Create](#create)|Vytvoří nový objekt okna.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Vrátí `IHTMLDocument2` rozhraní pro aktuální dokument.|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Načte název výchozího dokumentu pro toto zobrazení.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cscrollview –](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[Chtmleditctrlbase –](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView –](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxhtml.h

##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView

Vytvoří `CHtmlEditView` objektu.

```
CHtmlEditView();
```

##  <a name="create"></a>  CHtmlEditView::Create

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

*lpszClassName*<br/>
Odkazuje na řetězec znaků zakončené znakem null, která pojmenuje třídu Windows. Název třídy může být jakýkoli název zaregistrované [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce nebo `RegisterClass` funkce Windows. Pokud má hodnotu NULL, používá předdefinované výchozí [CFrameWnd](../../mfc/reference/cframewnd-class.md) atributy.

*lpszWindowName*<br/>
Odkazuje na řetězec znaků zakončené znakem null představující název okna.

*dwStyle*<br/>
Určuje atributy stylu okna. Ve výchozím nastavení jsou nastavené styly WS_VISIBLE a WS_CHILD Windows.

*Rect*<br/>
Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující velikost a umístění okna. *RectDefault* hodnota umožňuje určit velikost a umístění nového okna Windows.

*pParentWnd*<br/>
Ukazatel na nadřazené okno ovládacího prvku.

*nID*<br/>
Číslo ID zobrazení. Ve výchozím nastavení AFX_IDW_PANE_FIRST.

*pContext*<br/>
Ukazatel [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md). Ve výchozím nastavení s hodnotou NULL.

### <a name="remarks"></a>Poznámky

Tato metoda také bude volat obsažený ovládací prvek WebBrowser `Navigate` metoda načíst výchozí dokument (viz [CHtmlEditView::GetStartDocument](#getstartdocument)).

##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument

Vrátí `IHTMLDocument2` rozhraní pro aktuální dokument.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument*<br/>
[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní.

##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument

Načte název výchozího dokumentu pro toto zobrazení.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Viz také

[Ukázka HTMLEdit](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)


