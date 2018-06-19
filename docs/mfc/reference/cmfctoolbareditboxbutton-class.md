---
title: Třída CMFCToolBarEditBoxButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bddd7274feb9ecde268a94d7e9a6e857c906650
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376815"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton – třída
Tlačítka panelu nástrojů, který obsahuje ovládací prvek úprav ( [CEdit třída](../../mfc/reference/cedit-class.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Vytvoří `CMFCToolBarEditBoxButton` objektu.|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Určuje, zda uživatele lze roztáhnout tlačítko při přizpůsobení. (Přepisuje [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální. (Přepisuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek upravit v tlačítko.|  
|`CMFCToolBarEditBoxButton::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Načte první `CMFCToolBarEditBoxButton` objekt v aplikaci, která má zadaný příkaz ID.|  
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Načte text první pole panelu nástrojů ovládacích prvků pro úpravy s ID zadaného příkazu.|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Načte ID prostředku místní nabídky, která souvisí s tlačítko.|  
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Načte ohraničující obdélník upravit součástí pole tlačítko Upravit.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Vrátí ovládací prvek upravit, který je součástí tlačítko ukazatel.|  
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Načte popisovač okna, který je přidružen tlačítka panelu nástrojů. (Přepisuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Načte oblast klientské oblasti tlačítka, které musí být překreslen. (Přepisuje [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Určuje, jestli okrajem tlačítko se zobrazí, když uživatel klikne na tlačítko. (Přepisuje [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Určuje, zda pole tlačítka Upravit mají plochý stylu.|  
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracovává [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy. (Přepisuje [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Voláno rámcem při přidání tlačítka do **přizpůsobit** dialogové okno. (Přepisuje [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Voláno rámcem vypočítat velikost tlačítko pro zadané zařízení kontextu a ukotvení stavu. (Přepisuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Voláno rámcem při vložení do nového panelu nástrojů na tlačítko. (Přepisuje [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Voláno rámcem, když uživatel klikne na tlačítko myši. (Přepisuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Voláno rámcem při zpracovává nadřazené nástrojů `WM_CTLCOLOR` zprávy. (Přepisuje [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarEditBoxButton::OnDraw`|Voláno rámcem k vykreslení tlačítko pomocí zadané styly a možnosti. (Přepisuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Voláno rámcem k vykreslení tlačítko **příkazy** podokně **přizpůsobit** dialogové okno. (Přepisuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Voláno rámcem, pokud došlo ke změně globální písmo. (Přepisuje [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Voláno rámcem, pokud se přesune panel nástrojů nadřazené. (Přepisuje [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Voláno rámcem když se stane tlačítko viditelný nebo neviditelná. (Přepisuje [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Voláno rámcem, když nadřazené nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že na tlačítko Změnit velikost. (Přepisuje [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Voláno rámcem po aktualizaci jeho text popisu tlačítka panelu nástrojů nadřazené. (Přepisuje [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarEditBoxButton::Serialize`|Čte tento objekt z archivu nebo zapíše ho do archivu. (Přepisuje [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarEditBoxButton::SetACCData`|Naplní poskytnutého `CAccessibilityData` objekt usnadnění daty z tlačítka panelu nástrojů. (Přepisuje [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Nastaví text v textovém poli tlačítko.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Vyhledá na tlačítko Upravit ovládací prvek, který má zadaný příkaz ID a nastaví text v ovládacím prvku úpravy tohoto tlačítka.|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Určuje ID prostředku místní nabídky, která souvisí s tlačítko.|  
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Určuje plochý vzhled tlačítka Upravit pole v aplikaci.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Určuje styl tlačítka. (Přepisuje [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li přidat tlačítko pole na panelu nástrojů, postupujte takto:  
  
 1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.  
  
 2. Vytvořit `CMFCToolBarEditBoxButton` objektu.  
  
 3. V popisovač zpráv, který zpracovává `AFX_WM_RESETTOOLBAR` zprávy, nahraďte zástupný tlačítko tlačítka Nová pole se seznamem pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Další informace najdete v tématu [návod: vložení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCToolBarEditBoxButton` třídy. Příklad ukazuje, jak určit, že uživatel můžete stretch tlačítko během přizpůsobování, určit, že okrajem tlačítko se zobrazí, když uživatel klikne na tlačítko, nastavení textu v textové pole, zadejte plochý vzhled tlačítka Upravit pole v aplika místění a zadejte styl panelu nástrojů upravit ovládacích prvků pole.  
  
 [!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 `CMFCToolBarEditBoxButton` 
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbareditboxbutton.h  
  
##  <a name="canbestretched"></a>  CMFCToolBarEditBoxButton::CanBeStretched  
 Určuje, zda uživatele lze roztáhnout tlačítko při přizpůsobení.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení rozhraní neumožňuje uživateli při přizpůsobení funkce stretch tlačítka panelu nástrojů. Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že se uživatel k roztahování tlačítko panelu nástrojů pro úpravy pole během přizpůsobení.  
  
##  <a name="cmfctoolbareditboxbutton"></a>  CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton  
 Vytvoří [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objektu.  
  
```  
CMFCToolBarEditBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=ES_AUTOHSCROLL,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiID`  
 Určuje ID ovládacího prvku.  
  
 [v] `iImage`  
 Určuje index obrázku panelu nástrojů na nule. Bitovou kopii se nachází v [CMFCToolBarImages třída](../../mfc/reference/cmfctoolbarimages-class.md) objektu, který [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md) udržuje – třída.  
  
 [v] `dwStyle`  
 Určuje styl ovládací prvek upravit.  
  
 [v] `iWidth`  
 Určuje šířku v pixelech ovládacích prvků pro úpravy.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí konstruktor nastaví styl ovládací prvek upravit následující kombinace:  
  
 `WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL`  
  
 Výchozí šířku ovládacího prvku je 150 pixelů.  
  
##  <a name="copyfrom"></a>  CMFCToolBarEditBoxButton::CopyFrom  
 Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `src`  
 Odkaz na tlačítko zdroj ze kterého chcete zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu pro kopírování jiný tlačítka panelu nástrojů do tohoto tlačítka panelu nástrojů. `src` musí být typu `CMFCToolBarEditBoxButton`.  
  
##  <a name="createedit"></a>  CMFCToolBarEditBoxButton::CreateEdit  
 Vytvoří nový ovládací prvek upravit v tlačítko.  
  
```  
virtual CEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pWndParent`  
 Určuje nadřazeného okna ovládacích prvků pro úpravy. Nesmí být NULL.  
  
 `[in] rect`  
 Určuje velikost a umístění textové pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený textové pole; je `NULL` Pokud vytvoření ovládacího prvku a přílohy selže.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CMFCToolBarEditBoxButton` objektu ve dvou krocích. První volání konstruktoru a pak zavolají `CreateEdit`, který vytvoří ovládacího prvku úprav Windows a připojí jej k `CMFCToolBarEditBoxButton` objektu.  
  
##  <a name="getbycmd"></a>  CMFCToolBarEditBoxButton::GetByCmd  
 Načte první `CMFCToolBarEditBoxButton` objekt v aplikaci, která má zadaný příkaz ID.  
  
```  
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmd`  
 ID příkazu pro načtení tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 První `CMFCToolBarEditBoxButton` objekt v aplikaci, která má zadaný příkaz ID, nebo `NULL` Pokud takový objekt existuje.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda sdílené nástroj se používá metodami, jako [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) a [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) nastavit nebo získat text první panel nástrojů úprav pole ovládací prvek, který má zadaný příkaz ID.  
  
##  <a name="getcontentsall"></a>  CMFCToolBarEditBoxButton::GetContentsAll  
 Načte text první pole panelu nástrojů ovládacích prvků pro úpravy s ID zadaného příkazu.  
  
```  
static CString __stdcall GetContentsAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmd`  
 ID příkazu tlačítka, ze kterého chcete načíst obsah.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt, který obsahuje text první pole panelu nástrojů ovládacích prvků pro úpravy s ID zadaného příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ne, vrátí tato metoda prázdný řetězec `CMFCToolBarEditBoxButton` objekty mají ID zadaného příkazu.  
  
##  <a name="getcontextmenuid"></a>  CMFCToolBarEditBoxButton::GetContextMenuID  
 Načte ID prostředku místní nabídky, která souvisí s tlačítko.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID prostředku místní nabídky, která je přidružena tlačítko nebo 0, pokud tlačítko nemá žádné přidružené místní nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá ID prostředku při kliknutí pravým tlačítkem na tlačítko Vytvořit místní nabídky.  
  
##  <a name="geteditborder"></a>  CMFCToolBarEditBoxButton::GetEditBorder  
 Načte ohraničující obdélník upravit součástí pole tlačítko Upravit.  
  
```  
virtual void GetEditBorder(CRect& rectBorder);
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rectBorder`  
 Odkaz na `CRect` objekt, který přijme ohraničující obdélník.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte ohraničující obdélník ovládacích prvků pro úpravy v souřadnicích klienta. Velikost obdélníku v každém směru rozšiřuje o jeden bod.  
  
 [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) metoda volá tuto metodu, když ho nevykresluje ohraničení `CMFCToolBarEditBoxButton` objektu.  
  
##  <a name="geteditbox"></a>  CMFCToolBarEditBoxButton::GetEditBox  
 Vrátí ukazatel [CEdit třída](../../mfc/reference/cedit-class.md) ovládací prvek, který je součástí tlačítko.  
  
```  
CEdit* GetEditBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CEdit třída](../../mfc/reference/cedit-class.md) ovládací prvek, který obsahuje tlačítko. Je `NULL` Pokud `CEdit` řízení ještě nevytvořil.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoříte `CEdit` řízení voláním [CMFCToolBarEditBoxButton::CreateEdit](#createedit).  
  
##  <a name="gethwnd"></a>  CMFCToolBarEditBoxButton::GetHwnd  
 Načte popisovač okna, který je přidružen tlačítka panelu nástrojů.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna, který je přidružen tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Přepíše tuto metodu [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metoda vrácením popisovač okna součástí pole tlačítko Upravit pro ovládací prvek upravit.  
  
##  <a name="getinvalidaterect"></a>  CMFCToolBarEditBoxButton::GetInvalidateRect  
 Načte oblast klientské oblasti tlačítka, které musí být překreslen.  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CRect` objekt, který určuje oblast, která musí být překreslen.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), včetně v oblasti oblasti textu popisku.  
  
##  <a name="havehotborder"></a>  CMFCToolBarEditBoxButton::HaveHotBorder  
 Určuje, jestli okrajem tlačítko se zobrazí, když uživatel klikne na tlačítko.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě na tlačítko zobrazí jeho ohraničení, pokud vybraná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), vrácením nenulovou hodnotu, pokud je ovládací prvek viditelný.  
  
##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode  
 Určuje, zda pole tlačítka Upravit mají plochý stylu.  
  
```  
static BOOL __stdcall IsFlatMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítka plochý; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení mají tlačítka Upravit pole ploché stylu. Použití [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) metoda změnit plochý vzhled pro vaši aplikaci.  
  
##  <a name="notifycommand"></a>  CMFCToolBarEditBoxButton::NotifyCommand  
 Určuje, zda tlačítko zpracovává [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iNotifyCode`  
 Oznámení, které souvisí s příkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tlačítko zpracovává `WM_COMMAND` zprávy, nebo `FALSE` indikující, že zprávy musí být zpracována nadřazené panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když je odeslání [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zpráva do nadřazeného okna.  
  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním [EN_UPDATE](http://msdn.microsoft.com/library/windows/desktop/bb761687) oznámení. Pro každý textové pole se stejným ID příkaz jako tento objekt nastaví její textový popisek textový popisek tohoto objektu.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarEditBoxButton::OnAddToCustomizePage  
 Voláno rámcem při přidání tlačítka do **přizpůsobit** dialogové okno.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) tak, že zkopírujete vlastnosti z ovládacího prvku úprav pole na všech nástrojů, který má stejné ID příkazu, který jako tento objekt. Tato metoda se nic nestane. Pokud žádný panel nástrojů má ovládací prvek upravit pole, který má stejné ID příkazu, který jako tento objekt.  
  
 Další informace o **přizpůsobit** dialogové okno, najdete v části [CMFCToolBarsCustomizeDialog třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarEditBoxButton::OnChangeParentWnd  
 Voláno rámcem při vložení do nového panelu nástrojů na tlačítko.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWndParent`  
 Ukazatel do nového nadřazeného okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace třídy base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) opětovným vytvořením interní `CEdit` objektu.  
  
##  <a name="onclick"></a>  CMFCToolBarEditBoxButton::OnClick  
 Voláno rámcem, když uživatel klikne na tlačítko myši.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWnd`  
 Nepoužívá se.  
  
 [v] `bDelay`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítko zpracovává zprávy klikněte na tlačítko; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace třídy base ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) vrácením nenulovou hodnotu, pokud interní `CEdit` objekt je zobrazen.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor  
 Voláno rámcem při zpracovává nadřazené nástrojů `WM_CTLCOLOR` zprávy.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Kontext zařízení, který se zobrazí tlačítko.  
  
 [v] `nCtlColor`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro štětce globální okno.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace třídy base ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) nastavením barvu textu a pozadí kontextu zadaný zařízení na globální text a barvy pozadí v uvedeném pořadí.  
  
 Další informace o globální možnosti, které jsou k dispozici pro aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged  
 Voláno rámcem, pokud došlo ke změně globální písmo.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) tak, že změníte písmo ovládacího prvku na které globální písma.  
  
 Další informace o globální možnosti, které jsou k dispozici pro aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove  
 Voláno rámcem, pokud se přesune panel nástrojů nadřazené.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepíše výchozí implementaci třídy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) tím, že aktualizuje pozici interní `CEdit` objektu  
  
##  <a name="onshow"></a>  CMFCToolBarEditBoxButton::OnShow  
 Voláno rámcem když se stane tlačítko viditelný nebo neviditelná.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bShow`  
 Určuje, zda je tlačítko viditelná. Pokud tento parametr je `TRUE`, tlačítko je viditelné. Tlačítko, jinak hodnota není viditelný.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) tím, že pokud se zobrazuje na tlačítko `bShow` je `TRUE`. Tuto metodu, jinak hodnota skryje tlačítko.  
  
##  <a name="onsize"></a>  CMFCToolBarEditBoxButton::OnSize  
 Voláno rámcem, když nadřazené nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že na tlačítko Změnit velikost.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iSize`  
 Nové šířka tlačítko v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepíše výchozí implementaci třídy, [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), tím, že aktualizuje velikost a umístění interního `CEdit` objektu.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip  
 Voláno rámcem po aktualizaci jeho text popisu tlačítka panelu nástrojů nadřazené.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWndParent`  
 Nepoužívá se.  
  
 [v] `iButtonIndex`  
 Nepoužívá se.  
  
 [v] `wndToolTip`  
 Ovládací prvek, který zobrazí text popisku.  
  
 [out] `str`  
 A `CString` objekt, který přijme text aktualizované popisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda aktualizace text popisku; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) tím, že zobrazuje text popisku, který je přidružen upravit součástí tlačítko. Pokud interní `CEdit` objekt `NULL` nebo popisovač okna `CEdit` objekt neidentifikuje existujícího okna, tato metoda neprovede žádnou akci a vrátí `FALSE`.  
  
##  <a name="setcontents"></a>  CMFCToolBarEditBoxButton::SetContents  
 Nastaví text v textové pole.  
  
```  
virtual void SetContents(const CString& sContents);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] sContents`  
 Určuje nastavení nového textu.  
  
##  <a name="setcontentsall"></a>  CMFCToolBarEditBoxButton::SetContentsAll  
 Vyhledá [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objekt, který má zadaný příkaz ID a nastaví zadaný text v rámci jeho textové pole.  
  
```  
static BOOL SetContentsAll(
    UINT uiCmd,  
    const CString& strContents);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmd`  
 Určuje ID příkazu pro kterou se text změní ovládacího prvku.  
  
 [v] `strContents`  
 Určuje nastavení nového textu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl nastaven text; 0, pokud `CMFCToolBarEditBoxButton` ovládací prvek s ID zadaný příkaz neexistuje.  
  
##  <a name="setcontextmenuid"></a>  CMFCToolBarEditBoxButton::SetContextMenuID  
 Určuje ID prostředku místní nabídky, která souvisí s tlačítko.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmd`  
 ID prostředku v místní nabídce.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá ID prostředku vytvořit místní nabídku při kliknutí pravým tlačítkem na tlačítko panelu nástrojů.  
  
##  <a name="setflatmode"></a>  CMFCToolBarEditBoxButton::SetFlatMode  
 Určuje plochý vzhled tlačítka Upravit pole v aplikaci.  
  
```  
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bFlat`  
 Plochý pro pole tlačítka Upravit. Pokud tento parametr je `TRUE`, je povoleno plochý vzhled; v opačném případě je plochý vzhled zakázaná.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí styl ploché pro tlačítka Upravit pole je `TRUE`. Použití [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) metoda pro načtení plochý vzhled pro vaši aplikaci.  
  
##  <a name="setstyle"></a>  CMFCToolBarEditBoxButton::SetStyle  
 Určuje styl panelu nástrojů upravit ovládacích prvků pole.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nStyle`  
 Nový styl nastavit.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) k `nStyle` ho také zakáže textového pole, když je aplikace v režimu přizpůsobení a umožní, pokud aplikace není v režimu přizpůsobení (viz [CMFCToolBar: : SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) a [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). V tématu [styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md) seznam platný styl příznaky.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



