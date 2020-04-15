---
title: Třída CMDITabinfo
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 0d230d2a3401ab556adc1183f4c4210ec6ff3c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370036"
---
# <a name="cmditabinfo-class"></a>Třída CMDITabinfo

Třída `CMDITabInfo` se používá k předání parametrů metodě [CMDIFrameWndEx::EnableMDITabbedGroups.](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) Nastavte členy této třídy pro řízení chování skupin s kartami MDI.

## <a name="syntax"></a>Syntaxe

```
class CMDITabInfo
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMDITabInfo::Serializovat](#serialize)|Přečte nebo zapíše tento objekt z nebo do archivu.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Určuje, zda se na popisku aktivní karty zobrazí tlačítko **Zavřít.**|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Určuje, zda mají být karty MDI vybarvovány.|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Určuje, zda skupina karet zobrazí místní nabídku, která zobrazuje seznam otevřených dokumentů nebo zobrazuje rolovací tlačítka.|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Určuje, zda může uživatel zaměnit pozice karet přetažením.|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Určuje, zda mají tabulátory plochý rámeček.|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Určuje, zda se na každém popisku karty zobrazí tlačítko **Zavřít.**|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Určuje, zda jsou povoleny vlastní popisky.|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Určuje, zda se mají na kartách MDI zobrazovat ikony.|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Určuje velikost ohraničení každého okna karty.|
|[CMDITabInfo::m_style](#m_style)|Určuje styl popisků karet.|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Určuje, zda jsou popisky karet umístěny v horní nebo dolní části stránky.|

## <a name="remarks"></a>Poznámky

Tato třída určuje parametry skupin y karet MDI, které vytvoří rozhraní framework.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit hodnoty různých proměnných `CMDITabInfo` členů ve třídě.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMDITabinfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmdiclientareawnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;

Určuje, zda se na popisku aktivní karty zobrazí tlačítko **Zavřít.**

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Poznámky

Pokud true, popisek aktivní karty se zobrazí tlačítko **Zavřít.** Tlačítko **Zavřít** bude odstraněno z pravého horního rohu oblasti karty. V opačném případě se na popisku aktivní karty nezobrazí tlačítko **Zavřít.** Tlačítko **Zavřít** se zobrazí v pravém horním rohu oblasti tabulátoru.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor

Určuje, zda má každá karta MDI svou vlastní barvu.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Poznámky

Pokud true, každá karta bude mít svou vlastní barvu. Sada barev je spravována knihovnou knihovny knihovny MFC. V opačném případě jsou karty zobrazeny bíle. Výchozí hodnota je FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu

Určuje, zda se na každé tabulátoru zobrazí místní nabídka, která zobrazuje seznam otevřených dokumentů na pravém okraji oblasti tabulátoru.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Poznámky

Pokud je true, každé okno karet zobrazí místní nabídku, která zobrazuje seznam otevřených dokumentů na pravém okraji oblasti karty; V opačném případě se v okně karty zobrazí tlačítka posouvání na pravém okraji oblasti karty. Výchozí hodnota je FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap

Určuje, zda může uživatel zaměnit pozice karet přetažením.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Poznámky

Pokud true, uživatel může změnit pozice karet přetažením karty. V opačném případě uživatel nemůže změnit pozice karet. Výchozí hodnota je TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame

Určuje, zda má každé okno karty plochý rámeček.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton

Určuje, zda se v každém okně karty zobrazí tlačítko **Zavřít.**

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Poznámky

Pokud je true, každé okno karty zobrazí tlačítko **Zavřít** na **Close** pravém okraji karty. Výchozí hodnota je TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips

Určuje, zda karty zobrazují popisky.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Poznámky

Pokud true, aplikace odešle zprávu AFX_WM_ON_GET_TAB_TOOLTIP do hlavního rámce. Tuto zprávu lze zpracovat pomocí ON_REGISTERED_MESSAGE makra.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons

Určuje, zda se mají na kartách MDI zobrazovat ikony.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Poznámky

Pokud true, ikony jsou zobrazeny na každé kartě MDI. V opačném případě ikony nejsou zobrazeny na kartách. Výchozí hodnota je FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize

Určuje velikost ohraničení každého okna karty v obrazových bodech.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Poznámky

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) vrátí výchozí hodnotu.

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITabInfo::m_style

Určuje styl popisků karet.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Poznámky

Pro popisky tabulátorů určete jeden z následujících stylů:

|||
|-|-|
|STYLE_3D|3D styl.  |
|STYLE_3D_ONENOTE|Styl Aplikace Microsoft OneNote.  |
|STYLE_3D_VS2005|Ve stylu sady Microsoft Visual Studio 2005.  |
|STYLE_3D_SCROLLED|3D styl s popisky obdélníkových karet.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Plochý styl se sdíleným vodorovným posuvníkem.  |
|STYLE_3D_ROUNDED_SCROLL|3D styl s kulatými popisky karet.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITabInfo::m_tabLocation

Určuje, zda jsou popisky karet umístěny v horní nebo dolní části stránky.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Poznámky

Použít na kartách jeden z následujících příznaků umístění:

- LOCATION_BOTTOM: Popisky karet jsou umístěny v dolní části stránky.

- LOCATION_TOP: Popisky karet jsou umístěny v horní části stránky

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITabInfo::Serializovat

Přečte nebo zapíše tento objekt z archivu nebo do archivu.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[v] [CArchive Class](../../mfc/reference/carchive-class.md) objekt serializovat.

## <a name="see-also"></a>Viz také

[Třída CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI – skupiny se záložkami](../../mfc/mdi-tabbed-groups.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
