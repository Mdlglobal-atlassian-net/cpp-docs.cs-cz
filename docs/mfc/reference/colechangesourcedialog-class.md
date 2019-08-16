---
title: COleChangeSourceDialog Class
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
ms.openlocfilehash: 239d7eed89796f414a7665b203ca50fafec51277
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504388"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog Class

Používá se pro dialogové okno Změnit zdroj OLE.

## <a name="syntax"></a>Syntaxe

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|`COleChangeSourceDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Zobrazí dialogové okno Změnit zdroj OLE.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Získá úplný zobrazovaný název zdroje.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Získá název souboru ze zdrojového názvu.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Získá předponu předchozího zdroje.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Získá název položky ze zdrojového názvu.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Získá předponu nového zdroje.|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Určuje, zda je zdroj platný.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvořte objekt třídy `COleChangeSourceDialog` , pokud chcete zavolat toto dialogové okno. Po vytvoření `COleChangeSourceDialog` objektu lze pomocí struktury [m_cs](#m_cs) inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. Struktura je typu OLEUICHANGESOURCE. [](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) `m_cs` Další informace o použití této třídy dialogového okna naleznete v tématu členská funkce [DoModal](#domodal) .

Další informace najdete v tématu struktura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) v Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Tato funkce vytvoří `COleChangeSourceDialog` objekt.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na propojenou [COleClientItem](../../mfc/reference/coleclientitem-class.md) , jejíž zdroj se má aktualizovat.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, nadřazené okno dialogového okna bude nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal](#domodal) .

Další informace najdete v tématu struktura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) a funkce [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) v Windows SDK.

##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal

Voláním této funkce zobrazíte dialogové okno Změnit zdroj OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte členskou funkci [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , kde získáte další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v tématu funkce [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) v Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_cs](#m_cs) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat členské funkce pro načtení nastavení nebo informací zadaných uživatelem z dialogového okna. Následující seznam uvádí typické funkce dotazů:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItem](#getitemname)

##  <a name="getdisplayname"></a>COleChangeSourceDialog:: GetDisplayName

Voláním této funkce načtete celé zobrazované jméno pro propojenou položku klienta.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Návratová hodnota

Úplný zobrazovaný název zdroje (moniker) pro [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaný v konstruktoru.

##  <a name="getfilename"></a>COleChangeSourceDialog:: getsoubor

Voláním této funkce načtete část monikeru souboru zobrazovaného názvu pro propojenou položku klienta.

```
CString GetFileName();
```

### <a name="return-value"></a>Návratová hodnota

Část monikeru souboru zdrojového zobrazovaného názvu pro [COleClientItem](../../mfc/reference/coleclientitem-class.md) určenou v konstruktoru.

### <a name="remarks"></a>Poznámky

Moniker souboru spolu s monikerem položky poskytuje kompletní zobrazované jméno.

##  <a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Voláním této funkce získáte předchozí řetězec předpony pro zdroj.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí řetězec předpony zdroje.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte až po [DoModal](#domodal) vrátí IDOK.

Tato hodnota přichází přímo od `lpszFrom` členu struktury [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Další informace najdete v tématu struktura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) v Windows SDK.

##  <a name="getitemname"></a>COleChangeSourceDialog:: GetItem

Voláním této funkce načteme část monikeru položky zobrazovaného názvu pro propojenou položku klienta.

```
CString GetItemName();
```

### <a name="return-value"></a>Návratová hodnota

Část monikeru položky zdrojového zobrazovaného názvu pro [COleClientItem](../../mfc/reference/coleclientitem-class.md) určenou v konstruktoru.

### <a name="remarks"></a>Poznámky

Moniker souboru spolu s monikerem položky poskytuje kompletní zobrazované jméno.

##  <a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Voláním této funkce získáte nový řetězec předpony pro zdroj.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Návratová hodnota

Nový řetězec předpony zdroje.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte až po [DoModal](#domodal) vrátí IDOK.

Tato hodnota přichází přímo od `lpszTo` členu struktury [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Další informace najdete v tématu struktura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) v Windows SDK.

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

Tento datový člen je strukturou typu [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Poznámky

`OLEUICHANGESOURCE`slouží k řízení chování dialogového okna změnit zdroj OLE. Členy této struktury lze upravovat přímo.

Další informace najdete v tématu struktura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) v Windows SDK.

##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource

Voláním této funkce zjistíte, zda je nový zdroj platný.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nový zdroj platný, jinak 0.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte až po [DoModal](#domodal) vrátí IDOK.

Další informace najdete v tématu struktura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) v Windows SDK.

## <a name="see-also"></a>Viz také:

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
