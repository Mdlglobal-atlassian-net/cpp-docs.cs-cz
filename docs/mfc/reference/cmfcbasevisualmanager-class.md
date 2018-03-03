---
title: "Třída CMFCBaseVisualManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edb579cff639da9965c7214c2dd8abce8459d254
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager – třída
Vrstva mezi odvozené visual správci a rozhraní API motiv systému Windows.  
  
 `CMFCBaseVisualManager`načte UxTheme.dll, pokud je k dispozici a spravuje přístup k rozhraní API systému Windows motiv metody.  
  
 Tato třída je pouze pro interní použití.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Vytvoří a inicializuje `CMFCBaseVisualManager` objektu.|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Ovládací prvek zaškrtávací políčko nevykresluje pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Nakreslí ohraničení pole se seznamem pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Nakreslí tlačítko rozevírací pole se seznamem pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Nakreslí tlačítka pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Kreslení ovládací prvek přepínač pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Nakreslí indikátor průběhu na ovládacím panelu Stav ( [CMFCStatusBar – třída](../../mfc/reference/cmfcstatusbar-class.md)) pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Vyplní celé pozadí ovládacího prvku matrice pomocí aktuální motiv systému Windows.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Získá aktuální motiv systému Windows.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Volání `CloseThemeData` pro všechny popisovače získaných v `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Volání `OpenThemeData` k získání popisovačů pro vykreslení ovládacích prvků různých: windows, panely nástrojů, tlačítek a tak dále.|  
  
## <a name="remarks"></a>Poznámky  
 Nemáte k vytvoření objektů této třídy přímo.  
  
 Protože je základní třída pro všechny visual správce, můžete stačí zavolat [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), získání ukazatele na aktuální Visual Manager a metody pro přístup k `CMFCBaseVisualManager` pomocí tento ukazatel. Ale pokud máte k zobrazení ovládacího prvku s použitím aktuální motiv systému Windows, je lepší použít `CMFCVisualManagerWindows` rozhraní.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes  
 Volání `CloseThemeData` pro všechny popisovače získaných v `UpdateSystemColors`.  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>Poznámky  
 Pouze pro interní použití.  
  
##  <a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager  
 Vytvoří a inicializuje `CMFCBaseVisualManager` objektu.  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox  
 Ovládací prvek zaškrtávací políčko nevykresluje pomocí aktuální motiv systému Windows.  
  
```  
virtual BOOL DrawCheckBox(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    int nState,   
    BOOL bEnabled,   
    BOOL bPressed);

);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení  
  
 [v]`rect`  
 Ohraničující obdélník políčko.  
  
 [v]`bHighlighted`  
 Určuje, zda je označený políčko.  
  
 [v]`nState`  
 0 pro není zaškrtnuto, 1 pro zaškrtnuté normální  
  
 2 pro smíšený normální.  
  
 [v]`bEnabled`  
 Určuje, zda je políčko povoleno.  
  
 [v]`bPressed`  
 Určuje, zda je políčko stisknutí tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Hodnoty `nState` odpovídají následující styly zaškrtávací políčko.  
  
|nInformace|Styl zaškrtávací políčko|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder  
 Nakreslí okraj pole se seznamem pomocí aktuální motiv systému Windows.  
  
```  
virtual BOOL DrawComboBorder(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rect`  
 Ohraničující obdélník okraj pole se seznamem.  
  
 [v]`bDisabled`  
 Určuje, zda je zakázána okraj pole se seznamem.  
  
 [v]`bIsDropped`  
 Určuje, jestli je okraj pole se seznamem zahodit.  
  
 [v]`bIsHighlighted`  
 Určuje, zda je označený okraj pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
##  <a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton  
 Nakreslí tlačítko rozevírací pole se seznamem pomocí aktuální motiv systému Windows.  
  
```  
virtual BOOL DrawComboDropButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`pDC`|Ukazatel na kontextu zařízení.|  
|[v]`rect`|Ohraničující obdélník rozevírací tlačítko pole se seznamem.|  
|[v]`bDisabled`|Určuje, zda je vypnuté rozevírací tlačítko pole se seznamem.|  
|[v]`bIsDropped`|Určuje, zda je tlačítko rozevírací pole se seznamem vyřazen.|  
|[v]`bIsHighlighted`|Určuje, zda je označený rozevírací tlačítko pole se seznamem.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
##  <a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton  
 Nakreslí tlačítka pomocí aktuální motiv systému Windows.  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rect`  
 Ohraničující obdélník tlačítko.  
  
 [v]`pButton`  
 Ukazatel [CMFCButton třída](../../mfc/reference/cmfcbutton-class.md) objektu k vykreslení.  
  
 [v]`uiState`  
 Ignorovat. Stav je převzat ze `pButton`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
##  <a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton  
 Kreslení ovládací prvek přepínač pomocí aktuální motiv systému Windows.  
  
```  
virtual BOOL DrawRadioButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    BOOL bChecked,   
    BOOL bEnabled,   
    BOOL bPressed);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rect`  
 Ohraničující obdélník přepínač.  
  
 [v]`bHighlighted`  
 Určuje, zda je označený přepínač.  
  
 [v]`bChecked`  
 Určuje, jestli je zaškrtnuté přepínač.  
  
 [v]`bEnabled`  
 Určuje, zda je povoleno přepínač.  
  
 [v]`bPressed`  
 Určuje, zda je stisknutí přepínač.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
##  <a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress  
 Nakreslí indikátor průběhu na ovládací prvek panelu Stav ( [CMFCStatusBar – třída](../../mfc/reference/cmfcstatusbar-class.md)) pomocí aktuální motiv systému Windows.  
  
```  
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,   
    CMFCStatusBar* pStatusBar,   
    CRect rectProgress,   
    int nProgressTotal,   
    int nProgressCurr,  
    COLORREF clrBar,   
    COLORREF clrProgressBarDest,   
    COLORREF clrProgressText,   
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`pStatusBar`  
 Ukazatel na stavovém řádku. Tato hodnota je ignorována.  
  
 [v]`rectProgress`  
 Ohraničující obdélník indikátoru průběhu ve `pDC` souřadnice.  
  
 [v]`nProgressTotal`  
 Hodnota celkový průběh.  
  
 [v]`nProgressCurr`  
 Aktuální hodnota průběhu.  
  
 [v]`clrBar`  
 Počáteční barvu. `CMFCBaseVisualManager`to bude ignorovat. Odvozené třídy, můžete tyto informace použít pro barevné přechody.  
  
 [v]`clrProgressBarDest`  
 Koncová barva. `CMFCBaseVisualManager`to bude ignorovat. Odvozené třídy, můžete tyto informace použít pro barevné přechody.  
  
 [v]`clrProgressText`  
 Barva textu v průběhu. `CMFCBaseVisualManager`to bude ignorovat. Barva textu je definována `afxGlobalData.clrBtnText`.  
  
 [v]`bProgressText`  
 Určuje, jestli chcete-li zobrazit průběh text.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
##  <a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane  
 Vyplní celé pozadí ovládacího prvku matrice pomocí aktuální motiv systému Windows.  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`pBar`  
 Ukazatel na podokno vykreslovat jejichž pozadí.  
  
 [v]`rectClient`  
 Ohraničující obdélník oblasti, aby byla vyplněna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno rozhraní API motiv; v opačném případě `FALSE`.  
  
##  <a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme  
 Získá aktuální motiv systému Windows.  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuálně vybraná barva motivu systému Windows. Může být jedna z následujících výčtové hodnoty:  
  
- `WinXpTheme_None`-neexistuje žádné motiv povolena.  
  
- `WinXpTheme_NonStandard`-je vybrán jiný standardní motiv (tj. je vybraný motiv, ale žádné ze seznamu níže).  
  
- `WinXpTheme_Blue`-motiv modrý (vzhled Luna).  
  
- `WinXpTheme_Olive`-oliv motivu.  
  
- `WinXpTheme_Silver`-stříbrným motivu.  
  
##  <a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors  
 Volání `OpenThemeData` k získání popisovačů pro vykreslení ovládacích prvků různých: windows, panely nástrojů, tlačítek a tak dále.  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>Poznámky  
 Pouze pro interní použití.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
