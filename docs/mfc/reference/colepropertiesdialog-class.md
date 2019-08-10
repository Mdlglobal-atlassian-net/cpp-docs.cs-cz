---
title: COlePropertiesDialog – třída
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
ms.openlocfilehash: bdae64ff4a7bcfef761eaf3dd70a85a54efc28b7
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916963"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog – třída

Zapouzdřuje dialogové okno běžné vlastnosti objektu OLE systému Windows.

## <a name="syntax"></a>Syntaxe

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|`COlePropertiesDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Volá se rozhraním, když se změnilo měřítko položky dokumentu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Struktura používaná k inicializaci stránky `COlePropertiesDialog` "Obecné" objektu.|
|[COlePropertiesDialog::m_lp](#m_lp)|Struktura používaná k inicializaci stránky `COlePropertiesDialog` "propojení" objektu.|
|[COlePropertiesDialog::m_op](#m_op)|Struktura používaná k inicializaci `COlePropertiesDialog` objektu.|
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura používaná k přidání dalších vlastních stránek vlastností.|
|[COlePropertiesDialog::m_vp](#m_vp)|Struktura používaná k přizpůsobení stránky `COlePropertiesDialog` "zobrazení" objektu.|

## <a name="remarks"></a>Poznámky

Dialogová okna vlastností objektů OLE poskytují snadný způsob, jak zobrazit a upravit vlastnosti položky dokumentu OLE způsobem konzistentním s normami systému Windows. Tyto vlastnosti zahrnují mimo jiné informace o souboru reprezentovaného položkou dokumentu, možnosti pro zobrazení ikony a měřítka obrázku a informace o odkazu položky (Pokud je položka propojená).

Chcete-li `COlePropertiesDialog` použít objekt, nejprve vytvořte objekt `COlePropertiesDialog` pomocí konstruktoru. Po sestavení dialogového okna volejte `DoModal` členskou funkci pro zobrazení dialogového okna a umožněte uživateli upravovat jakékoli vlastnosti položky. `DoModal`Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL). Kromě tlačítek OK a Storno je k dispozici tlačítko použít. Když uživatel vybere použít, všechny změny vlastností položky dokumentu se aplikují na položku a její obrázek se automaticky aktualizuje, ale zůstane aktivní.

Datový člen [m_psh](#m_psh) je ukazatel na `PROPSHEETHEADER` strukturu a ve většině případů k němu nebudete mít přístup explicitně. Jedinou výjimkou je, že potřebujete další stránky vlastností nad rámec výchozích stránek Obecné, zobrazení a propojení. V takovém případě můžete změnit `m_psh` datového člena tak, aby zahrnoval vlastní stránky před `DoModal` voláním členské funkce.

Další informace o dialogových oknech OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

`COlePropertiesDialog` Vytvoří objekt.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku dokumentu, jejíž vlastnosti jsou k dispozici.

*nScaleMin*<br/>
Minimální procentuální hodnota měřítka pro obrázek položky dokumentu

*nScaleMax*<br/>
Maximální procentuální hodnota měřítka pro obrázek položky dokumentu

*pParentWnd*<br/>
Ukazatel na nadřazenou položku nebo vlastníka dialogového okna.

### <a name="remarks"></a>Poznámky

Chcete-li implementovat škálování pro položky dokumentu, `COlePropertiesDialog` odvodit vlastní třídu dialogového okna vlastností objektu OLE z důvodu implementace škálování. Všechna dialogová okna, která jsou implementována instancí této třídy, nebudou podporovat škálování položky dokumentu.

Ve výchozím nastavení má dialogové okno společné vlastnosti objektu OLE tři výchozí stránky:

- Obecné

   Tato stránka obsahuje systémové informace pro soubor reprezentovaný vybranou položkou dokumentu. Na této stránce může uživatel převést vybranou položku na jiný typ.

- Zobrazit

   Tato stránka obsahuje možnosti pro zobrazení položky, změnu ikony a změnu měřítka obrázku.

- Odkaz

   Tato stránka obsahuje možnosti pro změnu umístění propojené položky a aktualizaci propojené položky. Na této stránce může uživatel přerušit odkaz na vybranou položku.

Chcete-li přidat stránky nad rámec těch, které jsou [](#m_psh) k dispozici ve výchozím nastavení, upravte členskou proměnnou `COlePropertiesDialog`m_psh před ukončením konstruktoru vaší odvozené třídy. Toto je pokročilá implementace `COlePropertiesDialog` konstruktoru.

##  <a name="domodal"></a>COlePropertiesDialog::D oModal

Zavolejte tuto členskou funkci pro zobrazení dialogového okna běžné vlastnosti objektu OLE systému Windows a umožněte uživateli zobrazit a změnit různé vlastnosti položky dokumentu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL v případě úspěchu; v opačném případě 0. IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo Storno.

Pokud se vrátí IDCANCEL, můžete zavolat funkci Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) a zjistit, jestli došlo k chybě.

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

Struktura typu [OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa)používaná k inicializaci stránky Obecné dialogového okna vlastnosti objektu OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Poznámky

Tato stránka zobrazuje typ a velikost vložení a umožňuje uživateli přístup k dialogovému oknu převést. Tato stránka obsahuje také cíl propojení, pokud je objekt odkazem.

Další informace o `OLEUIGNRLPROPS` struktuře najdete v Windows SDK.

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

Struktura typu [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa), která se používá k inicializaci stránky odkazu v dialogovém okně Vlastnosti objektu OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Poznámky

Tato stránka zobrazuje umístění propojené položky a umožňuje uživateli aktualizovat nebo přerušit odkaz na položku.

Další informace o `OLEUILINKPROPS` struktuře najdete v Windows SDK.

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

Struktura typu [OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa)používaná k inicializaci běžných dialogových oken vlastností objektu OLE.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Poznámky

Tato struktura obsahuje členy používané k inicializaci stránek Obecné, propojení a zobrazení.

Další informace naleznete v tématu struktury OLEUIOBJECTPROPS a [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) v Windows SDK.

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

Struktura typu [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-propsheetheadera_v2), jejíž členové ukládají charakteristiky objektu dialogového okna.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Poznámky

Po sestavení `COlePropertiesDialog` objektu lze použít `m_psh` k nastavení různých aspektů `DoModal` dialogového okna před voláním členské funkce.

Změníte-li datový člen přímo, přepíšete všechny výchozí chování. `m_psh`

Další informace o `PROPSHEETHEADER` struktuře najdete v Windows SDK.

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

Struktura typu [OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa), která slouží k inicializaci stránky zobrazení dialogového okna vlastnosti objektu OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Poznámky

Tato stránka umožňuje uživateli přepínání mezi zobrazeními obsahu a ikonickým objektu a změnou jeho škálování v rámci kontejneru. Umožňuje také uživateli přístup k dialogovému oknu změnit ikonu změny, když se objekt zobrazuje jako ikona.

Další informace o `OLEUIVIEWPROPS` struktuře najdete v Windows SDK.

##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

Volá se rozhraním, když se změnila hodnota škálování a vybraná možnost OK nebo použít.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku dokumentu, jejíž vlastnosti jsou k dispozici.

*nCurrentScale*<br/>
Číselná hodnota měřítka dialogového okna

*bRelativeToOrig*<br/>
Určuje, zda se měřítko vztahuje na původní velikost položky dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se zpracovává; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovádí žádnou akci. Chcete-li povolit ovládací prvky škálování, je nutné tuto funkci přepsat.

> [!NOTE]
>  Před zobrazením dialogového okna společné vlastnosti objektu OLE rozhraní volá tuto funkci s hodnotou NULL pro *pItem* a-1 pro *nCurrentScale*. K tomu je potřeba určit, jestli se mají povolit ovládací prvky škálování.

## <a name="see-also"></a>Viz také:

[Ukázka MFC – ukázkový oběžník](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage – třída](../../mfc/reference/cpropertypage-class.md)
