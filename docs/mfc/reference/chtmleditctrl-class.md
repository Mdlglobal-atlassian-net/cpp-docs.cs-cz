---
title: Třída CHtmlEditCtrl
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
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366845"
---
# <a name="chtmleditctrl-class"></a>Třída CHtmlEditCtrl

Poskytuje funkce ovládacího prvku ActiveX webového prohlížeče v okně knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Vytvoří `CHtmlEditCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CHtmlEditCtrl::Vytvořit](#create)|Vytvoří ovládací prvek ActiveX webového prohlížeče `CHtmlEditCtrl` a připojí jej k objektu. Tato funkce automaticky přepne ovládací prvek ActiveX webového prohlížeče do režimu úprav.|
|[ChtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Načte rozhraní [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) v dokumentu aktuálně načteném v uzavřeném ovládacím prvku WebBrowser.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Načte adresu URL do výchozího dokumentu, který se načte v obsaženém ovládacím prvku WebBrowser.|

## <a name="remarks"></a>Poznámky

Ovládací prvek hostovaný webový prohlížeč je po vytvoření automaticky uveden do režimu úprav.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl

Vytvoří `CHtmlEditCtrl` objekt.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Vytvořit

Vytvoří ovládací prvek ActiveX webového prohlížeče `CHtmlEditCtrl` a připojí jej k objektu. Ovládací prvek ActiveX webového prohlížeče automaticky přejde na výchozí dokument a touto funkcí se umístí do režimu úprav.

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

*lpszNázev_okna*<br/>
Tento parametr není použit.

*dwStyl*<br/>
Tento parametr není použit.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku.

*pKontext*<br/>
Tento parametr není použit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>ChtmlEditCtrl::GetDHtmlDocument

Načte rozhraní [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) v dokumentu aktuálně načteném v ovládacím prvku Obsažený webový prohlížeč.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parametry

*ppDocument*<br/>
Rozhraní dokumentu.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument

Načte adresu URL do výchozího dokumentu, který se načte v obsaženém ovládacím prvku WebBrowser.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
