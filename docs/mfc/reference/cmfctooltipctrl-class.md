---
title: "Třída CMFCToolTipCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
dev_langs: C++
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae37349599977b236f111530f170da746b44b425
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl – třída
Na základě implementace rozšířených popisek [CToolTipCtrl – třída](../../mfc/reference/ctooltipctrl-class.md). Na základě popisek `CMFCToolTipCtrl` třída může zobrazit ikony, popisek a popis. Pomocí přechodu výplně, vlastní text a barvy ohraničení, tučně, zaoblenými hranami nebo bublinách styl můžete přizpůsobit její vzhled.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolTipCtrl : public CToolTipCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Vrátí velikost ikony ve formě popisu tlačítka.|  
|[CMFCToolTipCtrl::GetParams](#getparams)|Vrátí popisek nastavení zobrazení.|  
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Ohraničení popisku pole.|  
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||  
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Zobrazí ikona ve formě popisu tlačítka.|  
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Nakreslí popisek popisek nebo vypočítá velikost popisku.|  
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Nakreslí oddělovače mezi popisku a popisu ve formě popisu tlačítka.|  
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Vyplní celé pozadí popisu tlačítka.|  
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Nastaví popis, který se má zobrazit v popisu tlačítka.|  
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||  
|[CMFCToolTipCtrl::SetLocation](#setlocation)||  
|[CMFCToolTipCtrl::SetParams](#setparams)|Určuje vzhled popisek pomocí `CMFCToolTipInfo` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `CMFCToolTipCtrl`, `CMFCToolTipInfo`, a [CTooltipManager třída](../../mfc/reference/ctooltipmanager-class.md) objekty dohromady a implementovat vlastní popisy tlačítek v aplikaci.  
  
 Například bublinách stylu popisy tlačítek, postupujte podle těchto kroků:  
  
 1. Použití [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) metoda pro inicializaci správce popisek ve vaší aplikaci.  
  
 2. Vytvoření `CMFCToolTipInfo` struktura vizuální styl, který chcete zadat:  
  
```  
CMFCToolTipInfo params;  
    params.m_bBoldLabel = FALSE;  
    params.m_bDrawDescription = FALSE;  
    params.m_bDrawIcon = FALSE;  
    params.m_bRoundedCorners = TRUE;  
    params.m_bDrawSeparator = FALSE;  
    if (m_bCustomColors)  
 {  
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

 }  
```  
3. Použití [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) metodu a nastavit vizuální styl pro všechny popisy tlačítek v aplikaci se styly definované v `CMFCToolTipInfo` objektu:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```  
Můžete také odvodit novou třídu z `CMFCToolTipCtrl` ovládací prvek popisek chování a vykreslování. Pokud chcete zadat nové třídě ovládacího prvku tooltip, použijte `CTooltipManager::SetTooltipParams` metoda:  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
Obnovit výchozí popisek třídu ovládacího prvku a vzhled popisek resetovat do výchozího stavu, zadejte hodnotu NULL v parametrech runtime třídy a popisu tlačítka informace z `SetTooltipParams`:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL,
    NULL);
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCToolTipCtrl` objektu, nastavit popis, který zobrazí popisek a nastavte šířku ovládacího prvku popisek.  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtooltipctrl.h  
  
##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl  

  
```  
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pParams`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize  
 Vrátí velikost ikony ve formě popisu tlačítka.  
  
```  
virtual CSize GetIconSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost ikony v pixelech.  
  
##  <a name="getparams"></a>CMFCToolTipCtrl::GetParams  
 Vrátí popisek nastavení zobrazení.  
  
```  
const CMFCToolTipInfo& GetParams() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální nastavení zobrazení popisu tlačítka, které jsou uloženy v [CMFCToolTipInfo třída](../../mfc/reference/cmfctooltipinfo-class.md) objektu.  
  
##  <a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder  
 Ohraničení popisku pole.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pDC`  
 Ukazatel na kontextu zařízení.  
  
 `[in] rect`  
 Ohraničující obdélník popisek.  
  
 `[in] clrLine`  
 Barva ohraničení.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě a přizpůsobení vzhledu ohraničení popisku.  
  
##  <a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription  

  
```  
virtual CSize OnDrawDescription(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 [v]`rect`  
 [v]`bCalcOnly`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawIcon  
 Zobrazí ikona ve formě popisu tlačítka.  
  
```  
virtual BOOL OnDrawIcon(
    CDC* pDC,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectImage`  
 Souřadnice ikonu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud ikonu vykreslení. V opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě zobrazíte vlastní ikonou. Je nutné přepsat [CMFCToolTipCtrl::GetIconSize](#geticonsize) povolit popisek, který správně vypočítat rozložení textu a popis.  
  
##  <a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel  
 Nakreslí popisek popisek nebo vypočítá velikost popisku.  
  
```  
virtual CSize OnDrawLabel(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pDC`  
 Ukazatel na kontextu zařízení.  
  
 `[in] rect`  
 Ohraničující obdélník popisek oblasti.  
  
 `[in] bCalcOnly`  
 Pokud `TRUE`, nebude vykreslovat popisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost popisku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled popisek popisek.  
  
##  <a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator  
 Nakreslí oddělovače mezi popisku a popisu ve formě popisu tlačítka.  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    int x1,  
    int x2,  
    int y);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`x1`  
 Vodorovné souřadnice levého konce oddělovače.  
  
 [v]`x2`  
 Vodorovné souřadnice pravého konce oddělovače.  
  
 [v]`Y`  
 Svislé souřadnice oddělovače.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nevykresluje řádku z bodu (x1, y) do bodu (x2, y).  
  
 Potlačí tuto metodu v odvozené třídě přizpůsobit vzhled oddělovače.  
  
##  <a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground  
 Vyplní celé pozadí popisu tlačítka.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect,  
    COLORREF& clrText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pDC`  
 Ukazatel na kontextu zařízení.  
  
 `[in] rect`  
 Určuje ohraničující obdélník oblasti k vyplnění.  
  
 `[in] clrText`  
 Popisek barvu popředí.  
  
 `[in] clrLine`  
 Barva ohraničení a řádek oddělovač mezi popisek a popis.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace doplní obdélníku, která je zadána `rect` s barvu nebo vzorek určeného nejnovější volání [CMFCToolTipCtrl::SetParams](#setparams).  
  
 Potlačí tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled popisek.  
  
##  <a name="setdescription"></a>CMFCToolTipCtrl::SetDescription  
 Nastaví popis, který se má zobrazit v popisu tlačítka.  
  
```  
virtual void SetDescription(const CString strDesrciption);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] strDesrciption`  
 Text popisu.  
  
### <a name="remarks"></a>Poznámky  
 Textový popis se zobrazí na popisek za oddělovačem.  
  
##  <a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth  

  
```  
void SetFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nWidthRegular`  
 [v]`nWidthLargeImage`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton  

  
```  
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pRibbonButton`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setlocation"></a>CMFCToolTipCtrl::SetLocation  

  
```  
void SetLocation(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pt`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setparams"></a>CMFCToolTipCtrl::SetParams  
 Určuje vzhled popisek pomocí [CMFCToolTipInfo třída](../../mfc/reference/cmfctooltipinfo-class.md) objektu.  
  
```  
void SetParams(CMFCToolTipInfo* pParams);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pParams`  
 Ukazatel na [CMFCToolTipInfo třída](../../mfc/reference/cmfctooltipinfo-class.md) objekt, který obsahuje parametry zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Vždy, když se zobrazí popisek, kreslení pomocí barvy a styly visual, který `pParams` určuje. Hodnota `pParams` je uložen v chráněného člena `m_Params`, který je přístupný pomocí odvozené třídy, který přepíše [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), nebo [CMFCToolTipCtrl::OnFillBackground](#onfillbackground) k údržbě Zadaný vzhled.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl – třída](../../mfc/reference/ctooltipctrl-class.md)   
 [CTooltipManager – třída](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
