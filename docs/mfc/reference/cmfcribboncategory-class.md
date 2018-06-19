---
title: Třída CMFCRibbonCategory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddHidden
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CopyFrom
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindPanelWithElem
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetContextID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetDroppedDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElementsByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFirstVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFocused
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetHighlighted
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageSize
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetItemIDsList
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLastVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLargeImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetMaxHeight
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelFromPoint
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelIndex
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentButton
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentMenuBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentRibbonBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetSmallImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabColor
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTextTopLine
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetVisibleElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HighlightPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTest
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestEx
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestScrollButtons
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsActive
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsVisible
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsWindows7Look
- AFXRIBBONCATEGORY/CMFCRibbonCategory::NotifyControlCommand
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnCancelMode
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDraw
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawImage
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawMenuBorder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnKey
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonUp
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnMouseMove
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnRTLChanged
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnScrollHorz
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnUpdateCmdUI
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RecalcLayout
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RemovePanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::ReposPanels
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetCollapseOrder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetKeys
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetTabColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCategory [MFC], CMFCRibbonCategory
- CMFCRibbonCategory [MFC], AddHidden
- CMFCRibbonCategory [MFC], AddPanel
- CMFCRibbonCategory [MFC], CopyFrom
- CMFCRibbonCategory [MFC], FindByData
- CMFCRibbonCategory [MFC], FindByID
- CMFCRibbonCategory [MFC], FindPanelWithElem
- CMFCRibbonCategory [MFC], GetContextID
- CMFCRibbonCategory [MFC], GetData
- CMFCRibbonCategory [MFC], GetDroppedDown
- CMFCRibbonCategory [MFC], GetElements
- CMFCRibbonCategory [MFC], GetElementsByID
- CMFCRibbonCategory [MFC], GetFirstVisibleElement
- CMFCRibbonCategory [MFC], GetFocused
- CMFCRibbonCategory [MFC], GetHighlighted
- CMFCRibbonCategory [MFC], GetImageCount
- CMFCRibbonCategory [MFC], GetImageSize
- CMFCRibbonCategory [MFC], GetItemIDsList
- CMFCRibbonCategory [MFC], GetLastVisibleElement
- CMFCRibbonCategory [MFC], GetLargeImages
- CMFCRibbonCategory [MFC], GetMaxHeight
- CMFCRibbonCategory [MFC], GetName
- CMFCRibbonCategory [MFC], GetPanel
- CMFCRibbonCategory [MFC], GetPanelCount
- CMFCRibbonCategory [MFC], GetPanelFromPoint
- CMFCRibbonCategory [MFC], GetPanelIndex
- CMFCRibbonCategory [MFC], GetParentButton
- CMFCRibbonCategory [MFC], GetParentMenuBar
- CMFCRibbonCategory [MFC], GetParentRibbonBar
- CMFCRibbonCategory [MFC], GetRect
- CMFCRibbonCategory [MFC], GetSmallImages
- CMFCRibbonCategory [MFC], GetTabColor
- CMFCRibbonCategory [MFC], GetTabRect
- CMFCRibbonCategory [MFC], GetTextTopLine
- CMFCRibbonCategory [MFC], GetVisibleElements
- CMFCRibbonCategory [MFC], HighlightPanel
- CMFCRibbonCategory [MFC], HitTest
- CMFCRibbonCategory [MFC], HitTestEx
- CMFCRibbonCategory [MFC], HitTestScrollButtons
- CMFCRibbonCategory [MFC], IsActive
- CMFCRibbonCategory [MFC], IsVisible
- CMFCRibbonCategory [MFC], IsWindows7Look
- CMFCRibbonCategory [MFC], NotifyControlCommand
- CMFCRibbonCategory [MFC], OnCancelMode
- CMFCRibbonCategory [MFC], OnDraw
- CMFCRibbonCategory [MFC], OnDrawImage
- CMFCRibbonCategory [MFC], OnDrawMenuBorder
- CMFCRibbonCategory [MFC], OnKey
- CMFCRibbonCategory [MFC], OnLButtonDown
- CMFCRibbonCategory [MFC], OnLButtonUp
- CMFCRibbonCategory [MFC], OnMouseMove
- CMFCRibbonCategory [MFC], OnRTLChanged
- CMFCRibbonCategory [MFC], OnScrollHorz
- CMFCRibbonCategory [MFC], OnUpdateCmdUI
- CMFCRibbonCategory [MFC], RecalcLayout
- CMFCRibbonCategory [MFC], RemovePanel
- CMFCRibbonCategory [MFC], ReposPanels
- CMFCRibbonCategory [MFC], SetCollapseOrder
- CMFCRibbonCategory [MFC], SetData
- CMFCRibbonCategory [MFC], SetKeys
- CMFCRibbonCategory [MFC], SetName
- CMFCRibbonCategory [MFC], SetTabColor
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91dbbe3b3207eba50fd9206719de2fd4afd5cc5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377967"
---
# <a name="cmfcribboncategory-class"></a>CMFCRibbonCategory – třída
`CMFCRibbonCategory` Třída implementuje kartu pásu karet, která obsahuje skupinu [pásu karet panelů](../../mfc/reference/cmfcribbonpanel-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](#cmfcribboncategory)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonCategory::AddHidden](#addhidden)|Skrytý element přidá do kategorie pásu karet.|  
|[CMFCRibbonCategory::AddPanel](#addpanel)|Přidá nový panel do kategorie pásu karet.|  
|[CMFCRibbonCategory::CopyFrom](#copyfrom)||  
|[CMFCRibbonCategory::FindByData](#findbydata)||  
|[CMFCRibbonCategory::FindByID](#findbyid)||  
|[CMFCRibbonCategory::FindPanelWithElem](#findpanelwithelem)||  
|[CMFCRibbonCategory::GetContextID](#getcontextid)|Vrací ID kontextu kategorie pásu karet.|  
|[CMFCRibbonCategory::GetData](#getdata)|Vrátí uživatelská data, která souvisí s kategorie pásu karet.|  
|[CMFCRibbonCategory::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonCategory::GetElements](#getelements)||  
|[CMFCRibbonCategory::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](#getfirstvisibleelement)|Získáte první viditelné prvek, který patří do kategorie pásu karet.|  
|[CMFCRibbonCategory::GetFocused](#getfocused)|Vrátí element cílených.|  
|[CMFCRibbonCategory::GetHighlighted](#gethighlighted)|Vrátí element zvýrazněné.|  
|[CMFCRibbonCategory::GetImageCount](#getimagecount)||  
|[CMFCRibbonCategory::GetImageSize](#getimagesize)||  
|[CMFCRibbonCategory::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonCategory::GetLastVisibleElement](#getlastvisibleelement)|Získat poslední viditelné element, který patří do kategorie pásu karet|  
|[CMFCRibbonCategory::GetLargeImages](#getlargeimages)|Vrátí odkaz na seznam velkých obrázků, které používá kategorie pásu karet.|  
|[CMFCRibbonCategory::GetMaxHeight](#getmaxheight)||  
|[CMFCRibbonCategory::GetName](#getname)||  
|[CMFCRibbonCategory::GetPanel](#getpanel)|Vrací ukazatel na panelu pásu karet, který se nachází v zadaném indexu.|  
|[CMFCRibbonCategory::GetPanelCount](#getpanelcount)|Vrátí počet panelů pásu karet v kategorii pásu karet.|  
|[CMFCRibbonCategory::GetPanelFromPoint](#getpanelfrompoint)||  
|[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)|Vrátí index panelu zadaný pásu karet.|  
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||  
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonCategory::GetParentRibbonBar](#getparentribbonbar)||  
|[CMFCRibbonCategory::GetRect](#getrect)||  
|[CMFCRibbonCategory::GetSmallImages](#getsmallimages)|Vrátí odkaz na seznam malé bitové kopie, které používá kategorii.|  
|[CMFCRibbonCategory::GetTabColor](#gettabcolor)|Vrátí aktuální barva kartě kategorie pásu karet.|  
|[CMFCRibbonCategory::GetTabRect](#gettabrect)||  
|[CMFCRibbonCategory::GetTextTopLine](#gettexttopline)||  
|[CMFCRibbonCategory::GetVisibleElements](#getvisibleelements)|Získáte všechny viditelné prvky, které patří do kategorie pásu karet.|  
|[CMFCRibbonCategory::HighlightPanel](#highlightpanel)||  
|[CMFCRibbonCategory::HitTest](#hittest)||  
|[CMFCRibbonCategory::HitTestEx](#hittestex)||  
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||  
|[CMFCRibbonCategory::IsActive](#isactive)||  
|[CMFCRibbonCategory::IsVisible](#isvisible)|Určuje, zda je viditelná kategorie pásu karet.|  
|[CMFCRibbonCategory::IsWindows7Look](#iswindows7look)|Označuje, zda má na pásu karet nadřazené Windows 7 styl vzhledu (tlačítko malá obdélníková aplikace)|  
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||  
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||  
|[CMFCRibbonCategory::OnDraw](#ondraw)||  
|[CMFCRibbonCategory::OnDrawImage](#ondrawimage)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](#ondrawmenuborder)||  
|[CMFCRibbonCategory::OnKey](#onkey)|Voláno rámcem po stisknutí tlačítka klávesnice.|  
|[CMFCRibbonCategory::OnLButtonDown](#onlbuttondown)||  
|[CMFCRibbonCategory::OnLButtonUp](#onlbuttonup)||  
|[CMFCRibbonCategory::OnMouseMove](#onmousemove)||  
|[CMFCRibbonCategory::OnRTLChanged](#onrtlchanged)||  
|[CMFCRibbonCategory::OnScrollHorz](#onscrollhorz)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||  
|[CMFCRibbonCategory::RecalcLayout](#recalclayout)||  
|[CMFCRibbonCategory::RemovePanel](#removepanel)||  
|[CMFCRibbonCategory::ReposPanels](#repospanels)||  
|[CMFCRibbonCategory::SetCollapseOrder](#setcollapseorder)|Definuje pořadí sbalit panelů pásu karet, které se nacházejí v kategorii pásu karet.|  
|[CMFCRibbonCategory::SetData](#setdata)|Ukládá data uživatelsky definované v kategorii pásu karet.|  
|[CMFCRibbonCategory::SetKeys](#setkeys)|Přiřadí keytip kategorie pásu karet.|  
|[CMFCRibbonCategory::SetName](#setname)||  
|[CMFCRibbonCategory::SetTabColor](#settabcolor)|Nastaví barvu kategorie pásu karet.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle nepřímo vytvořit kategorii pásu karet voláním [CMFCRibbonBar::AddCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory), který vrací ukazatel na nově vytvořený pásu karet kategorii. Přidání panelů do kategorie voláním [CMFCRibbonCategory::AddPanel](#addpanel).  
  
 `CMFCRibbonTab` Třída nevykresluje kategorie pásu karet. Je odvozený od [CMFCRibbonBaseElement třída](../../mfc/reference/cmfcribbonbaseelement-class.md).  
  
 Následující příklad ukazuje postup vytvoření pásu karet kategorii a přidejte do ní panelu.  
  
 `// Create a new ribbon category and get a pointer to it`  
  
 `CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory`  
  
 `(_T("&Write"),           // Category name`  
  
 `IDB_WRITE,              // Category small images (16 x 16)`  
  
 `IDB_WRITE_LARGE);   // Category large images (32 x 32)`  
  
 `// Add a panel to the new category`  
  
 `CMFCRibbonPanel* pPanel = pCategory->AddPanel (`  
  
 `_T("Clipboard"),                       // Panel name`  
  
 `m_PanelIcons.ExtractIcon (0));  // Panel icon`  
  
 Následující diagram znázorňuje obrázek domovské kategorie z RibbonApp ukázkovou aplikaci.  
  
 ![Obrázek CMFCRibbonCategory](../../mfc/reference/media/cmfcribboncategory.png "cmfcribboncategory")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCRibbonCategory`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncategory.h  
  
##  <a name="addhidden"></a>  CMFCRibbonCategory::AddHidden  
 Přidá element zadaný pásu karet do pole prvky pásu karet, které se zobrazují v dialogovém okně přizpůsobení.  
  
```  
void AddHidden(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pElem`  
 Ukazatel na pásu karet elementu.  
  
### <a name="remarks"></a>Poznámky  
 Prvky pásu karet v dialogovém okně přizpůsobení jsou příkazy, které můžete přidat na panel nástrojů Rychlý přístup.  
  
##  <a name="addpanel"></a>  CMFCRibbonCategory::AddPanel  
 Vytvoří panel pásu karet pro kategorii pásu karet.  
  
```  
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,  
    HICON hIcon = 0,  
    CRuntimeClass* pRTI = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszPanelName`  
 Ukazatel na název nového panelu pásu karet.  
  
 [v] `hIcon`  
 Zpracování na ikonu výchozí pro nové panel pásu karet.  
  
 [v] `pRTI`  
 Ukazatel na informace o třídě modulu runtime pro vlastní pás karet panel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nový panel pásu karet, pokud metoda byla úspěšná. v opačném případě `NULL` Pokud nebyl vytvořen panelu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit vlastní pás karet panely, musíte zadat jeho informace o třídě runtime v `pRTI`. Třída panely vlastní pás karet musí být odvozen od `CMFCRibbonPanel` třídy.  
  
 Pokud není dostatek místa pro zobrazení prvků pásu karet, zobrazí se na výchozí ikonu na panelu pásu karet.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `AddPanel` metoda v `CMFCRibbonCategory` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#10](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]  
  
##  <a name="cmfcribboncategory"></a>  CMFCRibbonCategory::CMFCRibbonCategory  
 Vytvoří a inicializuje [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objektu.  
  
```  
CMFCRibbonCategory(
    CMFCRibbonBar* pParenrRibbonBar,  
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16),  
    CSize sizeLargeImage = CSize(32,
    32));
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pParenrRibbonBar`  
 Ukazatel na pásu karet panelu nadřazené kategorie pásu karet.  
  
 [v] `lpszName`  
 Název kategorie pásu karet.  
  
 [v] `uiSmallImagesResID`  
 ID prostředku ze seznamu obrázků pro malé bitové kopie, které jsou používány prvky pásu karet v kategorii pásu karet.  
  
 [v] `uiLargeImagesResID`  
 ID prostředku seznam obrázků pro velkých obrázků, které jsou používány prvky pásu karet v kategorii pásu karet.  
  
 [v] `sizeSmallImage`  
 Výchozí velikost malých bitových kopií pro prvky pásu karet v kategorii pásu karet.  
  
 [v] `sizeLargeImage`  
 Výchozí velikost velkých obrázků pro prvky pásu karet v kategorii pásu karet.  
  
##  <a name="copyfrom"></a>  CMFCRibbonCategory::CopyFrom  
 Zkopíruje stav zadaného [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) na aktuální [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objektu.  
  
```  
virtual void CopyFrom(CMFCRibbonCategory& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `src`  
 Zdroj `CMFCRibbonCategory` objektu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="findbydata"></a>  CMFCRibbonCategory::FindByData  
 Načte element pásu karet spojené se zadanými daty.  
  
```  
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwData`  
 Data související s element pásu karet.  
  
 [v] `bVisibleOnly`  
 `TRUE` Zahrnout prvky pásu karet rychlý přístup prohledávání. `FALSE` vyloučit rychlý přístup prvky pásu karet v hledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet elementu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="findbyid"></a>  CMFCRibbonCategory::FindByID  
 Načte element pásu karet spojené s ID zadaný příkaz.  
  
```  
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmdID`  
 ID příkazu, související s elementem pásu karet.  
  
 [v] `bVisibleOnly`  
 `TRUE` Zahrnout prvky pásu karet rychlý přístup prohledávání. `FALSE` vyloučit rychlý přístup prvky pásu karet v hledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet elementu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="findpanelwithelem"></a>  CMFCRibbonCategory::FindPanelWithElem  
 Načte panelu pásu karet, který obsahuje element zadaný pásu karet.  
  
```  
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pElement`  
 Ukazatel na pásu karet elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet panelu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcontextid"></a>  CMFCRibbonCategory::GetContextID  
 Načte ID kontextu kategorie pásu karet.  
  
```  
UINT GetContextID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID kontextu kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 ID kontextu je 0, pokud kategorie pásu karet není kategorií kontextu pásu karet.  
  
##  <a name="getdata"></a>  CMFCRibbonCategory::GetData  
 Načte uživatelská data, která souvisí s kategorie pásu karet.  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Uživatelská data, která souvisí s kategorie pásu karet.  
  
##  <a name="getdroppeddown"></a>  CMFCRibbonCategory::GetDroppedDown  
 Načte ukazatel na pásu karet elementu, který má aktuálně jeho místní nabídky zobrazí.  
  
```  
CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet elementu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getelements"></a>  CMFCRibbonCategory::GetElements  
 Načte všechny prvky pásu karet v kategorii pásu karet.  
  
```  
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out] `arElements`  
 Odkaz na [carray –](../../mfc/reference/carray-class.md) elementů pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 V poli jsou zahrnuty prvky pásu karet, které jsou určené pro použití na panelu nástrojů Rychlý přístup.  
  
##  <a name="getelementsbyid"></a>  CMFCRibbonCategory::GetElementsByID  
 Načte všechny elementy pásu karet, které jsou spojeny s číslem ID zadaný příkaz.  
  
```  
void GetElementsByID(
    UINT uiCmdID,  
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmdID`  
 ID příkazu, související s elementem pásu karet.  
  
 [ve out] `arElements`  
 Odkaz na [carray –](../../mfc/reference/carray-class.md) elementů pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 V poli jsou zahrnuty prvky pásu karet, které jsou určené pro použití na panelu nástrojů Rychlý přístup.  
  
##  <a name="getfirstvisibleelement"></a>  CMFCRibbonCategory::GetFirstVisibleElement  
 Načte první viditelné elementu, který patří do kategorie pásu karet.  
  
```  
CMFCRibbonBaseElement* GetFirstVisibleElement() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na první prvek viditelné; může být `NULL` Pokud kategorie nemá žádné viditelné prvky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getfocused"></a>  CMFCRibbonCategory::GetFocused  
 Vrátí element cílených.  
  
```  
CMFCRibbonBaseElement* GetFocused();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na element cílených nebo `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethighlighted"></a>  CMFCRibbonCategory::GetHighlighted  
 Vrátí element zvýrazněné.  
  
```  
CMFCRibbonBaseElement* GetHighlighted();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zvýrazněné element nebo `NULL` Pokud jsou vyznačené žádné elementy.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getimagecount"></a>  CMFCRibbonCategory::GetImageCount  
 Načte množství obrázků v seznamu zadanou bitovou kopii, která je součástí kategorie pásu karet.  
  
```  
int GetImageCount(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bIsLargeImage`  
 `TRUE` pro počet bitových kopií v seznamu velký obrázek; `FALSE` pro počet bitových kopií v seznamu malý obrázek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet obrázků v seznamu zadanou bitovou kopii.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getimagesize"></a>  CMFCRibbonCategory::GetImageSize  
 Získá velikost obrázku v seznamu zadanou bitovou kopii, která je součástí kategorie pásu karet.  
  
```  
CSize GetImageSize(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bIsLargeImage`  
 `TRUE` pro velikost velkých obrázků; `FALSE` pro velikost malých obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost obrázku v seznamu zadanou bitovou kopii.  
  
### <a name="remarks"></a>Poznámky  
 Velikost načíst zahrnuje měřítko globální bitové kopie.  
  
##  <a name="getitemidslist"></a>  CMFCRibbonCategory::GetItemIDsList  
 Načte ID příkazu pro prvky pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
```  
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,  
    BOOL bHiddenOnly = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `lstItems`  
 Seznam ID příkazu pro prvky pásu karet v kategorii pásu karet.  
  
 [v] `bHiddenOnly`  
 `TRUE` vyloučit prvky pásu karet zobrazují na pásu karet panelů v kategorii pásu karet; `FALSE` zahrnout všechny prvky pásu karet v kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlargeimages"></a>  CMFCRibbonCategory::GetLargeImages  
 Načte seznam velkých obrázků, které jsou obsaženy v kategorii pásu karet.  
  
```  
CMFCToolBarImages& GetLargeImages();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Seznam velkých obrázků, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="getlastvisibleelement"></a>  CMFCRibbonCategory::GetLastVisibleElement  
 Načte poslední viditelné elementu, který patří do kategorie pásu karet.  
  
```  
CMFCRibbonBaseElement* GetLastVisibleElement() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na posledním elementem viditelné; může být `NULL` Pokud kategorie nemá žádné viditelné prvky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getmaxheight"></a>  CMFCRibbonCategory::GetMaxHeight  
 Načte maximální výšku panelů pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
```  
int GetMaxHeight(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro panely pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální výška panelů pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota načíst zahrnuje výšku horní a dolní okraj pro panely pásu karet.  
  
##  <a name="getname"></a>  CMFCRibbonCategory::GetName  
 Načte název kategorie pásu karet.  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanel"></a>  CMFCRibbonCategory::GetPanel  
 Vrací ukazatel na panelu pásu karet, který se nachází v zadaném indexu.  
  
```  
CMFCRibbonPanel* GetPanel(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Index založený na nule panelu pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na panelu pásu karet, který se nachází v zadaném indexu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vyvolána výjimka `nIndex` je mimo rozsah.  
  
##  <a name="getpanelcount"></a>  CMFCRibbonCategory::GetPanelCount  
 Vrátí počet panelů pásu karet v kategorii pásu karet.  
  
```  
int GetPanelCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet panelů pásu karet v kategorii pásu karet.  
  
##  <a name="getpanelfrompoint"></a>  CMFCRibbonCategory::GetPanelFromPoint  
 Načte ukazatel na panelu pásu karet, pokud se zadaný bod nachází v ní.  
  
```  
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice x a y ukazatele, relativně k levém horním rohu okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet panelu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Jsou testovány pouze panelů pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="getpanelindex"></a>  CMFCRibbonCategory::GetPanelIndex  
 Načte index založený na nule panelu zadaný pásu karet.  
  
```  
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pPanel`  
 Ukazatel na panelu pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index nule panelu zadaný pásu karet, pokud metoda byla úspěšná. jinak-1.  
  
### <a name="remarks"></a>Poznámky  
 Prohledají se jenom panelů pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="getparentbutton"></a>  CMFCRibbonCategory::GetParentButton  
 Načte nadřazeného elementu pásu karet kategorie pásu karet.  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na nadřazený element pásu karet, nebo `NULL` Pokud neexistuje žádný nadřazený prvek.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getparentmenubar"></a>  CMFCRibbonCategory::GetParentMenuBar  
 Vrací ukazatel na panelu nabídek nadřazené `CMFCRibbonCategory` objektu.  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí obsah `m_pParentMenuBar` chráněný člen.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getparentribbonbar"></a>  CMFCRibbonCategory::GetParentRibbonBar  
 Načte panelu nadřazené pásu karet pro kategorii pásu karet.  
  
```  
CMFCRibbonBar* GetParentRibbonBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na panelu nadřazené pásu karet pro kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrect"></a>  CMFCRibbonCategory::GetRect  
 Načte obdélník zobrazení pro kategorii pásu karet.  
  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélník zobrazení pro kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Obdélník zobrazení pro kategorii pásu karet nezahrnuje kartě kategorie.  
  
##  <a name="getsmallimages"></a>  CMFCRibbonCategory::GetSmallImages  
 Načte seznam malé bitové kopie, které jsou obsaženy v kategorii pásu karet.  
  
```  
CMFCToolBarImages& GetSmallImages();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Seznam malé bitové kopie, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="gettabcolor"></a>  CMFCRibbonCategory::GetTabColor  
 Vrátí aktuální barva kartě kategorie pásu karet.  
  
```  
AFX_RibbonCategoryColor GetTabColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální barva kartě kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota může být jedna z následujících výčtové hodnoty:  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
##  <a name="gettabrect"></a>  CMFCRibbonCategory::GetTabRect  
 Načte obdélník zobrazení karty kategorie pásu karet.  
  
```  
CRect GetTabRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélník zobrazení karty kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettexttopline"></a>  CMFCRibbonCategory::GetTextTopLine  
 Načte svislé umístění textu tlačítka pásu karet v kategorii pásu karet, které zobrazí velkých obrázků.  
  
```  
int GetTextTopLine() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Svislé umístění textu v pixelech tlačítek pásu karet, které zobrazí velkých obrázků.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getvisibleelements"></a>  CMFCRibbonCategory::GetVisibleElements  
 Načte všechny viditelné prvky, které patří do kategorie pásu karet.  
  
```  
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,  
    CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Parametry  
 `arElements`  
 Pole všechny prvky viditelné.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="highlightpanel"></a>  CMFCRibbonCategory::HighlightPanel  
 Označuje panelu zadaný pásu karet.  
  
```  
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pHLPanel`  
 Ukazatel na panelu pásu karet, abyste měli na očích.  
  
 [v] `point`  
 Souřadnice x a y ukazatele, relativně k levém horním rohu okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na panelu dříve zvýrazněná pásu karet. v opačném případě `NULL` zvýrazněna žádné panely pásu karet, když tato metoda je volána.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o zvýraznění panely pásu karet najdete v tématu [CMFCRibbonPanel::Highlight](../../mfc/reference/cmfcribbonpanel-class.md#highlight).  
  
##  <a name="hittest"></a>  CMFCRibbonCategory::HitTest  
 Načte ukazatel na pásu karet elementu, pokud se zadaný bod nachází v ní.  
  
```  
CMFCRibbonBaseElement* HitTest(
    CPoint point,  
    BOOL bCheckPanelCaption = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice x a y ukazatel myši, relativně k levém horním rohu okna.  
  
 [v] `bCheckPanelCaption`  
 `TRUE` k testování titulek panely pásu karet; `FALSE` vyloučit titulek panely pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet elementu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Jsou testovány pouze prvky pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="hittestex"></a>  CMFCRibbonCategory::HitTestEx  
 Načte index založený na nule elementu pásu karet, pokud se zadaný bod nachází v ní.  
  
```  
int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice x a y ukazatel myši, relativně k levém horním rohu okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index počítaný od nuly pásu karet elementu, pokud metoda byla úspěšná. jinak-1.  
  
### <a name="remarks"></a>Poznámky  
 Jsou testovány pouze prvky pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="hittestscrollbuttons"></a>  CMFCRibbonCategory::HitTestScrollButtons  
 Pokud bod spadá do kategorie pásu karet tlačítko doleva nebo doprava posouvání, vrací ukazatel na toto tlačítko.  
  
```  
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Bod, který chcete otestovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `point` spadá do ohraničující obdélník buď doleva nebo doprava tlačítko pásu karet kategorie, vrací ukazatel na toto tlačítko nebo, jinak vrátí `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isactive"></a>  CMFCRibbonCategory::IsActive  
 Určuje, zda kategorie pásu karet je aktivní kategorie na panelu pásu karet.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je aktivní kategorie; kategorie pásu karet v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Kategorie active pásu karet zobrazuje jeho panely pásu karet.  
  
##  <a name="isvisible"></a>  CMFCRibbonCategory::IsVisible  
 Určuje, zda je viditelná kategorie pásu karet.  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je viditelná; kategorie pásu karet v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Kategorie pásu karet, které jsou viditelné zobrazit na kartě kategorie.  
  
##  <a name="iswindows7look"></a>  CMFCRibbonCategory::IsWindows7Look  
 Označuje, zda má na pásu karet nadřazené Windows 7, podívejte se (tlačítko malá obdélníková aplikace).  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud má nadřazený pásu karet Windows 7 vypadat; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="notifycontrolcommand"></a>  CMFCRibbonCategory::NotifyControlCommand  
 Přináší zprávou příkazu wm_notify – všechny `CMFCRibbonPanel` elementů v `CMFCRibbonCategory` dokud zpracovává zprávy.  
  
```  
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,  
    int nNotifyCode,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bAccelerator`  
 `TRUE` Pokud tento příkaz pochází z akcelerátor, nebo `FALSE` jinak.  
  
 [v] `nNotifyCode`  
 Kód oznámení.  
  
 [v] `wParam`  
 Pole WPARAM zprávy.  
  
 [v] `lParam`  
 Pole LPARAM zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud zpráva bylo zpracováno, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncancelmode"></a>  CMFCRibbonCategory::OnCancelMode  
 Vyvolá Storno režimu ve všech `CMFCRibbonPanel` prvky `CMFCRibbonCategory`.  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>  CMFCRibbonCategory::OnDraw  
 Voláno rámcem k vykreslení kategorie pásu karet.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawimage"></a>  CMFCRibbonCategory::OnDrawImage  
 Voláno rámcem k vykreslení zadanou bitovou kopii na pásu karet kategorii.  
  
```  
virtual BOOL OnDrawImage(
    CDC* pDC,  
    CRect rect,  
    CMFCRibbonBaseElement* pElement,  
    BOOL bIsLargeImage,  
    BOOL nImageIndex,  
    BOOL bCenter);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro bitovou kopii.  
  
 [v] `rect`  
 Obdélník zobrazení pro bitovou kopii.  
  
 [v] `pElement`  
 Ukazatel na pásu karet elementu, který obsahuje bitovou kopii.  
  
 [v] `bIsLargeImage`  
 `TRUE` Pokud je bitová kopie velké; `FALSE` Pokud bitovou kopii je malá velikost.  
  
 [v] `nImageIndex`  
 Index bitové kopie v poli bitovou kopii, která je součástí kategorie pásu karet nule.  
  
 [v] `bCenter`  
 `TRUE` na střed obrázku v obdélníku zobrazení; `FALSE` kreslení obrázku v levém horním rohu obdélníku zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawmenuborder"></a>  CMFCRibbonCategory::OnDrawMenuBorder  
 Voláno rámcem k vykreslení ohraničení místní nabídky.  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCRibbonPanelMenuBar* pMenuBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Tento parametr není používán.  
  
 [v] `pMenuBar`  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci. Potlačí tuto metodu k vykreslení ohraničení místní nabídky.  
  
##  <a name="onkey"></a>  CMFCRibbonCategory::OnKey  
 Voláno rámcem po stisknutí tlačítka klávesnice.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
 `nChar`  
 Virtuální kód klíče pro klíč, který uživatel stisknutí tlačítka.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttondown"></a>  CMFCRibbonCategory::OnLButtonDown  
 Voláno rámcem načíst prvek pásu karet v rámci Zadaný bod po stisknutí levé tlačítko.  
  
```  
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice x a y ukazatel myši, relativně k levém horním rohu okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pásu karet elementu, pokud metoda byla úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttonup"></a>  CMFCRibbonCategory::OnLButtonUp  
 Voláno rámcem, když uživatel uvolní levým tlačítkem myši a je ukazatel myši nad kategorie pásu karet.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice x a y ukazatele, relativně k levém horním rohu okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onmousemove"></a>  CMFCRibbonCategory::OnMouseMove  
 Voláno rámcem při umístění ukazatele na panelu pásu karet za účelem aktualizace zobrazení kategorie pásu karet.  
  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice x a y ukazatele, relativně k levém horním rohu okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrtlchanged"></a>  CMFCRibbonCategory::OnRTLChanged  
 Voláno rámcem při změně rozložení směr.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bIsRTL`  
 `TRUE` Pokud je rozložení-doleva; `FALSE` Pokud je rozložení zleva doprava.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda upraví rozložení všech panelů pásu karet a prvky pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
##  <a name="onscrollhorz"></a>  CMFCRibbonCategory::OnScrollHorz  
 Posune kategorie pásu karet ve vodorovném směru.  
  
```  
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,  
    int nScrollOffset = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bScrollLeft`  
 `TRUE` Posun vlevo. `FALSE` k se posuňte doprava.  
  
 [v] `nScrollOffset`  
 Posuv vzdálenost v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se přesune kategorie pásu karet ve vodorovném směru; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdatecmdui"></a>  CMFCRibbonCategory::OnUpdateCmdUI  
 Volání `OnUpdateCmdUI` – členská funkce v každém `CMFCRibbonPanel` prvky `CMFCRibbonCategory` k povolení nebo zakázání prvky uživatelského rozhraní v nich.  
  
```  
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,  
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pCmdUI`  
 Ukazatel `CMFCRibbonCmdUI` objekt, který určuje, které prvky uživatelského rozhraní mají být povoleny a které mají být zakázána.  
  
 [v] `pTarget`  
 Ukazatel na okno, které řídí povolení nebo zákaz prvků uživatelského rozhraní.  
  
 [v] `bDisableIfNoHndler`  
 `TRUE` zakázat uživatelské rozhraní položky, pokud žádná obslužná rutina je definována v mapy zpráv; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="recalclayout"></a>  CMFCRibbonCategory::RecalcLayout  
 Upraví rozložení všech ovládacích prvků na pásu karet kategorii.  
  
```  
virtual void RecalcLayout(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removepanel"></a>  CMFCRibbonCategory::RemovePanel  
 Odebere panely pásu karet z kategorie pásu karet.  
  
```cpp  
BOOL RemovePanel(
    int nIndex,  
    BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIndex`  
 Číslo indexu panelu odebrat. Získá voláním [CMFCRibbonCategory::GetPanelIndex](#getpanelindex) metoda.  
  
 [v] `bDelete`  
 `TRUE` objekt panel odstranit z paměti; `FALSE` k odebrání objektu panely bez jeho odstranění.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném `FALSE`.  
  
##  <a name="repospanels"></a>  CMFCRibbonCategory::ReposPanels  
 Upraví rozložení všech ovládacích prvků na panely pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
```  
virtual void ReposPanels(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro panely pásu karet, které jsou obsaženy v kategorii pásu karet.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcollapseorder"></a>  CMFCRibbonCategory::SetCollapseOrder  
 Definuje pořadí, ve kterém sbalit panelů pásu karet kategorie pásu karet.  
  
```  
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `arCollapseOrder`  
 Určuje pořadí sbalit. Toto pole obsahuje počítaný od nuly indexy panelů pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Knihovny definuje pořadí sbalit. Toto chování však můžete přizpůsobit a poskytovat seznam indexy, který určuje pořadí Sbalit kategorii.  
  
 Když kategorii zjistí, že je sbalit panel pásu karet, hledá na další prvek v zadaného seznamu. Pokud seznam je prázdný nebo jste nezadali dostatečný počet elementů, kategorii používá interní algoritmus.  
  
 Například kategorie má tři panely pásu karet a lze sbalit několikrát dokud všechny panely ve plně sbalené stavu. Můžete nastavit následující pořadí Sbalit: 0, 0, 2, 2. V takovém případě kategorii bude sbalit panel 0 dvakrát, panelu 2 dvakrát. Na panelu, který má index 1 zůstává rozbalen.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `SetCollapseOrder` metoda v `CMFCRibbonCategory` třídy. Příklad ukazuje, jak vytvořit pole pro sbalit pořadí a jak nastavit pořadí sbalit kategorie pásu karet.  
  
 [!code-cpp[NVC_MFC_RibbonApp#13](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]  
  
##  <a name="setdata"></a>  CMFCRibbonCategory::SetData  
 Nastaví uživatelem definované datové přidruženou kategorie pásu karet.  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwData`  
 Uživatelská data.  
  
##  <a name="setkeys"></a>  CMFCRibbonCategory::SetKeys  
 Přiřadí keytip kategorie pásu karet.  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszKeys`  
 Keytip text.  
  
### <a name="remarks"></a>Poznámky  
 Popisy tlačítek se zobrazí, když uživatel stiskne klávesu Alt nebo F10 klíč.  
  
##  <a name="setname"></a>  CMFCRibbonCategory::SetName  
 Název a keytip přiřadí kategorie pásu karet.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszName`  
 Název a keytip kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li nastavit keytip pro kategorii pásu karet, připojte nového řádku – řídicí sekvence následované znaky keytip k `lpszName`.  
  
##  <a name="settabcolor"></a>  CMFCRibbonCategory::SetTabColor  
 Nastaví barvu kategorie pásu karet.  
  
```  
void SetTabColor(AFX_RibbonCategoryColor color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Určuje barvu nové kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Barva může být jedna z následujících hodnot:  
  
-   AFX_CategoryColor_None  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
