---
title: Třída COleLinksDialog
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
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374937"
---
# <a name="colelinksdialog-class"></a>Třída COleLinksDialog

Používá se pro dialogové okno Ole Upravit vazby.

## <a name="syntax"></a>Syntaxe

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Vytvoří `COleLinksDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleLinksDialog::DoModální](#domodal)|Zobrazí dialogové okno Ole Upravit vazby.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Struktura typu OLEUIEDITLINKS, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li volat `COleLinksDialog` toto dialogové okno, vytvořte objekt třídy. Po `COleLinksDialog` vytvoření objektu můžete použít [m_el](#m_el) strukturu k inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. Struktura `m_el` je typu OLEUIEDITLINKS. Další informace o použití této třídy dialogů naleznete v členské funkci [DoModal.](#domodal)

> [!NOTE]
> Kód kontejneru generovaný průvodcem aplikace používá tuto třídu.

Další informace naleznete v [oleuiEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) struktury v sadě Windows SDK.

Další informace týkající se dialogových oken specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinksDialog::DoModální

Zobrazí dialogové okno Ole Upravit vazby.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volání `COleDialog::GetLastError` členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v tématu [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_el](#m_el) struktury, měli byste to udělat před voláním , ale po vytvoření objektu dialogového okna.

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

Vytvoří `COleLinksDialog` objekt.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Odkazuje na dokument OLE, který obsahuje odkazy, které mají být upraveny.

*pZobrazit*<br/>
Ukazuje na aktuální zobrazení na *pDoc*.

*dwFlags*<br/>
Vytvoření příznak, který obsahuje buď 0 nebo ELF_SHOWHELP k určení, zda se zobrazí tlačítko nápovědy při zobrazení dialogového okna.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno dialogového okna je nastavena na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří `COleLinksDialog` pouze objekt. Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal.](#domodal)

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinksDialog::m_el

Struktura typu OLEUIEDITLINKS používaná k řízení chování dialogového okna Upravit vazby.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravit přímo nebo prostřednictvím členských funkcí.

Další informace naleznete v [oleuiEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) struktury v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
