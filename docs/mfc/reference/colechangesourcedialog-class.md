---
title: Třída COleChangeSourceDialog
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321875"
---
# <a name="colechangesourcedialog-class"></a>Třída COleChangeSourceDialog

Používá se pro dialogové okno Změnit zdroj OLE.

## <a name="syntax"></a>Syntaxe

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Vytvoří `COleChangeSourceDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::DoModální](#domodal)|Zobrazí dialogové okno Změnit zdroj OLE.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Získá úplný zdrojový zobrazovaný název.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Získá název souboru ze zdrojového názvu.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Získá předponu předchozího zdroje.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Získá název položky ze zdrojového názvu.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Získá předponu nového zdroje|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Označuje, zda je zdroj platný.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li volat `COleChangeSourceDialog` toto dialogové okno, vytvořte objekt třídy. Po `COleChangeSourceDialog` vytvoření objektu můžete použít [m_cs](#m_cs) strukturu k inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. Struktura `m_cs` je typu [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Další informace o použití této třídy dialogů naleznete v členské funkci [DoModal.](#domodal)

Další informace naleznete v [oleuiCHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury v systému Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Tato funkce vytvoří `COleChangeSourceDialog` objekt.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na propojené [COleClientItem,](../../mfc/reference/coleclientitem-class.md) jehož zdroj má být aktualizován.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud se jedná o hodnotu NULL, bude nadřazené okno dialogového okna nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal.](#domodal)

Další informace naleznete v [oleuichangesource](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury a [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) funkce v systému Windows SDK.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChangeSourceDialog::DoModální

Voláním této funkce zobrazíte dialogové okno Změnit zdroj OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volejte [cOleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v části [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_cs](#m_cs) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí hodnotu IDOK, můžete volat členské funkce a načíst z dialogového okna nastavení nebo informace zadané uživatelem. Následující seznam pojmenuje typické funkce dotazu:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChangeSourceDialog::GetDisplayName

Volání této funkce načíst úplný zobrazovaný název pro propojenou položku klienta.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Návratová hodnota

Úplný zdrojový zobrazovaný název (zástupný název) pro [cOleClientItem](../../mfc/reference/coleclientitem-class.md) zadaný v konstruktoru.

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChangeSourceDialog::GetFileName

Volání této funkce načíst zástupný název souboru část zobrazovaného názvu pro propojené položky klienta.

```
CString GetFileName();
```

### <a name="return-value"></a>Návratová hodnota

Část zástupného názvu souboru zdrojového zobrazovaného názvu [položky COleClientItem](../../mfc/reference/coleclientitem-class.md) zadané v konstruktoru.

### <a name="remarks"></a>Poznámky

Zástupný název souboru spolu s zástupným názvem položky poskytuje úplný zobrazovaný název.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Volání této funkce získat předchozí řetězec předpony pro zdroj.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí řetězec předpony zdroje.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze po [DoModal](#domodal) vrátí IDOK.

Tato hodnota pochází `lpszFrom` přímo z člena struktury [OLEUICHANGESOURCE.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Další informace naleznete v [oleuiCHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury v systému Windows SDK.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChangeSourceDialog::GetItemName

Volání této funkce načíst zástupný název položky zobrazovaného názvu pro propojenou položku klienta.

```
CString GetItemName();
```

### <a name="return-value"></a>Návratová hodnota

Část skupiny položek zdrojového zobrazovaného názvu [položky COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaná v konstruktoru.

### <a name="remarks"></a>Poznámky

Zástupný název souboru spolu s zástupným názvem položky poskytuje úplný zobrazovaný název.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Volání této funkce získat nový řetězec předpony pro zdroj.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Návratová hodnota

Nový řetězec předpony zdroje.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze po [DoModal](#domodal) vrátí IDOK.

Tato hodnota pochází `lpszTo` přímo z člena struktury [OLEUICHANGESOURCE.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Další informace naleznete v [oleuiCHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury v systému Windows SDK.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChangeSourceDialog::m_cs

Tento datový člen je struktura typu [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Poznámky

`OLEUICHANGESOURCE`slouží k řízení chování dialogového okna Zdroj změny OLE. Členy této struktury lze upravovat přímo.

Další informace naleznete v [oleuiCHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury v systému Windows SDK.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

Volání této funkce k určení, zda je platný nový zdroj.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je nový zdroj platný, jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze po [DoModal](#domodal) vrátí IDOK.

Další informace naleznete v [oleuiCHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury v systému Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
