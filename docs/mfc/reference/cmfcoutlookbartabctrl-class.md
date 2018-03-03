---
title: "Třída CMFCOutlookBarTabCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d38cfd03c9d4fe192b8c1ee7e235140dba382ddb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl – třída
Ovládacího prvku karta, která má vzhled **navigačním podokně** v aplikaci Microsoft Outlook.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Výchozí konstruktor.|  
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Přidá ovládacího prvku Windows jako novou kartu na panelu aplikace Outlook.|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Voláno rámcem k určení dimenze textové pole, která se zobrazí, když uživatel přejmenuje na kartě. (Přepisuje `CMFCBaseTabCtrl::CalcRectEdit`.)|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Voláno rámcem během operací změny velikosti k určení, zda lze zobrazit méně Outlook tlačítek stránky karty na panelu, než je aktuálně vidět.|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Voláno rámcem během operací změny velikosti k určení, zda mohou být zobrazeny další Outlook tlačítek stránky karty na panelu, než aktuálně jsou zobrazeny.|  
|[CMFCOutlookBarTabCtrl::Create](#create)|Vytvoří ovládacího prvku karta panelu aplikace Outlook.|  
|`CMFCOutlookBarTabCtrl::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Určuje, zda je povoleno, ke kterému dochází při přepínání mezi active karty animace.|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Určuje, jestli uživatel může změnit štítky text na kartě tlačítek panelu aplikace Outlook. (Přepisuje [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Voláno rámcem povolit tlačítka, který umožní uživatelům procházet tlačítek na panelu aplikace Outlook řádku.|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|V podokně, která obsahuje zadaný bod identifikuje. (Přepisuje [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Vrátí velikost ohraničení ovládacího prvku Karta aplikace Outlook.|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|Načte velikost a umístění oblast karty ovládacího prvku karta. (Přepisuje [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Určuje, zda je povoleno, ke kterému dochází při přepínání mezi active karty animace.|  
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Určuje, zda ovládacího prvku karta panelu Outlook v režimu, který emuluje aplikaci Microsoft Outlook 2003.|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Určuje, zda bod uvnitř oblasti karet. (Přepisuje [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Určuje, zda je na kartě odpojitelných. (Přepisuje [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Voláno rámcem, když na kartě Vložení nebo odebrání. (Přepisuje `CMFCBaseTabCtrl::OnChangeTabs`.)|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Voláno rámcem chcete snížit počet tlačítka karta stránek, které jsou viditelné.|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Voláno rámcem a zvýšit počet tlačítka karta stránek, které jsou viditelné.|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Zobrazí **Možnosti navigačního podokna** dialogové okno.|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Přepočítá rozložení interní ovládacího prvku karta. (Přepisuje [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Nastaví aktivní karty. (Přepisuje [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Nastaví velikost ohraničení ovládacího prvku Karta aplikace Outlook.|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Nastaví zarovnání textu popisků na kartě tlačítek panelu aplikace Outlook.|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Nastaví rastrový obrázek, který obsahuje ikony, které se zobrazí v dolní části panelu aplikace Outlook v aplikaci Outlook 2003 režimu (viz [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md)).|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit panel aplikace Outlook, který má ukotvení podporu, použijte `CMFCOutlookBar` objektu k hostování aplikace Outlook panelu Ovládací prvek karty. Další informace najdete v tématu [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k chybě při inicializaci `CMFCOutlookBarTabCtrl` objektu a pomocí různých metod v nástroji `CMFCOutlookBarTabCtrl` třídy. Tento příklad ukazuje, jak povolit místní úpravy textu popisku na kartě stránky tlačítek panelu aplikace Outlook, povolit animace, povolit scroll popisovače, které uživateli umožňuje procházet tlačítek na panelu aplikace Outlook řádku, nastavte velikost ohraničení potřeba karta Outlook Karta a nastavte zarovnání textu popisků na kartě tlačítek panelu aplikace Outlook. Tento fragment kódu je součástí [Outlook Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]  
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxoutlookbartabctrl.h  
  
##  <a name="addcontrol"></a>CMFCOutlookBarTabCtrl::AddControl  
 Přidá ovládacího prvku Windows jako novou kartu na panelu aplikace Outlook.  
  
```  
void AddControl(
    CWnd* pWndCtrl,  
    LPCTSTR lpszName,  
    int nImageID=-1,  
    BOOL bDetachable=TRUE,  
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndCtrl`  
 Ukazatel na ovládací prvek pro přidání.  
  
 [v]`lpszName`  
 Určuje název karty.  
  
 [v]`bDetachable`  
 Pokud `TRUE`, stránka bude vytvořena jako odpojitelných.  
  
 [v]`nImageID`  
 Index bitové kopie v seznamu obrázků interní bitové kopie, který se má zobrazit na nové kartě.  
  
 [v]`dwControlBarStyle`  
 Určuje, AFX_ `CBRS_`* styl zabalené ukotvení podokna.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete přidat ovládací prvek jako novou stránku panel aplikace outlook.  
  
 Tato funkce interně volá na [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).  
  
 Pokud nastavíte `bDetachable` k `TRUE`, `AddControl` interně vytvoří `CDockablePaneAdapter` objektu a zabalí přidání ovládacího prvku. Automaticky nastaví třídu runtime okno s kartami třídu runtime `CMFCOutlookBar` a třída runtime plovoucí rámce k `CMultiPaneFrameWnd`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `AddControl` metoda v `CMFCOutlookBarTabCtrl` třídy. Tento fragment kódu je součástí [Outlook Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]  
  
##  <a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowFewerPageButtons  
 Voláno rámcem během operace k určení, zda lze zobrazit méně Outlook tlačítek stránky karty na panelu, než je aktuálně vidět změny velikosti.  
  
```  
virtual BOOL CanShowFewerPageButtons() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je více než jeden tlačítko; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek karty panelu Outlook dynamicky přidá nebo odebere karty ze zobrazení v závislosti na tom, kolik místa je k dispozici. Tato metoda se používá rámcem v tomto procesu pomoct.  
  
##  <a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowMorePageButtons  
 Voláno rámcem během operace k určení, zda lze zobrazit další Outlook tlačítek stránky karty na panelu, než je aktuálně vidět změny velikosti.  
  
```  
virtual BOOL CanShowMorePageButtons() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud jsou tlačítka, která nejsou aktuálně viditelné; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek karty panelu Outlook dynamicky přidá nebo odebere karty ze zobrazení v závislosti na tom, kolik místa je k dispozici. Tato metoda se používá rámcem v tomto procesu pomoct.  
  
##  <a name="create"></a>CMFCOutlookBarTabCtrl::Create  
 Vytvoří ovládacího prvku karta panelu aplikace Outlook.  
  
```  
virtual BOOL Create(
    const CRect& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Určuje počáteční velikost a umístění v pixelech.  
  
 [v]`pParentWnd`  
 Body do nadřazeného okna. Nesmí být `NULL`.  
  
 [v]`nID`  
 ID ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v ovládacím prvku vytvořeného úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvky karet panelu outlook obvykle vytvářejí při [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md) ovládací prvky `WM_CREATE` zpráva procesu.  
  
##  <a name="enableanimation"></a>CMFCOutlookBarTabCtrl::EnableAnimation  
 Určuje, zda je povoleno, ke kterému dochází při přepínání mezi active karty animace.  
  
```  
static void EnableAnimation(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 Určuje, zda by měl být animace povoleno nebo zakázáno.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce povolení a zakázání animace. Když uživatel otevře stránky karty, snímky popisek na stránku nahoru nebo dolů Pokud je povoleno animace. Pokud je zakázána animace, stránky se stane aktivní okamžitě.  
  
 Ve výchozím nastavení je povoleno animace.  
  
##  <a name="enableinplaceedit"></a>CMFCOutlookBarTabCtrl::EnableInPlaceEdit  
 Určuje, jestli uživatel může změnit štítky text na kartě stránky tlačítek panelu aplikace Outlook.  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Pokud `TRUE`, Povolit místní úpravy textu popisku. Pokud `FALSE`, zakažte úpravy na místě.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce, které chcete povolit nebo zakázat úpravy popisků text na kartě stránky tlačítka na místě. Ve výchozím nastavení je zakázáno úpravy na místě.  
  
##  <a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::EnableScrollButtons  
 Voláno rámcem povolit scroll popisovače, které uživateli umožní přejděte pomocí tlačítek na panelu aplikace Outlook řádku.  
  
```  
void EnableScrollButtons(
    BOOL bEnable = TRUE,  
    BOOL bIsUp = TRUE,  
    BOOL bIsDown = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 Určuje, zda se zobrazí tlačítka posuvníku.  
  
 [v]`bIsUp`  
 Určuje, zda je nejvyšší scrollbar zobrazovat.  
  
 [v]`bIsDown`  
 Určuje, zda je zobrazen scrollbar dolní.  
  
### <a name="remarks"></a>Poznámky  
 Umožňuje zobrazení tlačítka posuvníku. Tato metoda je volána rámcem, když se změní kartě active obnovit tlačítka posuvníku.  
  
##  <a name="getbordersize"></a>CMFCOutlookBarTabCtrl::GetBorderSize  
 Vrátí velikost ohraničení ovládacího prvku Karta aplikace Outlook.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost ohraničení v pixelech.  
  
##  <a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::GetVisiblePageButtons  

  
```  
int GetVisiblePageButtons() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isanimation"></a>CMFCOutlookBarTabCtrl::IsAnimation  
 Určuje, zda je povoleno, ke kterému dochází při přepínání mezi active karty animace.  
  
```  
static BOOL IsAnimation();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je povoleno animace; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) funkce, které chcete povolit nebo zakázat animace.  
  
##  <a name="ismode2003"></a>CMFCOutlookBarTabCtrl::IsMode2003  
 Určuje, zda ovládacího prvku karta panelu aplikace Outlook je v režimu, který emuluje aplikaci Microsoft Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`je-li aplikace Outlook panelu Ovládací prvek karty v aplikaci Outlook 2003 režimu; v opačném případě `FALSE`;  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se nastavuje [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).  
  
##  <a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowFewerPageButtons  
 Voláno rámcem chcete snížit počet tlačítka karta stránek, které jsou viditelné.  
  
```  
virtual void OnShowFewerPageButtons();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda upraví počet tlačítek karta viditelná stránky se při změně velikosti ovládacího prvku.  
  
##  <a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowMorePageButtons  
 Voláno rámcem a zvýšit počet tlačítka karta stránek, které jsou viditelné.  
  
```  
virtual void OnShowMorePageButtons();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda upravit počet kartě stránky tlačítka, které jsou viditelné při změně velikosti ovládacího prvku.  
  
##  <a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::OnShowOptions  
 Zobrazí **Možnosti navigačního podokna** dialogové okno.  
  
```  
virtual void OnShowOptions();
```  
  
### <a name="remarks"></a>Poznámky  
 **Možnosti navigačního podokna** dialogové okno umožňuje uživateli vybrat, která karta stránky tlačítka se mají zobrazovat a pořadí, ve kterém jsou zobrazeny.  
  
 Tato metoda je volána rozhraním framework, když uživatel vybere **Možnosti navigačního podokna** položky nabídky z nabídky přizpůsobení ovládacího prvku.  
  
##  <a name="setactivetab"></a>CMFCOutlookBarTabCtrl::SetActiveTab  
 Nastaví aktivní karty. Na kartě active je ten, který je otevřený v jeho obsahu viditelné.  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iTab`  
 Index založený na nule karty otevřít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadaný karta otevřena úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Visual účinek nastavení na kartě active závisí na tom, jestli jste povolili animace. Další informace najdete v tématu [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).  
  
##  <a name="setbordersize"></a>CMFCOutlookBarTabCtrl::SetBorderSize  
 Nastaví velikost ohraničení ovládacího prvku Karta aplikace Outlook.  
  
```  
void SetBorderSize(int nBorderSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nBorderSize`  
 Určuje velikost nového ohraničení v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví novou velikost ohraničení a přepočítá rozložení okna aplikace outlook.  
  
##  <a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::SetPageButtonTextAlign  
 Nastaví zarovnání textu popisků na kartě tlačítek panelu aplikace Outlook.  
  
```  
void SetPageButtonTextAlign(
    UINT uiAlign,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiAlign`  
 Určuje zarovnání textu.  
  
 [v]`bRedraw`  
 Pokud `TRUE`, bude překreslit okno aplikace outlook.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete změnit zarovnání textu pro stránku tlačítka.  
  
 `uiAlign`může být jedna z následujících hodnot:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|TA_LEFT|Zarovnání doleva|  
|TA_CENTER|Zarovnání na střed|  
|TA_RIGHT|Zarovnání doprava|  
  
 Výchozí hodnota je TA_CENTER.  
  
##  <a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList  
 Nastaví rastrový obrázek, který obsahuje ikony, které se zobrazí v dolní části panelu aplikace Outlook v aplikaci Outlook 2003 režimu.  
  
```  
BOOL SetToolbarImageList(
    UINT uiID,  
    int cx,  
    COLORREF clrTransp=RGB(255, 0, 255));
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiID`  
 Určuje ID prostředku bitové kopie k načtení.  
  
 [v]`cx`  
 Určuje šířku obrázku v seznamu obrázků v pixelech.  
  
 [v]`clrTransp`  
 Hodnoty RGB, který určuje průhlednou barvu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` v případě úspěšného; v opačném případě vrátí `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete připojit seznamu obrázků, jejichž bitové kopie se zobrazí na tlačítka panelu nástrojů v Microsoft Office 2003 režimu. Indexy Image by měla odpovídat stránky indexy.  
  
 Tuto metodu nelze volat, pokud není v režimu Microsoft Office 2003. Další informace najdete v tématu [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
##  <a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::SetVisiblePageButtons  

  
```  
void SetVisiblePageButtons(int nVisiblePageButtons);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nVisiblePageButtons`  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCBaseTabCtrl – třída](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarPane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md)
