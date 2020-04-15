---
title: Třída COleBusyDialog
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
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364244"
---
# <a name="colebusydialog-class"></a>Třída COleBusyDialog

Používá se pro dialogová okna OLE Server Neodpovídá nebo Server busy.

## <a name="syntax"></a>Syntaxe

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Vytvoří `COleBusyDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleBusyDialog::DoModální](#domodal)|Zobrazí dialogové okno Server OLE Server Busy.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Určuje volbu provedenou v dialogovém okně.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu OLEUIBUSY, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li volat `COleBusyDialog` tato dialogová okna, vytvořte objekt třídy. Po `COleBusyDialog` vytvoření objektu můžete použít [m_bz](#m_bz) strukturu k inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. Struktura `m_bz` je typu OLEUIBUSY. Další informace o použití této třídy dialogů naleznete v členské funkci [DoModal.](#domodal)

> [!NOTE]
> Kód kontejneru generovaný průvodcem aplikace používá tuto třídu.

Další informace naleznete v části Struktura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) v sadě Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

Tato funkce pouze `COleBusyDialog` vytvoří objekt.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*htaskBusy*<br/>
Zpracování úlohy serveru, která je zaneprázdněna.

*bNotResponding*<br/>
Pokud true, zavolejte dialogové okno Neodpovídá místo dialogového okna Server Busy. Znění v dialogovém okně Neodpovídá se mírně liší od znění v dialogovém okně Zaneprázdněn serveru a tlačítko Storno je zakázáno.

*dwFlags*<br/>
Příznak vytvoření. Může obsahovat nulu nebo více z následujících hodnot v kombinaci s operátorem BITWISE-OR:

- BZ_DISABLECANCELBUTTON Při volání dialogového okna zakážete tlačítko Storno.

- BZ_DISABLESWITCHTOBUTTON Při volání dialogového okna zakážete tlačítko Přepnout na.

- BZ_DISABLERETRYBUTTON Při volání dialogového okna zakáže tlačítko Opakovat.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogového okna je nastavena na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, volejte [DoModal](#domodal).

Další informace naleznete v části Struktura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) v sadě Windows SDK.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog::DoModální

Volánítéto funkce zobrazí dialogové okno Server OLE Server zaneprázdněn nebo Server neodpovídá.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volání `COleDialog::GetLastError` členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v části [Funkce OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_bz](#m_bz) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí Hodnotu IDOK, můžete volat další členské funkce a načíst nastavení nebo informace, které uživatel zadal do dialogového okna.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

Voláním této funkce získáte typ výběru zvolený uživatelem v dialogovém okně Zaneprázdněn serveru.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ výběru.

### <a name="remarks"></a>Poznámky

Hodnoty vráceného typu `Selection` jsou určeny typem `COleBusyDialog` výčtu deklarovaným ve třídě.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Stručný popis těchto hodnot je následující:

- `COleBusyDialog::switchTo`Tlačítko Přepnout na bylo stisknuto.

- `COleBusyDialog::retry`Bylo stisknuto tlačítko Opakovat.

- `COleBusyDialog::callUnblocked`Volání pro aktivaci serveru je nyní odblokováno.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusyDialog::m_bz

Struktura typu OLEUIBUSY používaná k řízení chování dialogového okna Server Busy.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat přímo nebo prostřednictvím členských funkcí.

Další informace naleznete v části Struktura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
