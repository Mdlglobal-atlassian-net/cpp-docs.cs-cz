---
title: Colechangesourcedialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc05da05ece61652a94c25ccae5b3164c067b8f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400936"
---
# <a name="colechangesourcedialog-class"></a>Colechangesourcedialog – třída

Používá se pro dialogové okno změny zdroje OLE.

## <a name="syntax"></a>Syntaxe

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Vytvoří `COleChangeSourceDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Zobrazí dialogové okno změny zdroje OLE.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Získá úplný zdrojový zobrazovaný název.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Získá název souboru z název zdroje.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Získá předponu předchozí zdroje.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Získá název položky z název zdroje.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Získá předponu nový zdroj|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Určuje, zda je platný zdroj.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu třídy `COleChangeSourceDialog` kdy chcete volat dialogovému oknu. Po `COleChangeSourceDialog` objekt byl vytvořen, můžete použít [m_cs](#m_cs) struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_cs` Struktury je typu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea). Další informace o použití této třídy dialogového okna, najdete v článku [DoModal](#domodal) členskou funkci.

Další informace najdete v tématu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktura v sadě Windows SDK.

Další informace o dialogových oknech OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

[Coledialog –](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog

Tato funkce vytvoří `COleChangeSourceDialog` objektu.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na propojený [COleClientItem](../../mfc/reference/coleclientitem-class.md) jejichž zdrojem je potřeba aktualizovat.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nastaví se nadřazené okno dialogového okna do hlavního okna aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.

Další informace najdete v tématu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) strukturu a [OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) funkce v sadě Windows SDK.

##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal

Voláním této funkce Zobrazit dialogové okno změny zdroje OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení pro dialogové okno. Jeden z následujících hodnot:

- IDOK, pokud úspěšně zobrazí dialogové okno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_cs](#m_cs) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat členské funkce k načtení nastavení zadaný uživatelem nebo informace z dialogového okna. Následující seznam uvádí typické dotazu funkce:

- [GetFileName](#getfilename)

- [Getdisplayname –](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName

Volání této funkce načtete úplný zobrazovaný název pro položku propojenou klienta.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Návratová hodnota

Úplný zdrojový zobrazovaný název (moniker) [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaný v konstruktoru.

##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName

Volání této funkce načtete soubor moniker část zobrazovaného názvu pro položku propojenou klienta.

```
CString GetFileName();
```

### <a name="return-value"></a>Návratová hodnota

Část zobrazovaný název zdrojového souboru moniker [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaný v konstruktoru.

### <a name="remarks"></a>Poznámky

Zástupný název souboru spolu s zástupný název položky poskytuje úplný zobrazovaný název.

##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix

Voláním této funkce získáte předchozí řetězec předpony pro zdroj.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí předpona řetězce zdroje.

### <a name="remarks"></a>Poznámky

Tato funkce až po volání [DoModal](#domodal) vrátí IDOK.

Tato hodnota pochází přímo z `lpszFrom` člena [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktury.

Další informace najdete v tématu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktura v sadě Windows SDK.

##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName

Volání této funkce načtete zástupný název položky část zobrazovaného názvu pro položku propojenou klienta.

```
CString GetItemName();
```

### <a name="return-value"></a>Návratová hodnota

Zástupný název položky část zobrazovaný název zdroje [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaný v konstruktoru.

### <a name="remarks"></a>Poznámky

Zástupný název souboru spolu s zástupný název položky poskytuje úplný zobrazovaný název.

##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix

Volání této funkce získáte nový řetězec předpony pro zdroj.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Návratová hodnota

Nový řetězec předpony zdroje.

### <a name="remarks"></a>Poznámky

Tato funkce až po volání [DoModal](#domodal) vrátí IDOK.

Tato hodnota pochází přímo z `lpszTo` člena [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktury.

Další informace najdete v tématu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktura v sadě Windows SDK.

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

Tento datový člen je struktura typu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Poznámky

`OLEUICHANGESOURCE` slouží k řízení chování dialogové okno změny zdroje OLE. Členové této struktury lze změnit přímo.

Další informace najdete v tématu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktura v sadě Windows SDK.

##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource

Voláním této funkce lze zjistit nový zdroj je platný.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud nový zdroj je platný, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce až po volání [DoModal](#domodal) vrátí IDOK.

Další informace najdete v tématu [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) struktura v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
