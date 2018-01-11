---
title: "Třída CMFCRibbonStatusBarPane | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3d5059adf0ebbd1ed651d57354ae73beadb919f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane – třída
`CMFCRibbonStatusBarPane` Třída implementuje na pásu karet element, který můžete přidat do stavového řádku pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Vytvoří a inicializuje `CMFCRibbonStatusBarPane` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Vrátí řetězec, který definuje nejdelší textový řetězec, který lze zobrazit v podokně bez zkrácení.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Vrátí aktuální nastavení zarovnání textu.|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Určuje, zda je animace v průběhu.|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Určuje, zda v podokně se nachází v oblasti rozšířené stavového řádku pásu karet.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Přepisuje [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Přepisuje [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definuje nejdelší textový řetězec, který lze zobrazit v podokně bez zkrácení.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Přiřadí v podokně seznamu obrázků, které lze použít pro animace.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Nastaví zarovnání textu.|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Spustí animace, který je přiřazen do podokna.|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Zastaví animace, který je přiřazen do podokna. .|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Voláno rámcem při zastavení animace, který je přiřazen do podokna.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonStatusBarPane` třídy. Tento příklad ukazuje, jak vytvořit `CMFCRibbonStatusBarPane` objektu, nastavte zarovnání textu popisku panelu Stav řádku, zadejte nejdelší text, který lze zobrazit v podokně panelu stavu bez zkrácení, připojení k panelu řádku stav seznamu obrázků, které lze použít pro nalizaci a spusťte animace.  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 Vytvořte objekt podokně ve stavovém řádku.  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nCmdID`  
 Určuje ID příkazu, který podokna.  
  
 [v]`lpszText`  
 Určuje textový řetězec, který se má zobrazit v podokně.  
  
 [v]`bIsStatic`  
 Pokud `TRUE`, v podokně Stav nemůže být zvýrazněná nebo vybrat kliknutím ji.  
  
 [v]`hIcon`  
 Určuje popisovač pro ikonu, která se zobrazí v podokně.  
  
 [v]`lpszAlmostLargeText`  
 Určuje nejdelší textový řetězec, který lze zobrazit v podokně.  
  
 [v]`hBmpAnimationList`  
 Určuje popisovač pro seznamu obrázků, který se používá pro animace.  
  
 [v]`cxAnimation`  
 Určuje šířku v pixelech na ikonu v seznamu obrázků, který se používá pro animace.  
  
 [v]`clrTrnsp`  
 Určuje průhlednou barvu obrázků v seznamu obrázků, které se používají pro animace.  
  
 [v]`uiAnimationListResID`  
 Určuje ID prostředku ze seznamu obrázků, který se používá pro animace.  
  
##  <a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText  
 Získá nejdelší textový řetězec, který můžete zobrazit v podokně panelu stavu.  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nejdelší textový řetězec, která může zobrazovat v podokně panelu stavu.  
  
##  <a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign  
 Získá aktuální nastavení zarovnání textu popisku panelu řádku stavu.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zarovnání textu, který může být jedna z následujících akcí:  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT.  
  
##  <a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation  
 Určuje, zda je animace v průběhu.  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud animace probíhá; `FALSE` jinak.  
  
##  <a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended  
 Určí, zda v podokně se nachází v oblasti rozšířené stavového řádku pásu karet.  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud podokno je na stavovém řádku rozšířené oblasti. `FALSE`jinak.  
  
##  <a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`CDC*`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation  
 Tato metoda volá Framework při ukončení animace, který je přiřazen do podokna.  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>Poznámky  
 `StopAnimation`volání metody `OnFinishAnimation` metodu, která slouží k vyčištění dat při ukončení animace.  
  
##  <a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText  
 Definujte nejdelší text, který lze zobrazit v podokně panelu stavu bez zkrácení.  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszAlmostLargeText`  
 Určuje nejdelší řetězec, který lze zobrazit v podokně Stav panelu bez zkrácení.  
  
### <a name="remarks"></a>Poznámky  
 Knihovny vypočítá velikost textu, který `lpszAlmostLargeText` určuje a změní velikost podokně odpovídajícím způsobem. Text bude zkrácen, pokud ho stále nevejde v podokně.  
  
##  <a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList  
 Připojí k panelu řádku stav seznamu obrázků, které lze použít pro animace.  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hBmpAnimationList`  
 Určuje popisovač pro seznamu obrázků.  
  
 [v]`cxAnimation`  
 Určuje šířku v pixelech rámce v seznamu obrázků.  
  
 [v]`clrTransp`  
 Určuje průhlednou barvu ze seznamu obrázků.  
  
 [v]`uiAnimationListResID`  
 Určuje ID prostředku seznamu obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud seznam obrázků se úspěšně připojil k panelu řádku stav; `FALSE` jinak.  
  
##  <a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign  
 Nastaví zarovnání textu popisku panelu řádku stavu.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nAlign`  
 Určuje zarovnání textu.  
  
### <a name="remarks"></a>Poznámky  
 `nAlign`může mít jednu z následujících hodnot:  
  
- `TA_LEFT`: zarovnání vlevo  
  
- `TA_CENTER:`zarovnání na střed  
  
- `TA_RIGHT:`Zarovnání doprava  
  
##  <a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation  
 Spustí animace, který přiřadíte do podokna.  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nFrameDelay`  
 Určuje frekvenci snímků animace, v milisekundách.  
  
 [v]`nDuration`  
 Určuje, jak dlouho přehrávání animace, v milisekundách. Použít hodnotu -1 pro nekonečné smyčce.  
  
### <a name="remarks"></a>Poznámky  
 Před voláním musíte zadat popisovač pro seznamu obrázků `StartAnimation` pomocí `SetAnimationList`.  
  
##  <a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation  
 Zastaví animace, který jste přiřadili k podokně panelu stavu.  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar – třída](../../mfc/reference/cmfcribbonstatusbar-class.md)
