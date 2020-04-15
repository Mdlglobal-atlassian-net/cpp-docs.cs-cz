---
title: CMultiPageDHtmlDialog – třída
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319654"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog – třída

Vícestránkové dialogové okno zobrazuje více stránek HTML postupně a zpracovává události z každé stránky.

## <a name="syntax"></a>Syntaxe

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[cMultiPageDhtmlDialog::cMultiPageDhtmlDialog](#cmultipagedhtmldialog)|Vytvoří vícestránkový dialogový objekt DHTML (ve stylu průvodce).|
|[cMultiPageDhtmlDialog::~cMultiPageDhtmlDialog](#_dtorcmultipagedhtmldialog)|Zničí vícestránkový objekt dialogového okna DHTML.|

## <a name="remarks"></a>Poznámky

Mechanismus pro to je [DHTML a URL mapa událostí](dhtml-event-maps.md), která obsahuje vložené mapy událostí pro každou stránku.

## <a name="example"></a>Příklad

Toto vícestránkové dialogové okno předpokládá tři prostředky HTML, které definují jednoduché funkce podobné průvodci. Na první stránce je tlačítko **Další,** druhé tlačítko **Před** a **Další** a třetí tlačítko **Před.** Po stisknutí jednoho z tlačítek zavolá funkce obslužné rutiny [CDHtmlDialog::LoadFromResource,](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) aby načetla příslušnou novou stránku.

Příslušné části deklarace třídy (v cmymultipagedlg.h):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Relevantní části implementace třídy (v CMyMultipageDlg.cpp):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cdhtmldialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>cMultiPageDhtmlDialog::cMultiPageDhtmlDialog

Vytvoří vícestránkový dialogový objekt DHTML (ve stylu průvodce).

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Řetězec s ukončeným hodnotou null, který je názvem prostředku šablony dialogového okna.

*szHtmlResID*<br/>
Řetězec ukončený hodnotou null, který je názvem prostředku HTML.

*pParentWnd*<br/>
Ukazatel na nadřazený objekt okna nebo objekt okna vlastníka (typu [CWnd),](../../mfc/reference/cwnd-class.md)ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

*nIDŠablona*<br/>
Obsahuje id číslo prostředku šablony dialogového okna.

*nHtmlResID*<br/>
Obsahuje id číslo prostředku HTML.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>cMultiPageDhtmlDialog::~cMultiPageDhtmlDialog

Zničí vícestránkový objekt dialogového okna DHTML.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Viz také

[Třída CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
