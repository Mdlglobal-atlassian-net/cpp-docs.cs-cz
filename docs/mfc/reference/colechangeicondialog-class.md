---
title: COleChangeIconDialog Class
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 4cbf1137a15a9f86a6377980526e6d188f4d0a69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504781"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog Class

Používá se pro dialogové okno ikona změny OLE.

## <a name="syntax"></a>Syntaxe

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|`COleChangeIconDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Provede změnu určenou v dialogovém okně.|
|[COleChangeIconDialog::DoModal](#domodal)|Zobrazí dialogové okno Změnit ikonu OLE 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k ikonickým formuláři této položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvořte objekt třídy `COleChangeIconDialog` , pokud chcete zavolat toto dialogové okno. Po vytvoření `COleChangeIconDialog` objektu lze pomocí struktury [m_ci](#m_ci) inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_ci` Struktura je typu OleUIChangeIcon. Další informace o použití této třídy dialogového okna naleznete v tématu členská funkce [DoModal](#domodal) .

Další informace najdete v tématu struktura [OleUIChangeIcon](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) v Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

Tato funkce vytvoří pouze `COleChangeIconDialog` objekt.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, která má být převedena.

*dwFlags*<br/>
Příznak vytvoření, který obsahuje libovolný počet následujících hodnot v kombinaci pomocí bitového operátoru OR:

- CIF_SELECTCURRENT určuje, že aktuální přepínač bude při volání dialogového okna vybrán jako první. Toto nastavení je výchozí.

- CIF_SELECTDEFAULT Určuje, že výchozí přepínač bude zpočátku vybrán při volání dialogového okna.

- CIF_SELECTFROMFILE určuje, že přepínač ze souboru od bude při volání dialogového okna vybrán jako první.

- CIF_SHOWHELP určuje, že se při volání dialogového okna zobrazí tlačítko Help.

- CIF_USEICONEXE určuje, že ikona by měla být extrahována ze spustitelného souboru `szIconExe` zadaného v poli [m_ci](#m_ci) namísto načtení z typu. To je užitečné pro vkládání nebo propojení s jinými soubory než OLE.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, nadřazené okno dialogového okna bude nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal](#domodal) .

Další informace najdete v tématu struktura [OleUIChangeIcon](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) v Windows SDK.

##  <a name="dochangeicon"></a>COleChangeIconDialog::D oChangeIcon

Voláním této funkce změníte ikonu reprezentující položku na tu, která je vybrána v dialogovém okně po [DoModal](#domodal) vrátí IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, jejíž ikonu se mění.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je změna úspěšná; v opačném případě 0.

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

Voláním této funkce zobrazíte dialogové okno ikona změny OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte `COleDialog::GetLastError` členskou funkci pro získání dalších informací o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) .

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_ci](#m_ci) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete zavolat jiné členské funkce a načíst tak nastavení nebo informace, které uživatel zadal, do dialogového okna.

##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Voláním této funkce získáte popisovač metasouboru, který obsahuje aspekt ikonickým vybrané položky.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahujícího aspekt ikonickým nové ikony, pokud dialogové okno bylo zavřeno kliknutím na **tlačítko OK**; v opačném případě se ikona změnila před zobrazením dialogového okna.

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

Struktura typu OLEUICHANGEICON slouží k řízení chování dialogového okna změnit ikonu.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat buď přímo, nebo prostřednictvím členských funkcí.

Další informace najdete v tématu struktura [OleUIChangeIcon](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) v Windows SDK.

## <a name="see-also"></a>Viz také:

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
