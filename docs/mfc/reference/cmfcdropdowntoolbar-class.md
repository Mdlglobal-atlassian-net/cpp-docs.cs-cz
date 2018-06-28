---
title: Třída CMFCDropDownToolBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74005682036e0a4d15d17d147b5994864fa97378
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042115"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar – třída
Panel nástrojů, který se zobrazí, když uživatel stiskne a obsahuje tlačítka panelu nástrojů nejvyšší úrovně.  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Přepisuje `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Přepisuje [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Přepisuje [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Přepisuje `CMFCToolBar::OnSendCommand`.)|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Přepisuje [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/571a38ab-2a56-4968-9796-273516126f80).)|  
  
### <a name="remarks"></a>Poznámky  
 A `CMFCDropDownToolBar` objekt s chováním místní nabídky kombinuje vzhled panelu nástrojů. Když uživatel stiskem tlačítka a obsahuje tlačítka panelu nástrojů rozevíracího seznamu (najdete v části [CMFCDropDownToolbarButton třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), zobrazí se panel nástrojů rozevíracího seznamu a kterého uživatel může vybrat tlačítko panelu nástrojů rozevíracího seznamu tak, že k němu posouvání a uvolněním tlačítka myši tlačítko. Po výběru tlačítka na panelu nástrojů rozevíracího seznamu, že tlačítko se zobrazí jako aktuální tlačítka na panelu nástrojů nejvyšší úrovně.  
  
 Rozevírací seznam nástrojů nelze přizpůsobit nebo ukotven a nemá do stavu úplné vypnutí.  
  
 Následující obrázek znázorňuje `CMFCDropDownToolBar` objektu:  
  
 ![Příklad CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 Vytvoříte `CMFCDropDownToolBar` objekt stejným způsobem jako vytvoříte obyčejnou panelu nástrojů (v tématu [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md)).  
  
 Rozevírací seznam nástrojů vložení do nadřazené nástrojů:  
  
 1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.  
  
 2. Vytvoření `CMFCDropDownToolBarButton` objekt, který obsahuje panelu nástrojů rozevíracího seznamu (Další informace najdete v tématu [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).  
  
 3. Nahraďte zástupný tlačítka s `CMFCDropDownToolBarButton` objekt pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Další informace o tlačítka panelu nástrojů najdete v tématu [návod: vložení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md). Příklad nástrojů rozevíracího seznamu v tématu ukázkový projekt VisualStudioDemo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Create` metoda v `CMFCDropDownToolBar` třídy. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap  
 Načte obrázků panelu nástrojů z prostředků aplikace.  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiResID*  
 ID prostředku bitové mapy, který odkazuje na jeho aktivní obrázků.  
  
 [v] *uiColdResID*  
 ID prostředku bitové mapy, který odkazuje na jeho cold obrázků.  
  
 [v] *uiMenuResID*  
 ID prostředku bitové mapy, která odkazuje na Image regulární nabídky.  
  
 [v] *blokován*  
 `TRUE` Zamknout panelu nástrojů; v opačném případě `FALSE`.  
  
 [v] *uiDisabledResID*  
 ID prostředku bitové mapy, který odkazuje na jeho zakázané obrázků.  
  
 [v] *uiMenuDisabledResID*  
 ID prostředku bitové mapy, který odkazuje na Image zakázané nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda úspěšně. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda volá tuto metodu za účelem načtení bitové kopie, které jsou přidruženy panelu nástrojů. Potlačí tuto metodu za účelem provedení vlastní načítání prostředků bitové kopie.  
  
 Volání `LoadBitmapEx` metodu pro načtení další Image, po vytvoření panelu nástrojů.  
  
##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar  

  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiResID*  
 [v] *uiColdResID*  
 [v] *uiMenuResID*  
 [v] *BOOL*  
 [v] *uiDisabledResID*  
 [v] *uiMenuDisabledResID*  
 [v] *uiHotResID*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nFlags*  
 [v] *bodu*  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nFlags*  
 [v] *bodu*  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pButton*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pTarget*  
 [v] *bDisableIfNoHndler*  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



