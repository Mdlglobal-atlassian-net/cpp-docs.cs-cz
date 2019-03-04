---
title: CHtmlEditCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: 6c1447c3157bceb4540007eca5c3eb85e8269bd2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285305"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl Class

Poskytuje funkce pro ovládací prvek WebBrowser ActiveX v okně MFC.

## <a name="syntax"></a>Syntaxe

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Vytvoří `CHtmlEditCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHtmlEditCtrl::Create](#create)|Vytvoří ovládací prvek WebBrowser ActiveX a připojí ho k `CHtmlEditCtrl` objektu. Tato funkce automaticky umístí do režimu úprav ovládacího prvku WebBrowser ActiveX.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Načte [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní na dokument aktuálně načtené obsažený ovládací prvek WebBrowser.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Načte adresu URL pro výchozí dokument k načtení v obsažený ovládací prvek WebBrowser.|

## <a name="remarks"></a>Poznámky

Hostované ovládací prvek WebBrowser, které ovládací prvek automaticky přejde do režimu úprav po jeho vytvoření.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Požadavky

**Header:** afxhtml.h

##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl

Vytvoří `CHtmlEditCtrl` objektu.

```
CHtmlEditCtrl();
```

##  <a name="create"></a>  CHtmlEditCtrl::Create

Vytvoří ovládací prvek WebBrowser ActiveX a připojí ho k `CHtmlEditCtrl` objektu. WebBrowser ActiveX ovládací prvek automaticky přejde na výchozí dokument a pak se umístí do režimu úprav touto funkcí.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszWindowName*<br/>
Tento parametr se nepoužívá.

*dwStyle*<br/>
Tento parametr se nepoužívá.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku.

*pContext*<br/>
Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument

Načte [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní na dokument aktuálně načtené obsažený ovládací prvek WebBrowser

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument*<br/>
Rozhraní dokumentu.

##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument

Načte adresu URL pro výchozí dokument k načtení v obsažený ovládací prvek WebBrowser.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)
