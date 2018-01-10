---
title: "Třída CMFCPopupMenuBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 002e059fd905930409cb5f2745628f8ac1dea103
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar – třída
Panel nabídek vkládat do místní nabídky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Okamžitě přepočítá rozložení podokno. (Přepisuje [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|  
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Načte položky místní nabídky z nabídky zadaný prostředek.|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Zavře tlačítko zpožděné místní nabídky.|  
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Vytvoří z místní nabídky tlačítka nabídky.|  
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Vyhledá panelu nástrojů, kde je zadaný bod.|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Určuje velikost obrázků tlačítka nabídky.|  
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Vrátí identifikátor výchozí položku nabídky.|  
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Získá index nedávno vyvolaná příkazu v nabídce.|  
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Získá posun řádku nabídek v automaticky otevřeném okně.|  
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Místní nabídky tlačítka importuje zadané nabídce.|  
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Určuje, zda nabídek v automaticky otevřeném okně je v režimu rozevíracího seznamu.|  
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Určuje, zda nabídek v automaticky otevřeném okně je v režimu palety.|  
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Určuje, zda tento panel pásu karet ( `FALSE` ve výchozím nastavení).|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Určuje, zda tento panel pásu karet v pravidelných režimu ( `FALSE` ve výchozím nastavení).|  
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Načte archivovaný nabídky.|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Obnoví zpožděné nabídky tlačítka pro zavření nabídek v automaticky otevřeném okně.|  
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Nastavuje styl tlačítka panelu nástrojů na danou indexu. (Přepisuje [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|  
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Nastaví posun řádku nabídek v automaticky otevřeném okně.|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Spustí časovač tlačítko zadaný zpožděné místní nabídky.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Určuje, zda na šedé bočním panelu se zobrazí, když aplikace má vzhledu Windows XP.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCPopupMenuBar` Je vytvořena ve stejnou dobu jako [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) a vložené uvnitř ho. `CMFCPopupMenuBar` Popisuje celý klientské oblasti `CMFCPopupMenu` objektu. Podporuje klávesnici a myš vstup. Také komunikuje, zadejte do `CMFCPopupMenu` a do nejvyšší úrovně rámce okna.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k chybě při inicializaci `CMFCPopupMenuBar` objektu z `CMFCPopupMenu` objektu. Tento fragment kódu je součástí [Ukázka kreslení klienta](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpopupmenubar.h  
  
##  <a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate  
 Okamžitě přepočítá rozložení v místní nabídce panelu podokně. (Přepisuje [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bRecalcLayout`  
 `TRUE`automaticky přepočítat rozložení v místní nabídce panelu podokně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems  
 Načte položky místní nabídky z nabídky zadaný prostředek.  
  
```  
BOOL BuildOrigItems(UINT uiMenuResID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiMenuResID`  
 Určuje ID nabídky prostředku nabídky načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` v případě úspěchu nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::CloseDelayedSubMenu  
 Zavře tlačítko místní nabídky, která byla zpožděna.  
  
```  
virtual void CloseDelayedSubMenu();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu  
 Vytvoří z místní nabídky tlačítka nabídky.  
  
```  
virtual HMENU ExportToMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač pro nové nabídky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar  
 Vyhledá panelu nástrojů, kde je zadaný bod.  
  
```  
CMFCToolBar* FindDestintationToolBar(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`point`  
 Bod na obrazovce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač na panelu nástrojů kde je bod, pokud therei je 1, nebo `NULL` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize  
 Určuje velikost obrázků tlačítka nabídky.  
  
```  
virtual CSize GetCurrentMenuImageSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost tlačítka nabídky obrázků na panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId  
 Vrátí identifikátor výchozí položku nabídky.  
  
```  
UINT GetDefaultMenuId() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí identifikátor výchozí položku nabídky v panelu nabídek v automaticky otevřeném okně.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex  
 Získá index nedávno vyvolaná příkazu v nabídce.  
  
```  
static int __stdcall GetLastCommandIndex();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí index posledního příkazu v nabídce, která metoda byla volána.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getoffset"></a>CMFCPopupMenuBar::GetOffset  
 Získá posun řádku nabídek v automaticky otevřeném okně.  
  
```  
int GetOffset() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí posun řádku nabídek v automaticky otevřeném okně.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se nastavuje pomocí [CMFCPopupMenuBar::SetOffset](#setoffset).  
  
##  <a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu  
 Místní nabídky tlačítka importuje zadané nabídce.  
  
```  
virtual BOOL ImportFromMenu(
    HMENU hMenu,  
    BOOL bShowAllCommands = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hMenu`  
 V nabídce, ze kterých chcete importovat tlačítka místní nabídky.  
  
 [v]`bShowAllCommands`  
 `TRUE`Pokud jsou všechny příkazy v nabídce k importu, nebo `FALSE` Pokud zřídka používané ty mohou být skryty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud tlačítka nabídky byly úspěšně importovány z nabídky, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode  
 Určuje, zda nabídek v automaticky otevřeném okně je v režimu rozevíracího seznamu.  
  
```  
BOOL IsDropDownListMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud nabídek v automaticky otevřeném okně je v režimu rozevíracího seznamu, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode  
 Určuje, zda nabídek v automaticky otevřeném okně je v režimu palety.  
  
```  
BOOL IsPaletteMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud palety režim povolený, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
 Pokud panelu nabídek je nastavená na režim palety, zobrazí se položky nabídky v více sloupců a omezený počet řádků.  
  
##  <a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel  
 Určuje, zda tento panel pásu karet ( `FALSE` ve výchozím nastavení).  
  
```  
virtual BOOL IsRibbonPanel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `FALSE` ve výchozím nastavení označující, že není panely pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode  
 Určuje, zda tento panel pásu karet v pravidelných režimu ( `FALSE` ve výchozím nastavení).  
  
```  
virtual BOOL IsRibbonPanelInRegularMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `FALSE` ve výchozím nastavení indikující, že to není panely pásu karet v pravidelných režimu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="loadfromhash"></a>CMFCPopupMenuBar::LoadFromHash  
 Načte archivovaný nabídky.  
  
```  
BOOL LoadFromHash(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hMenu`  
 Popisovač pro archivované nabídky načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud v nabídce se načetla úspěšně, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode  
 Parametr typu Boolean, která určuje, zda má aplikace šedé bočním panelu, když má vzhledu Windows XP.  
  
```  
BOOL m_bDisableSideBarInXPMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato proměnná člen je nastavená na `FALSE` a aplikace má vzhledu Windows XP, rozhraní nevykresluje šedé bočním panelu v aplikaci.  
  
 Výchozí hodnota je `FALSE`.  
  
##  <a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu  
 Obnoví zpožděné nabídky tlačítka pro zavření nabídek v automaticky otevřeném okně.  
  
```  
virtual void RestoreDelayedSubMenu();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle  
 Nastavuje styl tlačítka panelu nástrojů na danou indexu. (Přepisuje [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)  
  
```  
virtual void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nIndex`  
 Index založený na nule tlačítka panelu nástrojů, jehož styl má být nastavena.  
  
 [v]`nStyle`  
 Styl tlačítko. V tématu [styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md) seznam styly tlačítek panelu nástrojů k dispozici.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setoffset"></a>CMFCPopupMenuBar::SetOffset  
 Nastaví posun řádku nabídek v automaticky otevřeném okně.  
  
```  
void SetOffset(int iOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iOffset`  
 Počet řádků, že by měl posun nabídek v automaticky otevřeném okně.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer  
 Spustí časovač tlačítko zadaný zpožděné místní nabídky.  
  
```  
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,  
    int nDelayFactor = 1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pMenuButton`  
 Ukazatel na tlačítko nabídky, pro kterou chcete nastavit časovač zpoždění.  
  
 [v]`nDelayFactor`  
 Faktor zpoždění, alespoň jednu, chcete-li vynásobit doba zpoždění standardní nabídky (obvykle mezi půl sekundy a pět sekund).  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)
