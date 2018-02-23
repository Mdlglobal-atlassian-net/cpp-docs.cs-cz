---
title: "Třída CPaneDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e247d1d824d710cfa9588a01d73e1ca611d77ed
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2018
---
# <a name="cpanedialog-class"></a>CPaneDialog – třída
`CPaneDialog` Třída podporuje nemodální, lze ukotvit dialogové okno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|Výchozí konstruktor.|  
|`CPaneDialog::~CPaneDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaneDialog::Create](#create)|Dialogové okno lze ukotvit vytvoří a připojí jej k `CPaneDialog` objektu.|  
|`CPaneDialog::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CPaneDialog::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Zpracovává [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) zprávy. (Znovu definuje `CBasePane::HandleInitDialog`.)|  
|`CPaneDialog::OnEraseBkgnd`|Zpracovává [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) zprávy. (Znovu definuje [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|  
|`CPaneDialog::OnLButtonDblClk`|Zpracovává [WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) zprávy. (Znovu definuje [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|  
|`CPaneDialog::OnLButtonDown`|Zpracovává [WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) zprávy. (Znovu definuje [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|  
|`CPaneDialog::OnUpdateCmdUI`|Voláno rámcem aktualizace dialogového okna pole. (Přepisuje [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0).)|  
|`CPaneDialog::OnWindowPosChanging`|Zpracovává [WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) zprávy. (Znovu definuje [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Určuje šablonu pro dialogové okno, které je kontejneru ovládacího prvku OLE.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvořit `CPaneDialog` objektu ve dvou krocích. Nejprve vytvořte objekt v kódu. Za druhé volání [CPaneDialog::Create](#create). Musíte zadat ID platným prostředkem šablony název nebo šablony a předat ukazatel do nadřazeného okna. Proces vytvoření, jinak selže. Dialogové okno musíte zadat ws_child – a ws_visible – styl. Doporučujeme také určit ws_clipchildren – a ws_clipsiblings – styly. Další informace najdete v tématu [styly oken](styles-used-by-mfc.md#window-styles).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpanedialog.h  
  
##  <a name="create"></a>  CPaneDialog::Create  
 Vytvoří dialogové okno ukotvení a připojí jej k `CPaneDialog` objektu.  
  
```  
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID,  
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

 
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszWindowName`  
 Název dialogového okna ukotvení.  
  
 [in] `pParentWnd`  
 Body do nadřazeného okna.  
  
 [in] `bHasGripper`  
 `TRUE` Chcete-li vytvořit dialogové okno ukotvení s popiskem (úchytu); v opačném `FALSE`.  
  
 [in] `lpszTemplateName`  
 Název šablony dialogového okna prostředků.  
  
 [in] `nStyle`  
 Styl systému Windows.  
  
 [in] `nID`  
 ID ovládacího prvku.  
  
 [in] `nIDTemplate`  
 ID prostředku šablony dialogového okna.  
  
 [in] `dwTabbedStyle`  
 Styl okna s kartami, který nastane, když uživatel nastavuje tažením jiné podokně ovládacího prvku na titulek v tomto podokně ovládacího prvku. Výchozí hodnota je `AFX_CBRS_REGULAR_TABS`. Další informace najdete v části poznámky [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metoda.  
  
 [in] `dwControlBarStyle`  
 Atributy stylu Další. Výchozí hodnota je `AFX_DEFAULT_DOCKING_PANE_STYLE`. Další informace najdete v části poznámky [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Create` metoda v `CPaneDialog` třídy. Tato ukázka je součástí [nastavit velikost podokna ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog  
 Zpracovává [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) zprávy.  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `wParam`  
 Popisovač ovládací prvek, který má být vybrán výchozí klávesnice.  
  
 [in] `lParam`  
 Určuje další inicializační data.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšná. v opačném `FALSE`. Kromě toho `TRUE` nastaví fokus klávesnice do ovládacího prvku určeného `wParam` parametr; `FALSE` brání fokus klávesnice výchozí nastavení.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá tato metoda se inicializovat ovládací prvky a vzhled dialogového okna. Tato metoda volá framework předtím, než se zobrazí dialogové okno.  
  
##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo  
 Určuje šablonu pro dialogové okno, které je kontejneru ovládacího prvku OLE.  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pOccDialogInfo`  
 Ukazatel na pole šablony dialogového okna, který se používá k vytvoření objektu pole dialogového okna. Hodnota tohoto parametru je následně předán do [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda podporuje [COccManager](../../mfc/reference/coccmanager-class.md) třída, která spravuje OLE řízení lokality a ovládací prvky ActiveX. Struktura _AFX_OCC_DIALOG_INFO je definována v záhlaví souboru afxocc.h.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)   
 [Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles)



