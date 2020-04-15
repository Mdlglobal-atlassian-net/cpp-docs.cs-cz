---
title: Třída COleUpdateDialog
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374840"
---
# <a name="coleupdatedialog-class"></a>Třída COleUpdateDialog

Používá se pro zvláštní případ dialogového okna Ole Upravit odkazy, které by mělo být použito, když potřebujete aktualizovat pouze existující propojené nebo vložené objekty v dokumentu.

## <a name="syntax"></a>Syntaxe

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Vytvoří `COleUpdateDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleUpdateDialog::DoModální](#domodal)|Zobrazí dialogové okno **Upravit vazby** v aktualizačním režimu.|

## <a name="remarks"></a>Poznámky

Další informace týkající se dialogových oken specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

Vytvoří `COleUpdateDialog` objekt.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Odkazuje na dokument obsahující odkazy, které mohou vyžadovat aktualizaci.

*bUpdateOdkazy*<br/>
Příznak, který určuje, zda mají být propojené objekty aktualizovány.

*bUpdateEmbeddings*<br/>
Příznak, který určuje, zda mají být vložené objekty aktualizovány.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud se jedná o hodnotu NULL, bude nadřazené okno dialogového okna nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří `COleUpdateDialog` pouze objekt. Chcete-li zobrazit dialogové okno, volejte [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Tato třída by měla `COleLinksDialog` být použita místo toho, pokud chcete aktualizovat pouze existující propojené nebo vložené položky.

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COleUpdateDialog::DoModální

Zobrazí dialogové okno Upravit vazby v režimu aktualizace.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud dialogové okno vráceno úspěšně.

- IDCANCEL, pokud žádná z propojených nebo vložených položek v aktuálním dokumentu není třeba aktualizovat.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volejte [cOleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v tématu [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Všechny odkazy a/nebo vkládání jsou aktualizovány, pokud uživatel nevybere tlačítko Storno.

## <a name="see-also"></a>Viz také

[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Třída COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)
