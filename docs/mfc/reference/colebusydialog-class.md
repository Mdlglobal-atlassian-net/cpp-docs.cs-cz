---
title: COleBusyDialog Class
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: aa3f0d85bcbf34d325125187b22b38c4da01fb43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504396"
---
# <a name="colebusydialog-class"></a>COleBusyDialog Class

Používá se pro dialogová okna Server OLE neodpovídá nebo server je zaneprázdněn.

## <a name="syntax"></a>Syntaxe

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|`COleBusyDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|Zobrazí dialogové okno zaneprázdněný serverem OLE.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Určuje volbu vytvořenou v dialogovém okně.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu OLEUIBUSY, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvořte objekt třídy `COleBusyDialog` , pokud chcete volat Tato dialogová okna. Po vytvoření `COleBusyDialog` objektu lze pomocí struktury [m_bz](#m_bz) inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_bz` Struktura je typu OLEUIBUSY. Další informace o použití této třídy dialogového okna naleznete v tématu členská funkce [DoModal](#domodal) .

> [!NOTE]
>  Kód kontejneru generovaný průvodcem aplikací používá tuto třídu.

Další informace najdete v tématu struktura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) v Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog

Tato funkce vytvoří `COleBusyDialog` pouze objekt.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*htaskBusy*<br/>
Zpracujte úlohu serveru, která je zaneprázdněna.

*bNotResponding*<br/>
Je-li nastavena hodnota TRUE, zavolejte dialogové okno nereaguje, nikoli dialogové okno zaneprázdněný serverem. Formulace v dialogovém okně nereaguje se mírně liší od slov v dialogovém okně zaneprázdněný serverem a tlačítko Zrušit je zakázané.

*dwFlags*<br/>
Příznak vytvoření Může obsahovat nula nebo více z následujících hodnot v kombinaci s bitovým operátorem OR:

- BZ_DISABLECANCELBUTTON zakáže tlačítko zrušit při volání dialogového okna.

- BZ_DISABLESWITCHTOBUTTON při volání dialogového okna zakáže tlačítko Přepnout na.

- BZ_DISABLERETRYBUTTON zakáže tlačítko Opakovat při volání dialogového okna.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud je hodnota NULL, nadřazené okno objektu dialogového okna je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal).

Další informace najdete v tématu struktura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) v Windows SDK.

##  <a name="domodal"></a>  COleBusyDialog::DoModal

Voláním této funkce zobrazíte dialogové okno zaneprázdněný serverem OLE nebo server neodpovídá.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte `COleDialog::GetLastError` členskou funkci pro získání dalších informací o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OLEUIBUSY](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) .

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_bz](#m_bz) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete zavolat jiné členské funkce a načíst tak nastavení nebo informace, které uživatel zadal, do dialogového okna.

##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

Voláním této funkce získáte typ výběru vybraný uživatelem v dialogovém okně zaneprázdněný serverem.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ provedeného výběru.

### <a name="remarks"></a>Poznámky

Hodnoty návratového typu jsou určeny `Selection` výčtovým typem deklarovaným `COleBusyDialog` ve třídě.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Stručný popis těchto hodnot je následující:

- `COleBusyDialog::switchTo`Byl stisknut přepínač na tlačítko.

- `COleBusyDialog::retry`Bylo stisknuto tlačítko Opakovat.

- `COleBusyDialog::callUnblocked`Volání aktivace serveru je nyní odblokováno.

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

Struktura typu OLEUIBUSY slouží k řízení chování dialogového okna zaneprázdněno serverem.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat přímo nebo prostřednictvím členských funkcí.

Další informace najdete v tématu struktura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) v Windows SDK.

## <a name="see-also"></a>Viz také:

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
