---
title: COleUpdateDialog – třída
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
ms.openlocfilehash: 150e78b7880a61343db21c3c787ffdd1f0b734a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503172"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog – třída

Používá se pro zvláštní případ dialogového okna upravit odkazy OLE, které by mělo být použito v případě, že v dokumentu potřebujete aktualizovat pouze existující propojené nebo vložené objekty.

## <a name="syntax"></a>Syntaxe

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|`COleUpdateDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Zobrazí dialogové okno **Upravit odkazy** v režimu aktualizace.|

## <a name="remarks"></a>Poznámky

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

`COleUpdateDialog` Vytvoří objekt.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Odkazuje na dokument obsahující odkazy, které mohou být potřeba aktualizovat.

*bUpdateLinks*<br/>
Příznak, který určuje, zda mají být aktualizovány propojené objekty.

*bUpdateEmbeddings*<br/>
Příznak, který určuje, zda se mají aktualizovat vložené objekty.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, nadřazené okno dialogového okna bude nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří pouze `COleUpdateDialog` objekt. Chcete-li zobrazit dialogové okno, zavolejte [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Tato třída by měla být použita místo `COleLinksDialog` toho, když chcete aktualizovat pouze existující propojené nebo vložené položky.

##  <a name="domodal"></a>COleUpdateDialog::D oModal

Zobrazí dialogové okno Upravit odkazy v režimu aktualizace.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně vrátilo.

- IDCANCEL, pokud není potřeba aktualizovat žádnou propojenou nebo vloženou položku v aktuálním dokumentu.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte členskou funkci [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , kde získáte další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OLEUIEDITLINKS](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) .

### <a name="remarks"></a>Poznámky

Všechny odkazy a vložení jsou aktualizovány, pokud uživatel nevybere tlačítko Storno.

## <a name="see-also"></a>Viz také:

[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog – třída](../../mfc/reference/colelinksdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog – třída](../../mfc/reference/colelinksdialog-class.md)
