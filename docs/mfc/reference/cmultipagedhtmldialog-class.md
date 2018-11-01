---
title: Cmultipagedhtmldialog – třída
ms.date: 11/04/2016
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 680c485241b7a377d1c6f0ec2785dbbade01ed3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443548"
---
# <a name="cmultipagedhtmldialog-class"></a>Cmultipagedhtmldialog – třída

Vícestránkové dialogové okno zobrazí postupně několik stránek HTML a zpracovává události z každé stránky.

## <a name="syntax"></a>Syntaxe

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Vytvoří vícestránkové dialogové okno objekt DHTML (Průvodce style).|
|[Cmultipagedhtmldialog –:: ~ cmultipagedhtmldialog –](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Odstraní objekt vícestránkové dialogové okno DHTML.|

## <a name="remarks"></a>Poznámky

Mechanismus pro to je [DHTML a adresu URL mapa událostí](dhtml-event-maps.md), který obsahuje vložené mapy událostí pro každou stránku.

## <a name="example"></a>Příklad

Toto vícestránkové dialogové okno předpokládá tři zdroje HTML, které definují jednoduché funkce průvodce. První stránka má **Další** tlačítko, druhý **předchozí** a **Další** tlačítko a třetí **předchozí** tlačítko. Když se stiskne některého tlačítka, volá funkci obslužné rutiny [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) načíst příslušnou novou stránku.

Relevantní části deklaraci třídy (v CMyMultiPageDlg.h):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Relevantní části implementace třídy (v CMyMultipageDlg.cpp):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Vytvoří vícestránkové dialogové okno objekt DHTML (Průvodce style).

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
Řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*szHtmlResID*<br/>
Řetězec zakončený hodnotou null, který je název prostředku HTML.

*pParentWnd*<br/>
Ukazatel na objekt okna nadřazené nebo vlastník (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

*nHtmlResID*<br/>
Obsahuje identifikační číslo prostředku HTML.

##  <a name="_dtorcmultipagedhtmldialog"></a>  Cmultipagedhtmldialog –:: ~ cmultipagedhtmldialog –

Odstraní objekt vícestránkové dialogové okno DHTML.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Viz také

[CDHtmlDialog – třída](../../mfc/reference/cdhtmldialog-class.md)
