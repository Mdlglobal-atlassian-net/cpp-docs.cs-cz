---
title: Třída COleChangeIconDialog
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
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369625"
---
# <a name="colechangeicondialog-class"></a>Třída COleChangeIconDialog

Používá se pro dialogové okno Ikona změny OLE.

## <a name="syntax"></a>Syntaxe

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[ColeChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Vytvoří `COleChangeIconDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleChangeIconDialog:ikona :DoChangeIcon](#dochangeicon)|Provede změnu zadanou v dialogovém okně.|
|[COleChangeIconDialog::DoModal](#domodal)|Zobrazí dialogové okno Ikona změny prostředí OLE 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k kultovní podobě této položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li volat `COleChangeIconDialog` toto dialogové okno, vytvořte objekt třídy. Po `COleChangeIconDialog` vytvoření objektu můžete použít [m_ci](#m_ci) struktury k inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. Struktura `m_ci` je typu OLEUICHANGEICON. Další informace o použití této třídy dialogů naleznete v členské funkci [DoModal.](#domodal)

Další informace naleznete v [oleuiCHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) struktury v sadě Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>ColeChangeIconDialog::COleChangeIconDialog

Tato funkce vytvoří `COleChangeIconDialog` pouze objekt.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Odkazuje na položku, která má být převedena.

*dwFlags*<br/>
Vytvoření příznak, který obsahuje libovolný počet následujících hodnot v kombinaci s bitové nebo operátor:

- CIF_SELECTCURRENT Určuje, že přepínací tlačítko Aktuální bude vybráno zpočátku při volání dialogového okna. Toto nastavení je výchozí.

- CIF_SELECTDEFAULT Určuje, že při volání dialogového okna bude nejprve vybráno výchozí přepínací tlačítko.

- CIF_SELECTFROMFILE Určuje, že přepínací tlačítko From File bude vybráno zpočátku při volání dialogového okna.

- CIF_SHOWHELP Určuje, že se při volání dialogového okna zobrazí tlačítko Nápověda.

- CIF_USEICONEXE Určuje, že ikona by měla být extrahována z spustitelného souboru `szIconExe` určeného v poli [m_ci](#m_ci) namísto načteného z typu. To je užitečné pro vkládání nebo propojení se soubory, které nejsou ole.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud se jedná o hodnotu NULL, bude nadřazené okno dialogového okna nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal.](#domodal)

Další informace naleznete v [oleuiCHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) struktury v sadě Windows SDK.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIconDialog:ikona :DoChangeIcon

Voláním této funkce změníte ikonu představující položku na ikonu vybranou v dialogovém okně po vrácení funkce IDOK do [funkce DoModal.](#domodal)

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Odkazuje na položku, jejíž ikona se mění.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je změna úspěšná; jinak 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIconDialog::DoModal

Voláním této funkce zobrazíte dialogové okno Ikona změny OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volání `COleDialog::GetLastError` členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v části [Funkce OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_ci](#m_ci) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí Hodnotu IDOK, můžete volat další členské funkce a načíst nastavení nebo informace, které uživatel zadal do dialogového okna.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Volání této funkce získat popisovač metasouboru, který obsahuje kultovní aspekt vybrané položky.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahující kultovní aspekt nové ikony, pokud dialogové okno bylo odmítnuto volbou **OK**; v opačném případě ikona, jak byla před zobrazením dialogového okna.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIconDialog::m_ci

Struktura typu OLEUICHANGEICON slouží k řízení chování dialogového okna Změnit ikonu.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravit přímo nebo prostřednictvím členských funkcí.

Další informace naleznete v [oleuiCHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) struktury v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
