---
title: CMFCPopupMenuBar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: b4693e316fd78948cfae262433fee8ca8b6ab23c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375365"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar – třída

Řádek nabídek vložený do rozbalovací nabídky.

## <a name="syntax"></a>Syntaxe

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Okamžitě přepočítá rozložení podokna. (Přepíše [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Načte položky místní nabídky ze zadaného prostředku nabídky.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Zavře tlačítko zpožděné rozbalovací nabídky.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Vytvoří nabídku z tlačítek místní nabídky.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Vyhledá panel nástrojů, kde leží zadaný bod.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Označuje velikost obrázků s tlačítkem nabídky.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Vrátí identifikátor výchozí položky nabídky.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Získá index naposledy vyvolané příkazu nabídky.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Získá řádek posun řádku rozbalovací panel nabídek.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importuje tlačítka místní nabídky ze zadané nabídky.|
|[CMFCPopupMenuBar::Režim IsDropDownListMode](#isdropdownlistmode)|Označuje, zda je automaticky otevíraný řádek nabídek v režimu rozevíracího seznamu.|
|[CMFCPopupMenuBar::Režim IsPaletteMode](#ispalettemode)|Označuje, zda je místní panel nabídek v režimu palety.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Označuje, zda se jedná o panel pásu karet (ve výchozím nastavení NEPRAVDA).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Označuje, zda se jedná o panel pásu karet v běžném režimu (ve výchozím nastavení NEPRAVDA).|
|[CMFCPopupMenuBar::NačístFromHash](#loadfromhash)|Načte archivovované menu.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Obnoví tlačítko zpožděné nabídky pro zavření místního řádku nabídek.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Nastaví styl tlačítka panelu nástrojů v daném indexu. (Přepíše [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Nastaví odsazení řádku rozbalovacího řádku nabídek.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Spustí časovač pro zadané tlačítko zpožděné rozbalovací nabídky.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Určuje, zda bude šedý postranní panel zobrazen, pokud má aplikace vzhled systému Windows XP.|

## <a name="remarks"></a>Poznámky

Je `CMFCPopupMenuBar` vytvořen ve stejnou dobu jako [CMFCPopupMenu třídy](../../mfc/reference/cmfcpopupmenu-class.md) a vložené uvnitř něj. Pokrývá `CMFCPopupMenuBar` celou klientskou oblast `CMFCPopupMenu` objektu. Podporuje vstup z klávesnice a myši. Také komunikuje, že vstup `CMFCPopupMenu` do okna a do okna rámce nejvyšší úrovně.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak inicializovat `CMFCPopupMenuBar` `CMFCPopupMenu` objekt z objektu. Tento fragment kódu je součástí [ukázky klienta Draw](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCPanel](../../mfc/reference/cmfctoolbar-class.md)

[CmFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate

Okamžitě přepočítá rozložení podokna místnínabídky nabídek. (Přepíše [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Parametry

*bRozložení a rozložení*<br/>
[v] TRUE pro automatický přepočet rozložení podokna automaticky vyskakovacínabídky nabídek; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems

Načte položky místní nabídky ze zadaného prostředku nabídky.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Parametry

*uiMenuResID*<br/>
[v] Určuje ID nabídky prostředku nabídky, který má být načíst.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná, nebo nehodnotit, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::CloseDelayedSubMenu

Zavře tlačítko místní nabídky, které bylo zpožděno.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu

Vytvoří nabídku z tlačítek místní nabídky.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do nové nabídky.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar

Vyhledá panel nástrojů, kde leží zadaný bod.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Bod na obrazovce.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač na panelu nástrojů, kde leží bod, pokud existuje, nebo NULL, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize

Označuje velikost obrázků s tlačítkem nabídky.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost obrazů tlačítek nabídky na panelu nástrojů.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId

Vrátí identifikátor výchozí položky nabídky.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí identifikátor výchozí položky nabídky v rozbalovacím řádku nabídek.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex

Získá index naposledy vyvolané příkazu nabídky.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí index posledního příkazu nabídky, který byl vyvolán.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopupMenuBar::GetOffset

Získá řádek posun řádku rozbalovací panel nabídek.

```
int GetOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odsazení řádku řádku nabídky automaticky otevíraných panelů.

### <a name="remarks"></a>Poznámky

Tato hodnota je nastavena pomocí [cmfcpopupmenubar::SetOffset](#setoffset).

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu

Importuje tlačítka místní nabídky ze zadané nabídky.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
[v] Nabídka, ze které chcete importovat tlačítka místní nabídky.

*bZobrazitAllPříkazy*<br/>
[v] TRUE, pokud mají být importovány všechny příkazy v nabídce, nebo nepravda, pokud se používají jen zřídka, mohou být skryté.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byla tlačítka nabídky úspěšně importována z nabídky, nebo nepravda, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFCPopupMenuBar::Režim IsDropDownListMode

Označuje, zda je automaticky otevíraný řádek nabídek v režimu rozevíracího seznamu.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je rozbalovací řádek nabídek v rozevíracím seznamu, nebo nepravda, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopupMenuBar::Režim IsPaletteMode

Označuje, zda je místní panel nabídek v režimu palety.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je povolen režim palety, nebo NEPRAVDA, pokud ne.

### <a name="remarks"></a>Poznámky

Pokud je řádek nabídek nastaven na režim palety, položky nabídky se zobrazí ve více sloupcích a v omezeném počtu řádků.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel

Označuje, zda se jedná o panel pásu karet (ve výchozím nastavení NEPRAVDA).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vrátí hodnotu NEPRAVDA, což znamená, že se nejedná o panel pásu karet.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Označuje, zda se jedná o panel pásu karet v běžném režimu (ve výchozím nastavení NEPRAVDA).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vrátí hodnotu NEPRAVDA, což znamená, že se nejedná o panel pásu karet v normálním režimu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar::NačístFromHash

Načte archivovované menu.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
[v] Popisovač archivované nabídky, kterou chcete načíst.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je nabídka úspěšně načtena, nebo nepravda, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Logický parametr, který označuje, zda má aplikace šedý postranní panel, pokud má vzhled systému Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Poznámky

Pokud je tato členská proměnná nastavena na hodnotu FALSE a aplikace má vzhled systému Windows XP, nakreslí rozhraní v aplikaci šedý postranní panel.

Výchozí hodnota je FALSE.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu

Obnoví tlačítko zpožděné nabídky pro zavření místního řádku nabídek.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle

Nastaví styl tlačítka panelu nástrojů v daném indexu. (Přepíše [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Nulový index tlačítka panelu nástrojů, jehož styl má být nastaven.

*nStyl*<br/>
[v] Styl tlačítka. Seznam dostupných stylů tlačítek panelu nástrojů naleznete v tématu [Styly ovládacích prvků nástrojů.](../../mfc/reference/toolbar-control-styles.md)

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFCPopupMenuBar::SetOffset

Nastaví odsazení řádku rozbalovacího řádku nabídek.

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Parametry

*iOffset*<br/>
[v] Počet řádků, které rozbalovací panel nabídek by měl y být posunuty.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer

Spustí časovač pro zadané tlačítko zpožděné rozbalovací nabídky.

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Parametry

*pMenuButton*<br/>
[v] Ukazatel na tlačítko nabídky, pro které chcete nastavit časovač zpoždění.

*nDelayFactor*<br/>
[v] Faktor zpoždění, který se rovná alespoň jednomu, vynásobí standardní dobou zpoždění nabídky (obvykle mezi půl sekundou a pěti sekundami).

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[Třída cmfcpopupmenu](../../mfc/reference/cmfcpopupmenu-class.md)
