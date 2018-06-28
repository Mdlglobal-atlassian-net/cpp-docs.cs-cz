---
title: Třída CMFCRibbonStatusBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 256dbd6978b2d25cebb8496b6aa71763356f3637
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038100"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar – třída
`CMFCRibbonStatusBar` Třída implementuje ovládacích prvků na panelu stavu, která může zobrazovat prvky pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Přidá element dynamické stavového pásu karet.|  
|[CMFCRibbonStatusBar::AddElement](#addelement)|Přidá nového elementu pásu karet na stavovém řádku pásu karet.|  
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Přidá element pásu karet do oblasti rozšířené stavového řádku pásu karet.|  
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Přidá Oddělovač stavového pásu karet.|  
|[CMFCRibbonStatusBar::Create](#create)|Vytvoří stavového řádku pásu karet.|  
|[CMFCRibbonStatusBar::CreateEx](#createex)|Vytvoří stavového řádku pásu karet pomocí rozšířených stylu.|  
|[CMFCRibbonStatusBar::FindByID](#findbyid)||  
|[CMFCRibbonStatusBar::FindElement](#findelement)|Vrací ukazatel na elementu, který má zadaný příkaz ID.|  
|[CMFCRibbonStatusBar::GetCount](#getcount)|Vrátí počet prvků, které se nacházejí v oblasti hlavního panelu Stav pásu karet.|  
|[CMFCRibbonStatusBar::GetElement](#getelement)|Vrací ukazatel na element, který se nachází na zadaný index.|  
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Vrátí počet prvků, které se nacházejí v oblasti rozšířené stavového řádku pásu karet.|  
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Vrací ukazatel na element, který se nachází na zadaný index v oblasti rozšířené stavového řádku pásu karet.|  
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCRibbonStatusBar::GetSpace](#getspace)||  
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||  
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||  
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Určuje, jestli je povolený režim informace na pásu karet stavový řádek.|  
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Přepisuje [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|  
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Odebere všechny elementy z pásu karet stavový řádek.|  
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Odebere element, který má zadaný příkaz ID z pásu karet stavový řádek.|  
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Povolí nebo zakáže režimu informace na pásu karet stavový řádek.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Zobrazí informace o řetězec, který se zobrazí na pásu karet stavovém řádku když je povolený režim informace.|  
  
## <a name="remarks"></a>Poznámky  
 Uživatelé mohou změnit viditelnost prvky pásu karet na stavovém řádku pásu karet pomocí předdefinovaných kontextové nabídky na pásu karet stavový řádek. Můžete přidat nebo odebrat elementy dynamicky.  
  
 Pás karet stavového řádku má dvě oblasti: hlavní oblasti a rozšířené oblasti. Rozšířené oblasti se zobrazí na pravé straně panelu Stav pásu karet a zobrazí se barvu než hlavní oblasti.  
  
 Obvykle oblasti hlavního panelu Stav zobrazí oznámení o stavu, a oblasti Rozšířené ovládací prvky zobrazení. Oblasti rozšířené zůstává stejně dlouho viditelná, když uživatel změní stavový řádek pásu karet.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCRibbonStatusBar` třídy. Tento příklad ukazuje, jak přidat nového elementu pásu karet na stavovém řádku pásu karet, přidá prvek pásu karet do oblasti rozšířené na stavovém řádku pásu karet, přidejte oddělovač a povolte regulární režimu na pásu karet stavový řádek.  
  
 [!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribbonstatusbar.h  
  
##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement  
 Přidá element dynamické stavového pásu karet.  
  
```  
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pElement*  
 Ukazatel na dynamické elementu.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od regulární elementy dynamických elementů nejsou přizpůsobitelné a v nabídce Upravit stavový řádek je nezobrazí.  
  
##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement  
 Přidá nového elementu pásu karet na stavovém řádku pásu karet.  
  
```  
void AddElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pElement*  
 Ukazatel na přidaný prvek.  
  
 [v] *lpszLabel*  
 Text popisku elementu.  
  
 [v] *bIsVisible*  
 `TRUE` Pokud chcete přidat jako viditelná, element `FALSE` Pokud chcete přidat prvek jako skrytá.  
  
##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement  
 Přidá element pásu karet do oblasti rozšířené stavového řádku pásu karet.  
  
```  
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pElement*  
 Ukazatel na přidaný prvek.  
  
 [v] *lpszLabel*  
 Textový popisek elementu.  
  
 [v] *bIsVisible*  
 `TRUE` Pokud chcete přidat jako viditelná, element `FALSE` Pokud chcete přidat prvek jako skrytá.  
  
### <a name="remarks"></a>Poznámky  
 Rozšířené oblast je na pravé straně ovládacího panelu stavu.  
  
##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator  
 Přidá Oddělovač stavového pásu karet.  
  
```  
void AddSeparator();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework přidá oddělovače za metodu [CMFCRibbonStatusBar::AddElement](#addelement). Vloží posledním elementem.  
  
##  <a name="create"></a>  CMFCRibbonStatusBar::Create  
 Vytvoří stavového řádku pásu karet.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pParentWnd*  
 Ukazatel do nadřazeného okna.  
  
 [v] *dwStyle*  
 Logická nebo kombinace styly ovládacího prvku.  
  
 [v] *nID*  
 ID ovládacího prvku na stavovém řádku.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud stavový řádek je vytvořen úspěšně, `FALSE` jinak.  
  
##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx  
 Vytvoří stavového řádku pásu karet, který má rozšířené stylu.  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle=0,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Ukazatel do nadřazeného okna.  
  
 *dwCtrlStyle*  
 Logická nebo kombinace další styly pro vytvoření objektu panelu stavu.  
  
 *dwStyle*  
 Styl ovládacího prvku na stavovém řádku.  
  
 *nID*  
 ID ovládacího prvku na stavovém řádku.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud stavový řádek je vytvořen úspěšně, `FALSE` jinak.  
  
##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiCmdID*  
 [v] *BOOL*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement  
 Vrací ukazatel na elementu, který má zadaný příkaz ID.  
  
```  
CMFCRibbonBaseElement* FindElement(UINT uiID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiID*  
 ID elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na elementu, který má zadaný příkaz ID. `NULL` Pokud neexistuje žádný takový prvek.  
  
##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount  
 Vrátí počet prvků, které se nacházejí v oblasti hlavního panelu Stav pásu karet.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů, které se nacházejí v oblasti hlavního panelu Stav pásu karet.  
  
##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement  
 Vrací ukazatel na element, který se nachází na zadaný index.  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nIndex*  
 Určuje index počítaný od nuly elementu, který je umístěný v oblasti hlavního panelu řízení stavu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na element, který se nachází v zadaném indexu. `NULL` Pokud index je záporný nebo větší než počet elementů ve stavovém řádku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount  
 Vrátí počet prvků, které se nacházejí v oblasti rozšířené stavového řádku pásu karet.  
  
```  
int GetExCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů, které se nacházejí v oblasti rozšířené stavového řádku pásu karet.  
  
##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement  
 Vrací ukazatel na element, který se nachází na zadaný index v oblasti rozšířené stavového řádku pásu karet. Rozšířené oblast je na pravé straně ovládacího panelu stavu.  
  
```  
CMFCRibbonBaseElement* GetExElement(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nIndex*  
 Určuje index elementu, který je umístěný v oblasti rozšířené ovládacího panelu Stav založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na element, který se nachází na zadaný index v oblasti rozšířené stavového řádku pásu karet. `NULL` Pokud *nIndex* je záporný nebo větší než počet elementů v oblasti rozšířené stavového řádku pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] *Rect –*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSpace() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsBottomFrame() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pElement*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode  
 Určuje, jestli je povolený režim informace na pásu karet stavový řádek.  
  
```  
BOOL IsInformationMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud stavový řádek můžete pracovat v režimu informace; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V režimu informace stavového řádku skryje všechny regulární podokna a zobrazí řetězec zprávy.  
  
##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation  
 Zobrazí řetězec, který se zobrazí na pásu karet stavovém řádku když je povolený režim informace.  
  
```  
virtual void OnDrawInformation(
    CDC* pDC,  
    CString& strInfo,  
    CRect rectInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení.  
  
 [v] *strInfo*  
 Informace o řetězce.  
  
 [v] *rectInfo*  
 Ohraničující obdélník.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled řetězec informací na stavovém řádku. Použití [CMFCRibbonStatusBar::SetInformation](#setinformation) metoda uvést do režimu informace na stavovém řádku. V tomto režimu se na stavovém řádku skryje všechny podokna a zobrazí informace o řetězec určený *strInfo*.  
  
##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll  
 Odebere všechny elementy z pásu karet stavový řádek.  
  
```  
void RemoveAll();
```  
  
##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement  
 Odebere element, který má zadaný příkaz ID z pásu karet stavový řádek.  
  
```  
BOOL RemoveElement(UINT uiID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiID*  
 ID elementu k odebrání stavový řádek.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud element se zadaným *uiID* se odebere. `FALSE` jinak.  
  
##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation  
 Povolí nebo zakáže režimu informace na pásu karet stavový řádek.  
  
```  
void SetInformation(LPCTSTR lpszInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszInfo*  
 Informace o řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte uvést do režimu informace na stavovém řádku. V tomto režimu se na stavovém řádku skryje všechny podokna a zobrazí informace o řetězec určený *lpszInfo*.  
  
 Pokud je lpszInfo `NULL`, stavový řádek přejde do režimu regulární.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
