---
title: Colechangeicondialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs:
- C++
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f6cec1694e5885d837d68edd292f5cc201b9155
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384439"
---
# <a name="colechangeicondialog-class"></a>Colechangeicondialog – třída

Používá se pro dialogové okno změny ikony OLE.

## <a name="syntax"></a>Syntaxe

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Vytvoří `COleChangeIconDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Provede změnu zadané v dialogovém okně.|
|[COleChangeIconDialog::DoModal](#domodal)|Zobrazí dialogové okno 2 změny ikony OLE.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro tento metasoubor spojené s formuláři ikonickým této položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu třídy `COleChangeIconDialog` kdy chcete volat dialogovému oknu. Po `COleChangeIconDialog` objekt byl vytvořen, můžete použít [m_ci](#m_ci) struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_ci` Struktury je typu OLEUICHANGEICON. Další informace o použití této třídy dialogového okna, najdete v článku [DoModal](#domodal) členskou funkci.

Další informace najdete v tématu [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) struktura v sadě Windows SDK.

Další informace o dialogových oknech OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

[Coledialog –](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog

Tato funkce vytvoří pouze `COleChangeIconDialog` objektu.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, kterou chcete převést.

*dwFlags*<br/>
Vytvoření příznak, který bude obsahovat libovolný počet následující hodnoty kombinované pomocí bitového – operátor or:

- CIF_SELECTCURRENT Určuje, že bude aktuální přepínací tlačítko vybrané zpočátku když je volána dialogových oken. Toto nastavení je výchozí.

- CIF_SELECTDEFAULT Určuje, které se bude přepínač výchozí vybraná zpočátku když je volána dialogových oken.

- CIF_SELECTFROMFILE Určuje, které se bude přepínač ze souboru vybrat zpočátku když je volána dialogových oken.

- CIF_SHOWHELP Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogových oken.

- CIF_USEICONEXE Určuje, že ikona by měla být rozbalena z spustitelný soubor určený v `szIconExe` pole [m_ci](#m_ci) místo se načítá z typu. To je užitečné pro vkládání nebo propojení souborů jiných než OLE.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nastaví se nadřazené okno dialogového okna do hlavního okna aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.

Další informace najdete v tématu [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) struktura v sadě Windows SDK.

##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon

Voláním této funkce můžete změnit ikonu představující položku byla vybrána v dialogovém okně po [DoModal](#domodal) vrátí IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, jehož ikonu se mění.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud změna je úspěšná. jinak 0.

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

Voláním této funkce Zobrazit dialogové okno změny ikony OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení pro dialogové okno. Jeden z následujících hodnot:

- IDOK, pokud úspěšně zobrazí dialogové okno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte `COleDialog::GetLastError` členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIChangeIcon](/windows/desktop/api/oledlg/nf-oledlg-oleuichangeicona) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_ci](#m_ci) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat ostatní členské funkce k načtení nastavení nebo informace, které se vstup uživatelem do dialogových oken.

##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile

Voláním této funkce se získat popisovač pro tento metasoubor obsahující ikonickým aspekt vybranou položku.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač na metasoubor obsahující ikonickým aspekt přes novou ikonu, pokud dialogové okno se zavře výběrem **OK**; v opačném případě ikona, protože byl předtím, než se zobrazí dialogové okno.

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

Struktura typu OLEUICHANGEICON používat k ovládání chování dialogové okno změny ikony.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Poznámky

Přímo nebo prostřednictvím členské funkce, lze upravit členy této struktury.

Další informace najdete v tématu [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) struktura v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
