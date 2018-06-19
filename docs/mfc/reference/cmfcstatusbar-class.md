---
title: Třída CMFCStatusBar – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
dev_langs:
- C++
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b622ca84ca73090d609cbb557096fb75802a023
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376158"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar – třída
`CMFCStatusBar` Třída implementuje podobná stavového řádku `CStatusBar` třídy. Ale `CMFCStatusBar` třída má funkce není služeb `CStatusBar` třídy, například možnost zobrazit obrázky, animace a indikátory průběhu; a schopnost reagovat na myši poklikáním. 

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]   
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Přepisuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||  
|[CMFCStatusBar::Create](#create)|Vytvoří ovládacích pruhů a připojí jej k [CPane](../../mfc/reference/cpane-class.md) objektu. (Přepisuje [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCStatusBar::CreateEx](#createex)|Vytvoří ovládacích pruhů a připojí jej k [CPane](../../mfc/reference/cpane-class.md) objektu. (Přepisuje [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, zda jiný podokně můžete dynamicky vložen mezi v tomto podokně a nadřazeného rámce. (Přepisuje [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Povolí nebo zakáže ošetření myši poklikáním na stavovém řádku.|  
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|V podokně zadaný zobrazuje indikátor průběhu.|  
|[CMFCStatusBar::GetCount](#getcount)|Vrátí počet podokna na stavovém řádku.|  
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||  
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCStatusBar::GetItemID](#getitemid)||  
|[CMFCStatusBar::GetItemRect](#getitemrect)||  
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||  
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||  
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Vrátí styl podokně. (Přepisuje [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|  
|[CMFCStatusBar::GetPaneText](#getpanetext)||  
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Vrátí šířku v pixelech podokně zadaný stavový řádek.|  
|[CMFCStatusBar::GetTipText](#gettiptext)|Vrátí text popisu nástroje pro zadaný podokně stavový řádek.|  
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Zruší platnost zadaného podokně nebo ho překreslí jeho obsah.|  
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Voláno rámcem před vytvořením okna Windows připojených k tomuto `CWnd` objektu. (Přepisuje [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|  
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||  
|[CMFCStatusBar::SetIndicators](#setindicators)||  
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Přiřadí animace do podokna zadaný.|  
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Nastaví barvu pozadí pro zadaný podokně stavový řádek.|  
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Nastaví ikona indikátoru pro zadaný podokně stavový řádek.|  
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||  
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Nastaví aktuální průběh indikátor průběhu pro zadaný podokně stavový řádek.|  
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Nastavuje styl podokna. (Přepisuje [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|  
|[CMFCStatusBar::SetPaneText](#setpanetext)||  
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Nastaví barvu textu pro zadaný podokně stavový řádek.|  
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Nastaví šířku v pixelech podokně zadaný stavový řádek.|  
|[CMFCStatusBar::SetTipText](#settiptext)|Nastaví text popisu nástroje pro zadaný podokně stavový řádek.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Voláno rámcem, pokud ho překreslí podokně stavový řádek.|  
  
## <a name="remarks"></a>Poznámky  
 Následující diagram znázorňuje obrázek stavového řádku z [stav panelu Demo-ukázka](../../visual-cpp-samples.md) aplikace.  
  
 ![Příklad CMFCStatusBar –](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar –")  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, místní proměnné, které aplikace používá k volání různých metod `CMFCStatusBar` třídy. Tyto proměnné jsou deklarovány v StatusBarDemoView.h. Je v MainFrm.h deklarována hlavního rámce, dokument je deklarován v StatusBarDemoDoc.h a zobrazení je deklarován v StatusBarDemoView.h. Tento fragment kódu je součástí [stav panelu Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat odkaz na `CMFCStatusBar` objekt zavedením `GetStatusBar` metoda v MainFrm.h a potom voláním této metody z `GetStatusBar` metoda v StatusBarDemoView.h. Tento fragment kódu je součástí [stav panelu Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat různé metody `CMFCStatusBar` třídy v StatusBarDemoView.cpp. Konstanty jsou deklarované v MainFrm.h. Tento příklad ukazuje, jak na ikonu, a nastavte text popisku panelu řádku stav, v podokně zadaný, zobrazuje indikátor průběhu, přiřadit animace do podokna zadaný, nastavení textu a šířka podokně panelu stavu, a nastavit aktuální indikátor průběhu systému progr Indikátor ESS podokně panelu stavu. Tento fragment kódu je součástí [stav panelu Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar –](../../mfc/reference/cmfcstatusbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxstatusbar.h  
  
##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bStretch`  
 [v] `bHorz`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex  

  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIDFind`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>  CMFCStatusBar::Create  

  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pParentWnd`  
 [v] `dwStyle`  
 [v] `nID`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="createex"></a>  CMFCStatusBar::CreateEx  

  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pParentWnd`  
 [v] `dwCtrlStyle`  
 [v] `dwStyle`  
 [v] `nID`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore  

  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick  
 Povolí nebo zakáže ošetření myši poklikáním na stavovém řádku.  
  
```  
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 Pokud `TRUE`, povolit, klikněte dvakrát na zpracování myši. V opačném případě zakážete zpracování poklikejte myši.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je stavový řádek je povoleno ke zpracování dvojité kliknutí, systém Windows odešle `WM_COMMAND` oznámení společně s ID prostředku vlastníkovi pokaždé, když uživatel dvakrát klikne na panelu řádku stav řádek Stavový řádek.  
  
##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar  
 V podokně zadaný zobrazuje indikátor průběhu.  
  
```  
void EnablePaneProgressBar(
    int nIndex,  
    long nTotal=100,  
    BOOL bDisplayText=FALSE,  
    COLORREF clrBar=-1,  
    COLORREF clrBarDest=-1,  
    COLORREF clrProgressText=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně, jejichž indikátor průběhu, chcete-li povolit.  
  
 [v] `nTotal`  
 Určuje maximální hodnotu indikátor průběhu.  
  
 [v] `bDisplayText`  
 Určuje, zda má indikátoru průběhu zobrazit aktuální hodnota průběhu.  
  
 [v] `clrBar`  
 Určuje barvu pozadí indikátor průběhu.  
  
 [v] `clrBarDest`  
 Určuje sekundární barvu pozadí panelu průběhu. Použít jinou hodnotu než `clrBar` k vyplnění pomocí barev, smíšení do přechod.  
  
 [v] `clrProgressText`  
 Určuje barvu textu indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete zakázat volání panelu průběhu `EnablePaneProgressBar` s `nTotal` nastavena na hodnotu -1. Ve výchozím nastavení `nTotal` je nastavena na hodnotu 100. Proto není nutné žádné další výpočty zobrazíte průběh jako procento.  
  
 Musí předat různé hodnoty pro `clrBar` a `clrBarDest` tak, aby barvu pozadí panelu průběhu zobrazí barvu smíšení do přechod. .  
  
 Chcete-li nastavit aktuální průběh, zavolejte [CMFCStatusBar::SetPaneProgress](#setpaneprogress) metoda.  
  
##  <a name="getcount"></a>  CMFCStatusBar::GetCount  
 Načte počet podokna ve stavovém řádku.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet podokna ve stavovém řádku.  
  
##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea  

  
```  
BOOL GetDrawExtendedArea() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea  

  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rect`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID  

  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect  

  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 [v] `lpRect`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo  

  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 [v] `nID`  
 [v] `nStyle`  
 [v] `cxWidth`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress  

  
```  
long GetPaneProgress(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle  

  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText  

  
```  
void GetPaneText(
    int nIndex,  
    CString& s) const;  
  
CString GetPaneText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 [v] `s`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth  
 Načte šířku panelu stavového řádku.  
  
```  
int GetPaneWidth(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index panelu řádku stavu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka podokně panelu stavu, `nIndex` určuje; jinak hodnota nula, pokud panelu stavového řádku neexistuje.  
  
##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText  
 Načtěte text popisku panelu stavového řádku.  
  
```  
CString GetTipText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně, pro které chcete načíst text popisu nástroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Text popisku panelu stavového řádku, `nIndex` určuje. Jinak hodnota prázdnému řetězci, pokud podokno panelu Stav neexistuje pro zadaný `nIndex` nebo pokud jeho text popisu je prázdný.  
  
##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent  
 Zrušení platnosti podokně panelu stavu nebo ho překreslit jeho obsah.  
  
```  
void InvalidatePaneContent(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně, jejíž obsah má být zrušena a překreslen.  
  
### <a name="remarks"></a>Poznámky  
 Když je zrušena stavového řádku, je označen pro překreslování. Windows ho překreslí ho při `UpdateWindow` metoda odešle `WM_PAINT` zprávy do `OnPaint` metoda.  
  
##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane  
 Ho překreslit podokně stavový řádek.  
  
```  
virtual void OnDrawPane(
    CDC* pDC,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro kreslení.  
  
 [v] `pPane`  
 Ukazatel na `CMFCStatusBarPaneInfo` struktura, která obsahuje informace o podokně překreslit.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `OnDrawPane` ho překreslí v podokně s použitím kontextu zařízení `pDC` podle stylu a obsah v podokně.  
  
 Potlačí tuto metodu v `CMFCStatusBar`-odvozené třídy přizpůsobit vzhled podokno.  
  
##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow  

  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `cs`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea  

  
```  
void SetDrawExtendedArea(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bSet`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators  

  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpIDArray`  
 [v] `nIDCount`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation  
 Přiřadí animace do podokna zadaný.  
  
```  
void SetPaneAnimation(
    int nIndex,  
    HIMAGELIST hImageList,  
    UINT nFrameRate=500,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně, ke kterému chcete přiřadit k němu animace.  
  
 [v] `hImageList`  
 Určuje popisovač pro seznamu obrázků, který obsahuje snímků animace.  
  
 [v] `nFrameRate`  
 Určuje obnovovací frekvence (v milisekundách) pro animaci.  
  
 [v] `bUpdate`  
 Pokud `TRUE`, okamžitě aktualizovat obsah podokně. Jinak v podokně obsahu je aktualizována při je zrušena.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete zakázat aktuální animace, zavolejte `SetPaneAnimation` s `hImageList` nastavena na `NULL`.  
  
##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor  
 Nastaví barvu pozadí panelu řádku stavu.  
  
```  
void SetPaneBackgroundColor(
    int nIndex,  
    COLORREF clrBackground=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně pro kterou chcete nastavit novou barvu pozadí.  
  
 [v] `clrBackground`  
 Určuje barvu pozadí nové.  
  
 [v] `bUpdate`  
 Pokud `TRUE`, okamžitě aktualizovat obsah podokně. V podokně obsahu, jinak hodnota neaktualizujete, dokud v podokně zneplatněna jinou metodou.  
  
##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon  
 Nastavte ikonu podokně panelu stavu.  
  
```  
void SetPaneIcon(
    int nIndex,  
    HICON hIcon,  
    BOOL bUpdate=TRUE);

 
void SetPaneIcon(
    int nIndex,  
    HBITMAP hBmp,  
    COLORREF clrTransparent=RGB(255, 0, 255),  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně pro kterou chcete nastavit bitovou kopii.  
  
 [v] `hIcon`  
 Určuje popisovač pro ikonu Nastavit jako obrázek podokna.  
  
 [v] `bUpdate`  
 Určuje, jestli pro aktualizaci obsahu podokně okamžitě.  
  
 [v] `hBmp`  
 Určuje popisovač pro bitovou mapu nastavit jako obrázek podokna.  
  
 [v] `clrTransparent`  
 Určuje průhlednou barvu bitmapy, `hBmp` označuje.  
  
### <a name="remarks"></a>Poznámky  
 Můžete buď předat `HICON` nebo `HBITMAP` společně s průhledná barva nastavit bitové kopie v podokně. Pokud nechcete zobrazit obrázek už, předat `NULL` hodnotu jako popisovač bitové kopie.  
  
 Pokud je všechny běžící animace, [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) má nastavené, animace se zastaví.  
  
##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo  

  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 [v] `nID`  
 [v] `nStyle`  
 [v] `cxWidth`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress  
 Nastavte aktuální indikátor průběhu indikátoru průběhu pro zadaný podokně.  
  
```  
void SetPaneProgress(
    int nIndex,  
    long nCurr,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně, pro které chcete aktualizovat indikátor průběhu.  
  
 [v] `nCurr`  
 Určuje aktuální hodnota indikátoru průběhu.  
  
 [v] `bUpdate`  
 Určuje, zda by měl v podokně aktualizovat okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete aktualizovat indikátor průběhu pro indikátor průběhu v podokně zadaný, volejte tuto metodu.  
  
 Chcete-li tuto funkci použít pro dané podokně, musí volat [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) první.  
  
##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle  

  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 [v] `nStyle`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText  

  
```  
virtual BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 [v] `lpszNewText`  
 [v] `bUpdate`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor  
 Nastaví barvu textu zadaný podokna.  
  
```  
void SetPaneTextColor(
    int nIndex,  
    COLORREF clrText=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Určuje index v podokně, ke kterému chcete přiřadit nové barvy.  
  
 [v] `clrText`  
 Určuje barvu textu.  
  
 [v] `bUpdate`  
 Pokud `TRUE`, okamžitě aktualizovat obsah podokně. V podokně obsahu, jinak hodnota neaktualizujete, dokud v podokně zneplatněna jinou metodou.  
  
##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth  
 Nastavte šířku podokně panelu stavu.  
  
```  
void SetPaneWidth(
    int nIndex,  
    int cx);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Index panelu řádku stav, pro kterou chcete nastavit novou šířku.  
  
 [v] `cx`  
 Nové šířka podokně panelu stavu, v pixelech.  
  
##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText  
 Nastavte text popisku panelu řádku stav.  
  
```  
void SetTipText(
    int nIndex,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Index v podokně, ke kterému chcete přiřadit text popisku.  
  
 [v] `pszTipText`  
 Nový text popisku.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPane – třída](../../mfc/reference/cpane-class.md)   
 [CStatusBar – třída](../../mfc/reference/cstatusbar-class.md)
