---
title: Třída COlePropertiesDialog
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
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374886"
---
# <a name="colepropertiesdialog-class"></a>Třída COlePropertiesDialog

Zapouzdřuje dialogové okno Vlastnosti objektu OLE pro prostředí Windows.

## <a name="syntax"></a>Syntaxe

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Vytvoří `COlePropertiesDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COlePropertiesDialog::DoModální](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Volat rámci při změně škálování položky dokumentu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Struktura slouží k inicializaci "Obecné" `COlePropertiesDialog` stránky objektu.|
|[COlePropertiesDialog::m_lp](#m_lp)|Struktura slouží k inicializaci stránky "Odkaz" objektu. `COlePropertiesDialog`|
|[COlePropertiesDialog::m_op](#m_op)|Struktura slouží k inicializaci objektu. `COlePropertiesDialog`|
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura slouží k přidání další chod vlastní chod stránky.|
|[COlePropertiesDialog::m_vp](#m_vp)|Struktura používaná k přizpůsobení stránky Zobrazení `COlePropertiesDialog` objektu.|

## <a name="remarks"></a>Poznámky

Běžná dialogová okna vlastností objektu OLE poskytují snadný způsob zobrazení a úpravy vlastností položky dokumentu OLE způsobem konzistentním se standardy systému Windows. Mezi tyto vlastnosti patří mimo jiné informace o souboru reprezentovaném položkou dokumentu, možnosti zobrazení ikony a změny velikosti obrazu a informace o propojení položky (pokud je položka propojena).

Chcete-li `COlePropertiesDialog` použít objekt, nejprve `COlePropertiesDialog` vytvořte objekt pomocí konstruktoru. Po vytvoření dialogového okna zavolejte `DoModal` členská funkce, aby zobrazila dialogové okno a umožnila uživateli upravit všechny vlastnosti položky. `DoModal`vrátí, zda uživatel zvolil tlačítko OK (IDOK) nebo Cancel (IDCANCEL). Kromě tlačítek OK a Storno je k dispozici tlačítko Použít. Když uživatel vybere použít, všechny změny provedené ve vlastnostech položky dokumentu se použijí na položku a její obraz se automaticky aktualizuje, ale zůstane aktivní.

Datový [člen m_psh](#m_psh) je ukazatel `PROPSHEETHEADER` na strukturu a ve většině případů k němu nebudete muset přistupovat explicitně. Jednou výjimkou je, když potřebujete další stránky vlastností nad rámec výchozích stránek Obecné, Zobrazení a Odkaz. V takovém případě můžete `m_psh` upravit datový člen tak, aby `DoModal` zahrnoval vlastní stránky před voláním členské funkce.

Další informace o dialogových oknech OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

Vytvoří `COlePropertiesDialog` objekt.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na položku dokumentu, jejíž vlastnosti jsou prostupovány.

*nScaleMin*<br/>
Minimální procento změny měřítka pro obrázek položky dokumentu.

*nScaleMax*<br/>
Maximální procento změny měřítka pro obraz položky dokumentu

*pParentWnd*<br/>
Ukazatel na nadřazeného nebo vlastníka dialogového okna.

### <a name="remarks"></a>Poznámky

Odvodit běžné vlastnosti `COlePropertiesDialog` objektu OLE třídy dialogového okna z za účelem implementace změny měřítka pro položky dokumentu. Všechna dialogová okna implementovaná instancí této třídy nebudou podporovat změnu měřítka položky dokumentu.

Ve výchozím nastavení má společné dialogové okno Vlastnosti objektu OLE tři výchozí stránky:

- Obecné

   Tato stránka obsahuje systémové informace pro soubor reprezentované vybranou položkou dokumentu. Na této stránce může uživatel převést vybranou položku na jiný typ.

- Zobrazení

   Tato stránka obsahuje možnosti zobrazení položky, změny ikony a změny měřítka obrazu.

- Odkaz

   Tato stránka obsahuje možnosti pro změnu umístění propojené položky a aktualizaci propojené položky. Na této stránce může uživatel přerušit propojení vybrané položky.

Chcete-li přidat stránky nad rámec stránek, které jsou k dispozici `COlePropertiesDialog`ve výchozím nastavení, upravte [proměnnou m_psh](#m_psh) člen před ukončením konstruktoru odvozené třídy. Toto je pokročilá `COlePropertiesDialog` implementace konstruktoru.

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COlePropertiesDialog::DoModální

Volánítéto členské funkce zobrazí dialogové okno Vlastnosti objektu OLE pro systém Windows a umožní uživateli zobrazit nebo změnit různé vlastnosti položky dokumentu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL v případě úspěchu; jinak 0. IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel zvolil tlačítko OK nebo Cancel.

Pokud je vrácena funkce IDCANCEL, můžete volat funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a zjistit, zda došlo k chybě.

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COlePropertiesDialog::m_gp

Struktura typu [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw), která slouží k inicializaci stránky Obecné v dialogovém okně Vlastnosti objektu OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Poznámky

Na této stránce se zobrazuje typ a velikost vložení a umožňuje uživateli přístup k dialogovému oknu Převést. Tato stránka také zobrazuje cíl odkazu, pokud je objekt emitační.

Další informace o `OLEUIGNRLPROPS` struktuře naleznete v souboru Windows SDK.

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COlePropertiesDialog::m_lp

Struktura typu [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw), která slouží k inicializaci stránky Propojení dialogového okna Vlastnosti objektu OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Poznámky

Na této stránce je zobrazeno umístění propojené položky a umožňuje uživateli aktualizovat nebo přerušit odkaz na položku.

Další informace o `OLEUILINKPROPS` struktuře naleznete v souboru Windows SDK.

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COlePropertiesDialog::m_op

Struktura typu [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw), která slouží k inicializaci společného dialogového okna Vlastnosti objektu OLE.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Poznámky

Tato struktura obsahuje členy používané k inicializaci obecné, odkaz a zobrazit stránky.

Další informace naleznete v oleuiobjectprops a [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) struktury v sadě Windows SDK.

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COlePropertiesDialog::m_psh

Struktura typu [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2), jejíž členové ukládají vlastnosti objektu dialogového okna.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Poznámky

Po vytvoření `COlePropertiesDialog` objektu můžete `m_psh` před voláním `DoModal` členské funkce nastavit různé aspekty dialogového okna.

Pokud změníte `m_psh` datový člen přímo, přepíšete jakékoli výchozí chování.

Další informace o `PROPSHEETHEADER` struktuře naleznete v souboru Windows SDK.

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COlePropertiesDialog::m_vp

Struktura typu [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw), která slouží k inicializaci stránky Zobrazení dialogového okna Vlastnosti objektu OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Poznámky

Tato stránka umožňuje uživateli přepínat mezi "obsah" a "ikonické" zobrazení objektu a změnit jeho škálování v kontejneru. Umožňuje také uživateli přístup k dialogovému oknu Změnit ikonu, když je objekt zobrazen jako ikona.

Další informace o `OLEUIVIEWPROPS` struktuře naleznete v souboru Windows SDK.

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

Volat rámci při změně hodnoty škálování a buď OK nebo Použít byla vybrána.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na položku dokumentu, jejíž vlastnosti jsou prostupovány.

*nCurrentScale*<br/>
Číselná hodnota dialogového okna.

*bRelativeToOrig*<br/>
Označuje, zda se změna měřítka vztahuje na původní velikost položky dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné provádění. Chcete-li povolit ovládací prvky škálování, je nutné tuto funkci přepsat.

> [!NOTE]
> Před zobrazením společného dialogového okna Vlastnosti objektu OLE nazývá rozhraní tuto funkci s hodnotou NULL pro *položku pItem* a a - 1 pro *nCurrentScale*. To se provádí k určení, pokud by měly být povoleny ovládací prvky škálování.

## <a name="see-also"></a>Viz také

[Vzorek knihovny MFC CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage – třída](../../mfc/reference/cpropertypage-class.md)
