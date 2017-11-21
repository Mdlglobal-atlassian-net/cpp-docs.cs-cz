---
title: "Třída CMFCToolBarMenuButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CompareWith
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CopyFrom
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateFromMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::EnableQuickCustomize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetCommands
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetImageRect
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPaletteRows
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HasButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HaveHotBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsClickedOnMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsDroppedDown
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsEmptyMenuAllowed
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsExclusive
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsQuickMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsTearOffMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnAfterCreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnBeforeDrag
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCalculateSize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCancelMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnChangeParentWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClick
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClickMenuItem
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnContextHelp
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDraw
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDrawOnCustomizeList
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OpenPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::ResetImageToDefault
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SaveBarState
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::Serialize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetACCData
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuOnly
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMessageWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetRadio
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetTearOff
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::DrawDocumentIcon
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarMenuButton [MFC], CMFCToolBarMenuButton
- CMFCToolBarMenuButton [MFC], CompareWith
- CMFCToolBarMenuButton [MFC], CopyFrom
- CMFCToolBarMenuButton [MFC], CreateFromMenu
- CMFCToolBarMenuButton [MFC], CreateMenu
- CMFCToolBarMenuButton [MFC], CreatePopupMenu
- CMFCToolBarMenuButton [MFC], EnableQuickCustomize
- CMFCToolBarMenuButton [MFC], GetCommands
- CMFCToolBarMenuButton [MFC], GetImageRect
- CMFCToolBarMenuButton [MFC], GetPaletteRows
- CMFCToolBarMenuButton [MFC], GetPopupMenu
- CMFCToolBarMenuButton [MFC], HasButton
- CMFCToolBarMenuButton [MFC], HaveHotBorder
- CMFCToolBarMenuButton [MFC], IsBorder
- CMFCToolBarMenuButton [MFC], IsClickedOnMenu
- CMFCToolBarMenuButton [MFC], IsDroppedDown
- CMFCToolBarMenuButton [MFC], IsEmptyMenuAllowed
- CMFCToolBarMenuButton [MFC], IsExclusive
- CMFCToolBarMenuButton [MFC], IsMenuPaletteMode
- CMFCToolBarMenuButton [MFC], IsQuickMode
- CMFCToolBarMenuButton [MFC], IsTearOffMenu
- CMFCToolBarMenuButton [MFC], OnAfterCreatePopupMenu
- CMFCToolBarMenuButton [MFC], OnBeforeDrag
- CMFCToolBarMenuButton [MFC], OnCalculateSize
- CMFCToolBarMenuButton [MFC], OnCancelMode
- CMFCToolBarMenuButton [MFC], OnChangeParentWnd
- CMFCToolBarMenuButton [MFC], OnClick
- CMFCToolBarMenuButton [MFC], OnClickMenuItem
- CMFCToolBarMenuButton [MFC], OnContextHelp
- CMFCToolBarMenuButton [MFC], OnDraw
- CMFCToolBarMenuButton [MFC], OnDrawOnCustomizeList
- CMFCToolBarMenuButton [MFC], OpenPopupMenu
- CMFCToolBarMenuButton [MFC], ResetImageToDefault
- CMFCToolBarMenuButton [MFC], SaveBarState
- CMFCToolBarMenuButton [MFC], Serialize
- CMFCToolBarMenuButton [MFC], SetACCData
- CMFCToolBarMenuButton [MFC], SetMenuOnly
- CMFCToolBarMenuButton [MFC], SetMenuPaletteMode
- CMFCToolBarMenuButton [MFC], SetMessageWnd
- CMFCToolBarMenuButton [MFC], SetRadio
- CMFCToolBarMenuButton [MFC], SetTearOff
- CMFCToolBarMenuButton [MFC], DrawDocumentIcon
- CMFCToolBarMenuButton [MFC], m_bAlwaysCallOwnerDraw
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f41fc2d55cb5aeb2a8173e9912ddb7c67c582ab9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctoolbarmenubutton-class"></a>CMFCToolBarMenuButton – třída
Tlačítka panelu nástrojů, který obsahuje místní nabídky.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](#cmfctoolbarmenubutton)|Vytvoří `CMFCToolBarMenuButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CompareWith](#comparewith)|Porovná tuto instanci poskytnutým `CMFCToolBarButton` objektu. (Přepisuje [CMFCToolBarButton::CompareWith](../../mfc/reference/cmfctoolbarbutton-class.md#comparewith).)|  
|[CMFCToolBarMenuButton::CopyFrom](#copyfrom)|Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální. (Přepisuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)|Inicializuje nabídky panelu nástrojů v nabídce zpracování systému Windows.|  
|[CMFCToolBarMenuButton::CreateMenu](#createmenu)|Vytvoří nabídky systému Windows, která se skládá z příkazů v nabídce panelu nástrojů. Vrátí popisovač do nabídky systému Windows.|  
|[CMFCToolBarMenuButton::CreatePopupMenu](#createpopupmenu)|Vytvoří objekt místní nabídky ( [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md)) zobrazení nabídky panelu nástrojů.|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](#enablequickcustomize)||  
|[CMFCToolBarMenuButton::GetCommands](#getcommands)|Poskytuje přístup jen pro čtení k seznam příkazů v nabídce panelu nástrojů.|  
|[CMFCToolBarMenuButton::GetImageRect](#getimagerect)|Načte ohraničující obdélník pro vzhled tlačítka.|  
|[CMFCToolBarMenuButton::GetPaletteRows](#getpaletterows)|Vrátí počet řádků v rozbalovací nabídce, když v nabídce v režimu palety.|  
|[CMFCToolBarMenuButton::GetPopupMenu](#getpopupmenu)|Vrací ukazatel na místní nabídky objekt, který je přidružen tlačítko.|  
|[CMFCToolBarMenuButton::HasButton](#hasbutton)||  
|[CMFCToolBarMenuButton::HaveHotBorder](#havehotborder)|Určuje, jestli okrajem tlačítko se zobrazí, když uživatel vybere tlačítko. (Přepisuje [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarMenuButton::IsBorder](#isborder)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](#isclickedonmenu)||  
|[CMFCToolBarMenuButton::IsDroppedDown](#isdroppeddown)|Určuje, zda je zobrazen v místní nabídce.|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Voláno rámcem k určení, jestli uživatel může otevřít podnabídky z vybranou položku nabídky.|  
|[CMFCToolBarMenuButton::IsExclusive](#isexclusive)|Určuje, zda tlačítko je ve výhradním režimu, to znamená, zda zůstává v rozbalovací nabídce otevřete i v případě, že přesunutí ukazatele myši jiný panelu nástrojů nebo tlačítko.|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](#ismenupalettemode)|Určuje, zda místní nabídky v režimu palety.|  
|[CMFCToolBarMenuButton::IsQuickMode](#isquickmode)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](#istearoffmenu)|Určuje, zda má v rozbalovací nabídce panel úplné vypnutí.|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](#onaftercreatepopupmenu)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](#onbeforedrag)|Určuje, zda můžete přetáhnout tlačítko. (Přepisuje [CMFCToolBarButton::OnBeforeDrag](../../mfc/reference/cmfctoolbarbutton-class.md#onbeforedrag).)|  
|[CMFCToolBarMenuButton::OnCalculateSize](#oncalculatesize)|Voláno rámcem vypočítat velikost tlačítko pro zadané zařízení kontextu a ukotvení stavu. (Přepisuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarMenuButton::OnCancelMode](#oncancelmode)|Voláno rámcem pro zpracování [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) zprávy. (Přepisuje [CMFCToolBarButton::OnCancelMode](../../mfc/reference/cmfctoolbarbutton-class.md#oncancelmode).)|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Voláno rámcem při vložení do nového panelu nástrojů na tlačítko. (Přepisuje [CMFCToolBarButton::OnChangeParentWnd](cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarMenuButton::OnClick](#onclick)|Voláno rámcem, když uživatel klikne na tlačítko myši. (Přepisuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarMenuButton::OnClickMenuItem](#onclickmenuitem)|Voláno rámcem, když uživatel vybere položka v místní nabídce.|  
|[CMFCToolBarMenuButton::OnContextHelp](#oncontexthelp)|Voláno rámcem při zpracovává nadřazené nástrojů `WM_HELPHITTEST` zprávy. (Přepisuje [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCToolBarMenuButton::OnDraw](#ondraw)|Voláno rámcem k vykreslení tlačítko pomocí zadané styly a možnosti. (Přepisuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Voláno rámcem k vykreslení tlačítko **příkazy** podokně **přizpůsobit** dialogové okno. (Přepisuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarMenuButton::OpenPopupMenu](#openpopupmenu)|Voláno rámcem, když uživatel otevře v místní nabídce.|  
|[CMFCToolBarMenuButton::ResetImageToDefault](#resetimagetodefault)|Nastaví na výchozí hodnotu bitovou kopii, která souvisí s tlačítko. (Přepisuje [CMFCToolBarButton::ResetImageToDefault](../../mfc/reference/cmfctoolbarbutton-class.md#resetimagetodefault).)|  
|[CMFCToolBarMenuButton::SaveBarState](#savebarstate)|Uloží stav tlačítka panelu nástrojů. (Přepisuje [CMFCToolBarButton::SaveBarState](../../mfc/reference/cmfctoolbarbutton-class.md#savebarstate).)|  
|[CMFCToolBarMenuButton::Serialize](#serialize)|Čte tento objekt z archivu nebo zapíše ho do archivu. (Přepisuje [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCToolBarMenuButton::SetACCData](#setaccdata)|Naplní poskytnutého `CAccessibilityData` objekt usnadnění daty z tlačítka panelu nástrojů. (Přepisuje [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|[CMFCToolBarMenuButton::SetMenuOnly](#setmenuonly)|Určuje, zda lze na tlačítko Přidat na panel nástrojů.|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)|Určuje, zda místní nabídky v režimu palety.|  
|[CMFCToolBarMenuButton::SetMessageWnd](#setmessagewnd)||  
|[CMFCToolBarMenuButton::SetRadio](#setradio)|Vynutí se tak na tlačítko nabídky panelu nástrojů zobrazí ikona, která určuje, že je vybraný.|  
|[CMFCToolBarMenuButton::SetTearOff](#settearoff)|Určuje úplné vypnutí panel ID pro místní nabídky.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](#drawdocumenticon)|Nakreslí ikonu na tlačítko nabídky.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw](#m_balwayscallownerdraw)|Pokud `TRUE`, vždy volá framework [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) při tlačítko vykreslením.|  
  
## <a name="remarks"></a>Poznámky  
 A `CMFCToolBarMenuButton` může se objevit jako nabídky, položku nabídky, která má dílčí nabídky, tlačítko, které provede příkaz nebo se zobrazí nabídka nebo tlačítko, které se zobrazí pouze nabídka. Určit chování a vzhled tlačítka nabídky tak, že zadáte parametry, například bitové kopie, text, nabídky popisovač a příkaz ID, který je přidružen tlačítko v konstruktoru `CMFCToolbarMenuButton::CMFCToolbarMenuButton`.  
  
 Vlastní třída odvozená z `CMFCToolbarMenuButton` třída musí použít [declare_serial –](run-time-object-model-services.md#declare_serial) makro. [DECLARE_DYNCREATE –](run-time-object-model-services.md#declare_dyncreate) makro vygeneruje chybu aplikace zavře.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat `CMFCToolBarMenuButton` objektu. Kód ukazuje, jak určit, že v rozevírací nabídce je v režimu palety, a zadejte ID pro panel úplné vypnutí, který se vytvoří, když uživatel nastavuje tažením tlačítko nabídky z řádku nabídek. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#10](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarmenubutton.h  
  
##  <a name="cmfctoolbarmenubutton"></a>CMFCToolBarMenuButton::CMFCToolBarMenuButton  
 Vytvoří `CMFCToolBarMenuButton` objektu.  
  
```  
CMFCToolBarMenuButton();
CMFCToolBarMenuButton(const CMFCToolBarMenuButton& src);

CMFCToolBarMenuButton(
    UINT uiID,  
    HMENU hMenu,  
    int iImage,  
    LPCTSTR lpszText=NULL,  
    BOOL bUserButton=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
 Existující `CMFCToolBarMenuButton` objekt, který se má zkopírovat do této `CMFCToolBarMenuButton` objektu.  
  
 [v]`uiID`  
 ID příkazu Spustit, když uživatel klikne na tlačítko; nebo ( `UINT`) -1 pro tlačítko nabídky, které není přímo provedení příkazu.  
  
 [v]`hMenu`  
 Popisovač pro nabídky; nebo `NULL` není-li na tlačítko nabídky.  
  
 [v]`iImage`  
 Index obrázku pro tlačítko; nebo -1, pokud toto tlačítko nemá ikonu nebo používá na ikonu pro příkaz určeného `uiID`. Index je stejný pro každou `CMFCToolBarImages` objektu ve vaší aplikaci.  
  
 [v]`lpszText`  
 Text tlačítka nabídky panelu nástrojů.  
  
 [v]`bUserButton`  
 `TRUE`Pokud na tlačítko zobrazí uživatelská image; `FALSE` případě na tlačítko zobrazí předdefinované obrázku přidružený k příkazu určeného `uiID`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `uiID` je platné ID příkazu, tlačítko provede tento příkaz, když uživatel klikne ho. Pokud `hMenu` je platný nabídky popisovač, tlačítko poskytuje rozevírací nabídky, když se objeví v panelu nástrojů nebo podnabídky, když se objeví v nabídce. Pokud oba `uiID` a `hMenu` jsou platné, tlačítko je tlačítko rozdělení s část, která provede příkaz, když uživatel klikne na něm a část s šipka dolů, která bude rozevírací nabídce když uživatel klikne na něm. Ale pokud `hMenu` je platný, uživatel nebude moci kliknout na tlačítko o provedení příkazu, když na tlačítko se vloží do nabídky.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarMenuButton` třídy. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#9](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_2.cpp)]  
  
##  <a name="comparewith"></a>CMFCToolBarMenuButton::CompareWith  

  
```  
virtual BOOL CompareWith(const CMFCToolBarButton& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`other`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="copyfrom"></a>CMFCToolBarMenuButton::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="createfrommenu"></a>CMFCToolBarMenuButton::CreateFromMenu  
 Inicializuje nabídky panelu nástrojů v nabídce zpracování systému Windows.  
  
```  
virtual void CreateFromMenu(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hMenu`  
 Popisovač pro nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Tlačítka panelu nástrojů nabídky můžete zobrazit podnabídky rozevíracího seznamu.  
  
 Rozhraní framework volá tuto metodu za účelem inicializace příkazy v podnabídce z nabídky.  
  
##  <a name="createmenu"></a>CMFCToolBarMenuButton::CreateMenu  
 Vytvoří nabídky, která se skládá z příkazů v nabídce panelu nástrojů. Vrátí popisovač do nabídky.  
  
```  
virtual HMENU CreateMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A zpracování do nabídky Pokud úspěch. `NULL`Pokud je prázdný seznam příkazů, které jsou přidružené k nabídce tlačítka panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Můžete přepsat tuto metodu v odvozené třídě a přizpůsobit způsob, jakým se vygeneruje v nabídce.  
  
##  <a name="createpopupmenu"></a>CMFCToolBarMenuButton::CreatePopupMenu  
 Vytvoří `CMFCPopupMenu` objekt, který chcete zobrazit v nabídce panelu nástrojů.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CMFCPopupMenu` objekt, který zobrazí rozevírací nabídky přidružené k nabídce tlačítka panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem Příprava zobrazení rozevírací nabídky přidružené tlačítko.  
  
 Výchozí implementace právě vytvoří a vrátí novou `CMFCPopupMenu` objektu. Potlačí tuto metodu, pokud chcete použít typ odvozené [CMFCPopupMenu třídy](cmfcpopupmenu-class.md) nebo provádět další inicializace.  
  
##  <a name="drawdocumenticon"></a>CMFCToolBarMenuButton::DrawDocumentIcon  
 Nakreslí ikonou dokumentu na tlačítko nabídky.  
  
```  
void DrawDocumentIcon(
    CDC* pDC,  
    const CRect& rectImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontext zařízení.  
  
 [v]`rectImage`  
 Souřadnice ohraničujícího rámečku bitové kopie.  
  
 [v]`hIcon`  
 Popisovač pro ikonu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přebírá ikonou dokumentu a nevykresluje na tlačítko nabídky zarovnaný na střed v oblasti určeného `rectImage`.  
  
##  <a name="enablequickcustomize"></a>CMFCToolBarMenuButton::EnableQuickCustomize  

  
```  
void EnableQuickCustomize();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasbutton"></a>CMFCToolBarMenuButton::HasButton  

  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="havehotborder"></a>CMFCToolBarMenuButton::HaveHotBorder  

  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isborder"></a>CMFCToolBarMenuButton::IsBorder  

  
```  
virtual BOOL IsBorder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isclickedonmenu"></a>CMFCToolBarMenuButton::IsClickedOnMenu  

  
```  
BOOL IsClickedOnMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isquickmode"></a>CMFCToolBarMenuButton::IsQuickMode  

  
```  
BOOL IsQuickMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcommands"></a>CMFCToolBarMenuButton::GetCommands  
 Poskytuje přístup jen pro čtení k seznam příkazů v nabídce panelu nástrojů.  
  
```  
const CObList& GetCommands() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const odkaz na [CObList třída](../../mfc/reference/coblist-class.md) objekt, který obsahuje kolekci [CMFCToolBarButton třída](../../mfc/reference/cmfctoolbarbutton-class.md) objekty.  
  
### <a name="remarks"></a>Poznámky  
 Tlačítka panelu nástrojů nabídky můžete zobrazit podnabídky. Můžete zadat seznam příkazů v podnabídce v konstruktoru nebo v [CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu) jako popisovač pro nabídky ( `HMENU`). V nabídce jsou převedeny na seznam objektů, které jsou odvozeny od [CMFCToolBarButton třída](../../mfc/reference/cmfctoolbarbutton-class.md) a uložená v interní `CObList` objektu. Tento seznam můžete přejít pomocí voláním této metody.  
  
##  <a name="getimagerect"></a>CMFCToolBarMenuButton::GetImageRect  
 Načte ohraničující obdélník pro vzhled tlačítka.  
  
```  
void GetImageRect(CRect& rectImage);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectImage`  
 Odkaz na `CRect` objekt, který přijme souřadnice ohraničujícího rámečku bitové kopie.  
  
##  <a name="getpaletterows"></a>CMFCToolBarMenuButton::GetPaletteRows  
 Když v nabídce v režimu palety, vrátí počet řádků v rozevírací nabídce.  
  
```  
int GetPaletteRows() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků v paletě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tlačítko nabídky je nastavená na režim palety, zobrazí se položky nabídky v více sloupců s pouze omezený počet řádků. Voláním této metody lze získat počet řádků. Můžete povolit nebo zakázat režim palety a zadejte počet řádků pomocí [CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode).  
  
##  <a name="getpopupmenu"></a>CMFCToolBarMenuButton::GetPopupMenu  
 Vrátí ukazatel [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objekt, který reprezentuje rozevírací nabídky tlačítka.  
  
```  
CMFCPopupMenu* GetPopupMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objekt, který byl vytvořen při rozhraní obrázek podnabídce tlačítka nabídky panelu nástrojů; `NULL` Pokud žádné dílčí se zobrazí.  
  
### <a name="remarks"></a>Poznámky  
 Když tlačítka nabídky panelu nástrojů zobrazí rozevírací nabídky, tlačítko vytvoří [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objekt představující v nabídce. Volat tuto metodu za účelem získání ukazatele na `CMFCPopupMenu` objektu. Vrácený ukazatel nesmí uložit, protože je dočasný a stává neplatným při zavření v rozevírací nabídce.  
  
##  <a name="isdroppeddown"></a>CMFCToolBarMenuButton::IsDroppedDown  
 Označuje, zda je aktuálně zobrazený v místní nabídce.  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tlačítko nabídky panelu nástrojů zobrazí jeho dílčí; v opačném případě `FALSE`.  
  
##  <a name="isemptymenuallowed"></a>CMFCToolBarMenuButton::IsEmptyMenuAllowed  
 Určuje, zda položky nabídky ukazuje dílčích prázdný.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud rozhraní otevře podnabídky z aktuálně vybranou položku nabídky i tehdy, je-li podnabídky prázdná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když se uživatel pokusí otevřít podnabídky z aktuálně vybranou položku nabídky. Pokud je prázdný podnabídky a `IsEmptyMenuAllowed` vrátí `FALSE`, podnabídky neotevře.  
  
 Výchozí implementace vrací `FALSE`. Potlačí tuto metodu za účelem přizpůsobení toto chování.  
  
##  <a name="isexclusive"></a>CMFCToolBarMenuButton::IsExclusive  
 Určuje, zda tlačítko je ve výhradním režimu.  
  
```  
virtual BOOL IsExclusive() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tlačítko funguje ve výhradním režimu; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel otevře místní nabídky pro tlačítka a pak se posouvá ukazatel myši nad jiné tlačítko panelu nástrojů nebo nabídky, místní nabídky zavře, není-li na tlačítko ve výhradním režimu.  
  
 Výchozí implementace vždy vrátí `FALSE`. Potlačí tuto metodu v odvozené třídě, pokud chcete zapnout výhradním režimu.  
  
##  <a name="ismenupalettemode"></a>CMFCToolBarMenuButton::IsMenuPaletteMode  
 Určuje, zda v rozevírací nabídce v režimu palety.  
  
```  
BOOL IsMenuPaletteMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povolen režim palety, jinak `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tlačítko nabídky je nastavená na režim palety, zobrazí se v více sloupců s pouze omezený počet řádků položky nabídky. Voláním této metody lze získat počet řádků. Můžete povolit nebo zakázat režim palety voláním [CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode).  
  
##  <a name="istearoffmenu"></a>CMFCToolBarMenuButton::IsTearOffMenu  
 Označuje, zda má v rozevírací nabídce panel úplné vypnutí.  
  
```  
virtual BOOL IsTearOffMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`má-li na tlačítko nabídky panelu nástrojů úplné vypnutí panel; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Povolit funkci úplné vypnout a nastavit úplné vypnutí panelu ID, volání [CMFCToolBarMenuButton::SetTearOff](#settearoff).  
  
##  <a name="m_balwayscallownerdraw"></a>CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw  
 Určuje, zda vždy volá framework [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) při tlačítko vykreslením.  
  
```  
static BOOL m_bAlwaysCallOwnerDraw;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je tato proměnná člen nastavená na `TRUE`, tlačítko vždy volá [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) metodu pro zobrazení obrázek na tlačítko. Když `m_bAlwaysCallOwnerDraw` je `FALSE`, na tlačítku nakreslí obrázek, pokud je předdefinovaná bitovou kopii. Jinak zavolá `OnDrawMenuImage`.  
  
##  <a name="onaftercreatepopupmenu"></a>CMFCToolBarMenuButton::OnAfterCreatePopupMenu  

  
```  
virtual void OnAfterCreatePopupMenu();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onbeforedrag"></a>CMFCToolBarMenuButton::OnBeforeDrag  

  
```  
virtual BOOL OnBeforeDrag() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncalculatesize"></a>CMFCToolBarMenuButton::OnCalculateSize  

  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 [v]`sizeDefault`  
 [v]`bHorz`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncancelmode"></a>CMFCToolBarMenuButton::OnCancelMode  

  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarMenuButton::OnChangeParentWnd  

  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onclick"></a>CMFCToolBarMenuButton::OnClick  

  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 [v]`bDelay`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onclickmenuitem"></a>CMFCToolBarMenuButton::OnClickMenuItem  
 Voláno rámcem, když uživatel vybere v rozevírací nabídce.  
  
```  
virtual BOOL OnClickMenuItem();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `FALSE`Pokud rozhraní pokračovat v nabídce výchozí položky zpracování; v opačném případě `TRUE`. Výchozí implementace vždy vrátí `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Po kliknutí na položku nabídky, rozhraní provede příkaz, který je přidružena k této položce.  
  
 Chcete-li přizpůsobit zpracování položky nabídky, přepište `OnClickMenuItem` v třídy odvozené od `CMFCToolBarMenuButton` třídy. Je nutné přepsat [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) a nahraďte tlačítka nabídky, které vyžadují zvláštní zpracování s instancí odvozené třídy.  
  
##  <a name="oncontexthelp"></a>CMFCToolBarMenuButton::OnContextHelp  

  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>CMFCToolBarMenuButton::OnDraw  

  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 [v]`rect`  
 [v]`pImages`  
 [v]`bHorz`  
 [v]`bCustomizeMode`  
 [v]`bHighlight`  
 [v]`bDrawBorder`  
 [v]`bGrayDisabledButtons`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarMenuButton::OnDrawOnCustomizeList  

  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 [v]`rect`  
 [v]`bSelected`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="openpopupmenu"></a>CMFCToolBarMenuButton::OpenPopupMenu  
 Voláno rámcem, když uživatel otevře rozevírací nabídky tlačítka nabídky panelu nástrojů.  
  
```  
virtual BOOL OpenPopupMenu(CWnd* pWnd=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Určuje okně, které přijímá příkazy rozevírací nabídce. Může být `NULL` pouze v případě na tlačítko nabídky panelu nástrojů nadřazeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Když [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objekt byl vytvořen a otevřít úspěšně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána rozhraním framework, když uživatel otevře rozevírací nabídky z nabídky tlačítka panelu nástrojů.  
  
##  <a name="resetimagetodefault"></a>CMFCToolBarMenuButton::ResetImageToDefault  

  
```  
virtual void ResetImageToDefault();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="savebarstate"></a>CMFCToolBarMenuButton::SaveBarState  

  
```  
virtual void SaveBarState();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při vytváření tlačítka panelu nástrojů jako výsledek operace přetažení myší. Tato metoda volá [CMFCPopupMenu::SaveState](../../mfc/reference/cmfcpopupmenu-class.md#savestate) metoda nejvyšší úrovně místní nabídky, což způsobí, že tlačítko nadřazené z místní nabídky k opětovnému vytvoření jeho nabídky.  
  
##  <a name="serialize"></a>CMFCToolBarMenuButton::Serialize  

  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setaccdata"></a>CMFCToolBarMenuButton::SetACCData  
 Nastaví data usnadnění pro element pásu karet.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Nadřazené okno pro element pásu karet.  
  
 `data`  
 Usnadnění data pro element pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda nastaví usnadnění data pro element pásu karet a vždy vrátí `TRUE`. Potlačí tuto metodu za účelem usnadnění, nastavte a vrátí hodnotu, která označuje úspěch nebo selhání.  
  
##  <a name="setmenuonly"></a>CMFCToolBarMenuButton::SetMenuOnly  
 Určuje, zda tlačítko vykreslením jako tlačítka s nabídkou nebo tlačítko rozdělení, pokud má platný příkaz ID a podnabídky.  
  
```  
void SetMenuOnly(BOOL bMenuOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bMenuOnly`  
 `TRUE`Toto tlačítko Zobrazit jako tlačítka s nabídkou, když se má platný příkaz ID a podnabídky, `FALSE` se zobrazí toto tlačítko jako tlačítko rozdělení, pokud má platný příkaz ID a podnabídky.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle když tlačítka nabídky panelu nástrojů má podnabídky i ID příkazu, v nabídce pravděpodobně tlačítko rozdělení, který má hlavní tlačítko a připojené šipku dolů. Pokud tuto metodu lze volat a `bMenuOnly` je `TRUE`, na tlačítko se zobrazí místo jako jeden nabídky tlačítka s šipku dolů ve tlačítko. Když uživatel klikne na šipku v obou režimech, podnabídky otevře a po kliknutí na jiný šipku součástí tlačítko v obou režimech rozhraní provede příkaz.  
  
##  <a name="setmenupalettemode"></a>CMFCToolBarMenuButton::SetMenuPaletteMode  
 Určuje, zda v rozevírací nabídce v režimu palety.  
  
```  
void SetMenuPaletteMode(
    BOOL bMenuPaletteMode=TRUE,  
    int nPaletteRows=1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bMenuPaletteMode`  
 Určuje, zda v rozevírací nabídce v režimu palety.  
  
 [v]`nPaletteRows`  
 Počet řádků v palety.  
  
### <a name="remarks"></a>Poznámky  
 V režimu palety jsou zobrazené všechny položky nabídky jako více sloupců palety. Zadejte počet řádků pomocí `nPaletteRows`.  
  
##  <a name="setmessagewnd"></a>CMFCToolBarMenuButton::SetMessageWnd  

  
```  
void SetMessageWnd(CWnd* pWndMessage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndMessage`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setradio"></a>CMFCToolBarMenuButton::SetRadio  
 Nastaví na tlačítko nabídky panelu nástrojů zobrazí ikona přepínač tlačítko stylu při zaškrtnutí.  
  
```  
virtual void SetRadio();
```  
  
### <a name="remarks"></a>Poznámky  
 Tlačítko nabídky se nevykreslí, pokud je rezervován, zavolá [CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck) k vykreslení ikonou zaškrtnutí. Ve výchozím nastavení `OnDrawMenuCheck` požadavky, že aktuální visual manager nevykresluje zaškrtávací políčko stylů na tlačítko zaškrtnutí. Po volání této metody správce aktuální visual místo nevykresluje zaškrtnout styl tlačítko přepínač na tlačítko nabídky. Tuto změnu nelze vrátit zpět.  
  
 Když zavoláte tuto metodu a tlačítko nabídky aktuálně se zobrazuje, se aktualizuje.  
  
##  <a name="settearoff"></a>CMFCToolBarMenuButton::SetTearOff  
 Určuje ID panel úplné vypnutí pro rozevírací nabídky.  
  
```  
virtual void SetTearOff(UINT uiBarID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiBarID`  
 Určuje nové úplné – vypnuté panel ID.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem zadejte ID pro panel úplné vypnutí, který se vytvoří, když uživatel nastavuje tažením tlačítko nabídky z řádku nabídek. Pokud `uiBarID` parametru je 0, uživatel nemůže oddělení tlačítka nabídky.  
  
 Volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) k povolení této funkce nabídky úplné vypnutí ve vaší aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)