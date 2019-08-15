---
title: COleLinksDialog – třída
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: 911108f9a231b752790abfdf86d1b4042d30b149
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504111"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog – třída

Používá se pro dialogové okno Upravit odkazy OLE.

## <a name="syntax"></a>Syntaxe

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|`COleLinksDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|Zobrazí dialogové okno Upravit odkazy OLE.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Struktura typu OLEUIEDITLINKS, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvořte objekt třídy `COleLinksDialog` , pokud chcete zavolat toto dialogové okno. Po vytvoření `COleLinksDialog` objektu lze pomocí struktury [m_el](#m_el) inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_el` Struktura je typu OLEUIEDITLINKS. Další informace o použití této třídy dialogového okna naleznete v tématu členská funkce [DoModal](#domodal) .

> [!NOTE]
>  Kód kontejneru generovaný průvodcem aplikací používá tuto třídu.

Další informace najdete v tématu struktura [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) v Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="domodal"></a>COleLinksDialog::D oModal

Zobrazí dialogové okno Upravit odkazy OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte `COleDialog::GetLastError` členskou funkci pro získání dalších informací o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OLEUIEDITLINKS](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) .

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_el](#m_el) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

`COleLinksDialog` Vytvoří objekt.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Odkazuje na dokument OLE, který obsahuje odkazy, které chcete upravit.

*pView*<br/>
Odkazuje na aktuální zobrazení v *pDoc*.

*dwFlags*<br/>
Příznak vytvoření, který obsahuje hodnotu 0 nebo ELF_SHOWHELP, chcete-li určit, zda bude tlačítko Help zobrazeno při zobrazení dialogového okna.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, nadřazené okno dialogového okna je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří pouze `COleLinksDialog` objekt. Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal](#domodal) .

##  <a name="m_el"></a>COleLinksDialog::m_el

Struktura typu OLEUIEDITLINKS slouží k řízení chování dialogového okna upravit odkazy.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat buď přímo, nebo prostřednictvím členských funkcí.

Další informace najdete v tématu struktura [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) v Windows SDK.

## <a name="see-also"></a>Viz také:

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
