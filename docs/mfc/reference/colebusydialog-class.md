---
title: Colebusydialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs:
- C++
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d60a86888f601463fa5c2151eb3243c3f55078ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380370"
---
# <a name="colebusydialog-class"></a>Colebusydialog – třída

Používá se pro dialogová okna Server OLE neodpovídá nebo Server je zaneprázdněn.

## <a name="syntax"></a>Syntaxe

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Vytvoří `COleBusyDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE Server je zaneprázdněn.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Určuje volby provedené v dialogovém okně.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu OLEUIBUSY, které ovládá chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu třídy `COleBusyDialog` kdy chcete volat tyto dialogy. Po `COleBusyDialog` objekt byl vytvořen, můžete použít [m_bz](#m_bz) struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_bz` Struktury je typu OLEUIBUSY. Další informace o použití této třídy dialogového okna, najdete v článku [DoModal](#domodal) členskou funkci.

> [!NOTE]
>  Generované průvodcem kontejneru kódu aplikace používá tuto třídu.

Další informace najdete v tématu [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) struktura v sadě Windows SDK.

Další informace o dialogových oken OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

[Coledialog –](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog

Tato funkce vytvoří pouze `COleBusyDialog` objektu.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*htaskBusy*<br/>
Zpracování úkolu serveru, který je zaneprázdněný.

*bNotResponding*<br/>
Při hodnotě TRUE se volejte bez Serverbusy dialogu dialogové okno neodpovídá. Text v dialogovém okně neodpovídá se trochu liší od formulace v dialogovém okně Serverbusy a je zakázáno na tlačítko Storno.

*dwFlags*<br/>
Vytvoření příznak. Může obsahovat nula nebo více z následujících hodnot kombinované pomocí bitového operátoru OR – operátor:

- Při volání metody dialogových oken, zakažte BZ_DISABLECANCELBUTTON tlačítko Storno.

- BZ_DISABLESWITCHTOBUTTON zakázat tlačítko Přepnout při volání metody dialogových oken.

- BZ_DISABLERETRYBUTTON zakázat tlačítko opakování při volání metody dialogových oken.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nadřazené okno z objektu dialogového okna je nastaveno na hlavního okna aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal).

Další informace najdete v tématu [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) struktura v sadě Windows SDK.

##  <a name="domodal"></a>  COleBusyDialog::DoModal

Voláním této funkce k zobrazení dialogových oken OLE zaneprázdněný Server nebo Server neodpovídá.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení pro dialogové okno. Jeden z následujících hodnot:

- IDOK, pokud úspěšně zobrazí dialogové okno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte `COleDialog::GetLastError` členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIBusy](/windows/desktop/api/oledlg/nf-oledlg-oleuibusya) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_bz](#m_bz) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat ostatní členské funkce k načtení nastavení nebo informace, které se vstup uživatelem do dialogových oken.

##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType

Voláním této funkce se získat typ výběru uživatelem v dialogovém okně Server je zaneprázdněn.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ výběru.

### <a name="remarks"></a>Poznámky

Typ vrácené hodnoty jsou určeny `Selection` typ výčtu deklarovaný v `COleBusyDialog` třídy.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Postupujte podle stručný popis těchto hodnot:

- `COleBusyDialog::switchTo` Stisknutí tlačítka Přepnout.

- `COleBusyDialog::retry` Klepnutí na tlačítko Opakovat.

- `COleBusyDialog::callUnblocked` Volání k aktivaci serveru je nyní odblokované.

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

Struktura typu OLEUIBUSY používat k ovládání chování Serverbusy dialogového okna.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Poznámky

Přímo nebo prostřednictvím členské funkce, lze upravit členy této struktury.

Další informace najdete v tématu [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) struktura v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
