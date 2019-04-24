---
title: Colepropertiesdialog – třída
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: e574f535609ec9401bd76badf11fa7e05cc0c619
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224389"
---
# <a name="colepropertiesdialog-class"></a>Colepropertiesdialog – třída

Zapouzdřuje dialogové okno Vlastnosti objektu OLE Windows běžné.

## <a name="syntax"></a>Syntaxe

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Vytvoří `COlePropertiesDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživatelům provést výběr.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Volá se rozhraním, při škálování položka dokumentu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Struktury použité k inicializaci stránku "Obecné" `COlePropertiesDialog` objektu.|
|[COlePropertiesDialog::m_lp](#m_lp)|Struktury použité k inicializaci stránky na "Propojení" `COlePropertiesDialog` objektu.|
|[COlePropertiesDialog::m_op](#m_op)|Struktury použité k inicializaci `COlePropertiesDialog` objektu.|
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura, chcete-li přidat další vlastní stránky vlastností.|
|[COlePropertiesDialog::m_vp](#m_vp)|Struktura používané k úpravám na stránce "Zobrazit" `COlePropertiesDialog` objektu.|

## <a name="remarks"></a>Poznámky

Společná dialogová okna vlastnosti objektu OLE poskytují snadný způsob, jak zobrazit a upravit vlastnosti dokumentu položky OLE v souladu se standardy Windows. Tyto vlastnosti patří mimo jiné informace o souboru reprezentována položka dokumentu, možnosti pro zobrazení ikon a škálování image a informace na odkaz položku (Pokud je propojená položka).

Použití `COlePropertiesDialog` objektu, musíte nejprve vytvořit objekt pomocí `COlePropertiesDialog` konstruktoru. Poté, co byl vytvořen dialogových oken, volejte `DoModal` členské funkce k zobrazení dialogového okna a umožní uživateli změnit jakékoli vlastnosti položky. `DoModal` Vrátí, zda uživatel vybral OK (IDOK) nebo na tlačítko Storno (IDCANCEL). Kromě tlačítka OK a zrušit je tlačítko použít. Když uživatel vybere použít, jsou všechny změny vlastnosti položky. dokument použitý pro položku a jeho image se automaticky aktualizují, ale zůstává aktivní.

[M_psh](#m_psh) je ukazatel na datový člen `PROPSHEETHEADER` strukturu a ve většině případů nebudete muset explicitně k němu přístup. Jedinou výjimkou je, když budete potřebovat další stránky vlastností nad výchozí stránky Obecné, zobrazení a propojení. V takovém případě můžete upravit `m_psh` datový člen zahrnout vaše vlastní stránky před voláním `DoModal` členskou funkci.

Další informace o dialogových oken OLE, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog

Vytvoří `COlePropertiesDialog` objektu.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku dokumentu, jehož vlastnosti přistupuje.

*nScaleMin*<br/>
Minimální velikost v procentech pro obrázek položky dokumentu.

*nScaleMax*<br/>
Maximální velikost v procentech pro obrázek položky dokumentu.

*pParentWnd*<br/>
Ukazatel na nadřazenou nebo vlastník dialogových oken.

### <a name="remarks"></a>Poznámky

Odvodit vlastní běžné třídy dialogového okna vlastnosti objektu OLE z `COlePropertiesDialog` kvůli implementaci škálování pro vaše položky dokumentu. Všechna dialogová okna implementované instance této třídy nebude podporovat škálování položka dokumentu.

Ve výchozím nastavení běžné dialogové okno Vlastnosti objektu OLE má tři výchozí stránky:

- Obecné

   Tato stránka obsahuje informace o systému pro soubor reprezentován položkou vybraný dokument. Z této stránky můžete uživatele převést vybrané položky k jinému typu.

- Zobrazit

   Tato stránka obsahuje možnosti pro položku zobrazení, změna ikony a změna měřítka obrázku.

- Odkaz

   Tato stránka obsahuje možnosti pro změnu umístění propojené položky a aktualizaci propojená položka. Z této stránky můžete uživatele rozdělit odkaz na vybranou položku.

Chcete-li přidat stránky nad rámec těch, které poskytuje ve výchozím nastavení, upravte [m_psh](#m_psh) členskou proměnnou před ukončením konstruktoru vaše `COlePropertiesDialog`– odvozené třídy. Toto je implementace pokročilých `COlePropertiesDialog` konstruktoru.

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

Voláním této členské funkce a zobrazte dialogové okno Vlastnosti objektu OLE Windows běžné povolit uživatelům zobrazení a/nebo měnit různé vlastnosti objektu položka dokumentu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL v případě úspěchu; jinak 0. IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo zrušit.

Pokud se vrátí IDCANCEL, můžete volat Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě.

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

Strukturu typu [OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa), která slouží k inicializaci stránku Obecné dialogové okno Vlastnosti objektu OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Poznámky

Tato stránka zobrazuje typ a velikost obsažení a umožňuje uživatelům přístup k dialogové okno Převést. Tato stránka zobrazuje také cíl odkazu, pokud objekt je odkaz.

Další informace o `OLEUIGNRLPROPS` struktury, naleznete v sadě Windows SDK.

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

Strukturu typu [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa), která slouží k inicializaci stránky odkaz v dialogovém okně vlastností objektu OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Poznámky

Tato stránka zobrazuje umístění propojené položky a umožní uživateli aktualizovat nebo přerušit, odkaz na položku.

Další informace o `OLEUILINKPROPS` struktury, naleznete v sadě Windows SDK.

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

Strukturu typu [OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa), která slouží k inicializaci běžné dialogové okno Vlastnosti objektu OLE.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Poznámky

Tato struktura obsahuje členy použitý k inicializaci Obecné, propojení a zobrazení stránek.

Další informace najdete v článku OLEUIOBJECTPROPS a [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) struktury v sadě Windows SDK.

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

Strukturu typu [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2), jejíž členové uložení vlastnosti z objektu dialogového okna.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Poznámky

Po sestavení `COlePropertiesDialog` objektu, můžete použít `m_psh` nastavit různé aspekty dialogového okna před voláním `DoModal` členskou funkci.

Pokud změníte `m_psh` datový člen přímo, budou všechny výchozí chování přepsat.

Další informace o `PROPSHEETHEADER` struktury, naleznete v sadě Windows SDK.

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

Strukturu typu [OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa), která slouží k inicializaci stránky zobrazení dialogového okna vlastnosti objektu OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Poznámky

Tato stránka umožňuje uživatelům přepínat mezi "obsah" a "ikonickým" zobrazení objektu a změnit jeho velikost v rámci kontejneru. Umožňuje také přístup uživatelů k dialogové okno změny ikony, když se objekt zobrazí jako ikona.

Další informace o `OLEUIVIEWPROPS` struktury, naleznete v sadě Windows SDK.

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

Volá se rozhraním, když došlo ke změně hodnoty měřítka a byla vybrána OK nebo použít.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku dokumentu, jehož vlastnosti přistupuje.

*nCurrentScale*<br/>
Číselná hodnota parametru scale dialogového okna.

*bRelativeToOrig*<br/>
Určuje, zda škálování se vztahuje na původní velikost položka dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpracovává; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace nemá žádný účinek. Tato funkce umožňuje škálování ovládací prvky je nutné přepsat.

> [!NOTE]
>  Předtím, než se zobrazí dialogové okno běžné vlastnosti objektu OLE, volá rámec této funkce s hodnotou NULL pro *pItem* a a - 1 pro *nCurrentScale*. To slouží k určení, zda by měl povolený škálování ovládací prvky.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC KR](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage – třída](../../mfc/reference/cpropertypage-class.md)
