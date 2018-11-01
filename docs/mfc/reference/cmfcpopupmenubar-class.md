---
title: Cmfcpopupmenubar – třída
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
ms.openlocfilehash: 931404412d3b30d5352ecd2fabe30f9ec30f2e3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511815"
---
# <a name="cmfcpopupmenubar-class"></a>Cmfcpopupmenubar – třída

Panel nabídek vložený do místní nabídky.

## <a name="syntax"></a>Syntaxe

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Okamžitě přepočítá rozložení na stavového řádku. (Přepíše [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Načte položky místní nabídky z nabídky prostředků.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Tlačítka s nabídkou zpožděné automaticky otevírané okno se zavře.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Sestavení z místní nabídky tlačítka nabídky.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Pokud je zadaný bod vyhledá panelu nástrojů.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Určuje velikost obrázků tlačítka nabídky.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Vrátí identifikátor výchozí položku nabídky.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Získá index nedávno vyvolaný příkazu nabídky.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Získá posun řádku nabídek automaticky otevíraného okna.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importuje místní nabídky tlačítka ze zadaného nabídky.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Označuje, zda je panel nabídek automaticky otevírané okno v rozevíracím seznamu vyberte režim.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Označuje, zda je panel nabídek automaticky otevírané okno v režimu palety.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Určuje, zda je panel pásu karet (FALSE ve výchozím nastavení).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Určuje, zda tento panel pásu karet do normálního režimu (ve výchozím nastavení FALSE).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Načte archivované nabídky.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Obnoví zpožděné tlačítko pro uzavření nabídek automaticky otevíraného okna.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Nastaví styl tlačítka panelu nástrojů na daném indexu. (Přepíše [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Nastavuje posun řádku nabídek automaticky otevíraného okna.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Spustí časovač pro tlačítko zadané zpožděné místní nabídky.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Určuje, zda šedé postranního panelu se zobrazí, když má aplikace vzhledu Windows XP.|

## <a name="remarks"></a>Poznámky

`CMFCPopupMenuBar` Se vytvoří ve stejnou dobu jako [cmfcpopupmenu – třída](../../mfc/reference/cmfcpopupmenu-class.md) a vložené dovnitř. `CMFCPopupMenuBar` Pokrývá celou klientskou oblast `CMFCPopupMenu` objektu. Podporuje klávesnice a myši. Také komunikaci, která vstup `CMFCPopupMenu` a v okně rámce nejvyšší úrovně.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak inicializovat `CMFCPopupMenuBar` objektu z `CMFCPopupMenu` objektu. Tento fragment kódu je součástí [nakreslit Client sample](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[Cmfcbasetoolbar –](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar –](../../mfc/reference/cmfctoolbar-class.md)

[Cmfcpopupmenubar –](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpopupmenubar.h

##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate

Okamžitě přepočítá rozložení panelu stavového řádku nabídky automaticky otevíraného okna. (Přepíše [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Parametry

*bRecalcLayout*<br/>
[in] TRUE, pokud chcete automaticky přepočítat rozložení panelu stavového řádku nabídky automaticky otevírané okno; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems

Načte položky místní nabídky z nabídky prostředků.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Parametry

*uiMenuResID*<br/>
[in] Určuje ID nabídky prostředku nabídky pro načtení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu, nebo hodnotu NEPRAVDA, pokud tomu tak není.

### <a name="remarks"></a>Poznámky

##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu

Zavře tlačítko nabídky automaticky otevírané okno, které byla odložena.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Poznámky

##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu

Sestaví nabídky z místní nabídky tlačítka nabídky.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do nové nabídky.

### <a name="remarks"></a>Poznámky

##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar

Pokud je zadaný bod vyhledá panelu nástrojů.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[in] Bod na obrazovce.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do panelu nástrojů ve kterém je místo, pokud existuje, nebo hodnota NULL, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize

Určuje velikost obrázků tlačítka nabídky.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost obrázků tlačítko nabídky na panelu nástrojů.

### <a name="remarks"></a>Poznámky

##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId

Vrátí identifikátor výchozí položku nabídky.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí identifikátor výchozí položky nabídky na řádku nabídek automaticky otevíraného okna.

### <a name="remarks"></a>Poznámky

##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex

Získá index nedávno vyvolaný příkazu nabídky.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí index posledního příkazu v nabídce, která byla vyvolána.

### <a name="remarks"></a>Poznámky

##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset

Získá posun řádku nabídek automaticky otevíraného okna.

```
int GetOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí posun řádku nabídek automaticky otevíraného okna.

### <a name="remarks"></a>Poznámky

Tato hodnota se nastavuje pomocí [CMFCPopupMenuBar::SetOffset](#setoffset).

##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu

Importuje místní nabídky tlačítka ze zadaného nabídky.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
[in] V nabídce, ze kterých chcete importovat tlačítka nabídky automaticky otevírané okno.

*bShowAllCommands*<br/>
[in] Hodnota TRUE, pokud všechny příkazy v nabídce jsou importované, nebo hodnotu NEPRAVDA, pokud zřídka používané ty mohou být skryty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud tlačítka nabídky úspěšně importováno z nabídky, nebo FALSE, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode

Označuje, zda je panel nabídek automaticky otevírané okno v rozevíracím seznamu vyberte režim.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud nabídek automaticky otevíraného okna je v rozevíracím seznamu vyberte režim, nebo FALSE, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode

Označuje, zda je panel nabídek automaticky otevírané okno v režimu palety.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je povolený režim palety nebo hodnotu NEPRAVDA, pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Pokud nabídek nastaven na režim palety, položky nabídky zobrazí ve více sloupcích a omezený počet řádků.

##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel

Určuje, zda je panel pásu karet (FALSE ve výchozím nastavení).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení, která udává, že to není panel pásu karet, vrací hodnotu FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Určuje, zda tento panel pásu karet do normálního režimu (ve výchozím nastavení FALSE).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení, označující, že to není panel pásu karet do normálního režimu, vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash

Načte archivované nabídky.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
[in] Popisovač nabídky archivované načíst.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se nabídka úspěšně načteny, nebo hodnotu FALSE, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Parametr logické hodnoty označující, zda má vaše aplikace šedé postranního panelu po vzhledu Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Poznámky

Pokud tato členská proměnná je nastavena na hodnotu FALSE a vaše aplikace má vzhledu Windows XP, nakreslí rozhraní šedé postranního panelu ve vaší aplikaci.

Výchozí hodnota je FALSE.

##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu

Obnoví zpožděné tlačítko pro uzavření nabídek automaticky otevíraného okna.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Poznámky

##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle

Nastaví styl tlačítka panelu nástrojů na daném indexu. (Přepíše [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Z nuly vycházející index panelu nástrojů, jehož styl, je možné nastavit.

*nStyle*<br/>
[in] Styl tlačítka. Zobrazit [– styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md) seznam dostupných nástrojů styly.

### <a name="remarks"></a>Poznámky

##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset

Nastavuje posun řádku nabídek automaticky otevíraného okna.

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Parametry

*iOffset*<br/>
[in] Počet řádků, že by měl posun řádku nabídek automaticky otevíraného okna.

### <a name="remarks"></a>Poznámky

##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer

Spustí časovač pro tlačítko zadané zpožděné místní nabídky.

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Parametry

*pMenuButton*<br/>
[in] Ukazatel na tlačítko nabídky, pro kterou chcete nastavit zpoždění časovače.

*nDelayFactor*<br/>
[in] Faktor zpoždění, rovno alespoň jeden, kterým se má vynásobit ve standardní nabídce zpoždění (obecně mezi půl sekundy a pět sekund).

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)
