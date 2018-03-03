---
title: "Třída CMFCToolBarsCustomizeDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 978303c9edaec2d9776d6e1c81b530df791ca5ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog – třída
Dialogové okno nemodální karta ( [cpropertysheet – třída](../../mfc/reference/cpropertysheet-class.md)), který umožňuje uživateli upravit panely nástrojů, nabídek, klávesové zkratky, uživatelem definované nástroje a vizuální styl v aplikaci. Obvykle se uživatel přistoupí k tohoto dialogového okna tak, že vyberete **přizpůsobit** z **nástroje** nabídky.  
  
 **Přizpůsobit** dialogové okno obsahuje šest karet: **příkazy**, **panely nástrojů**, **nástroje**, **klávesnice**,  **Nabídky**, a **možnosti**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Vytvoří `CMFCToolBarsCustomizeDialog` objektu.|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Vloží tlačítka panelu nástrojů do seznamu příkazů, na **příkazy** stránky|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Načte nabídky z prostředků a volání [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) této nabídky přidat do seznamu příkazů na **příkazy** stránky.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Načte nabídky z prostředků a volání [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) této nabídky přidat do seznamu příkazů na **příkazy** stránky.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Panel nástrojů načte z prostředků. Pak u každého příkazu v nabídce volání [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda vložit tlačítka v seznamu příkazů na **příkazy** stránky v zadané kategorii.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::Create](#create)|Zobrazí **přizpůsobení** dialogové okno.|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|Vyhrazeno pro budoucí použití.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Povolí nebo zakáže vytváření nových panelů nástrojů pomocí **přizpůsobit** dialogové okno.|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Naplní poskytnutého `CListBox` objekt s příkazy v **všechny příkazy** kategorie.|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Naplní poskytnutého `CComboBox` objekt s názvem kategorie každý příkaz v **přizpůsobit** dialogové okno.|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Naplní poskytnutého `CListBox` objekt s názvem kategorie každý příkaz v **přizpůsobit** dialogové okno.|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Načte název, který je přidružen ID daného příkazu.|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Načte počet položek v seznamu Zadaný popisek daného textu.|  
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Načte sadu příznaky, které ovlivňují chování dialogového okna.|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Spustí editoru bitové kopie, takže uživatel může přizpůsobit tlačítka nebo nabídky položky ikonu na panelu nástrojů.|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Přepsání posílení inicializace list vlastností. (Přepisuje [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Voláno rámcem po okno byl zničen. (Přepisuje `CPropertySheet::PostNcDestroy`.)|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Tlačítko s ID zadaný příkaz odebere z Zadaná kategorie nebo ze všech kategorií.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Přejmenuje kategorii v poli seznamu kategorií na **příkazy** kartě.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Nahradí tlačítka v seznamu příkazů na **příkazy** karta s nový objekt tlačítka panelu nástrojů.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Přidá do seznamu kategorií, které se zobrazí na kategorii **příkazy** kartě.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Voláno rámcem k určení, zda seznam uživatelem definované nástroje je platný.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Voláno rámcem při změně vlastnosti uživatelem definované nástroje.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Určuje, zda zadaný klávesové zkratky lze přiřadit k akci.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Určuje, zda lze změnit nástroj definovaný uživatelem.|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Voláno rámcem, když uživatel vybere **nástroje** karty je požadovaný.|  
  
## <a name="remarks"></a>Poznámky  
 K zobrazení **přizpůsobit** dialogové okno pole, vytvořte `CMFCToolBarsCustomizeDialog` objekt a volání [CMFCToolBarsCustomizeDialog::Create](#create) metoda.  
  
 Když **přizpůsobit** dialogové okno je aktivní, aplikace pracuje v zvláštního režimu, který omezuje uživateli úkoly vlastního nastavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCToolBarsCustomizeDialog` třídy. Tento příklad ukazuje, jak nahradit tlačítka panelu nástrojů v seznamu příkazů na **příkazy** povolte vytváření nových panelů nástrojů pomocí **přizpůsobit** dialogové okno a zobrazení  **Přizpůsobení** dialogové okno. Tento fragment kódu je součástí [IE Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cpropertysheet –](../../mfc/reference/cpropertysheet-class.md)  
  
 `CMFCToolBarsCustomizeDialog`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxToolBarsCustomizeDialog.h  
  
##  <a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton  
 Vloží tlačítka panelu nástrojů do seznamu příkazů, na **příkazy** stránky.  
  
```  
void AddButton(
    UINT uiCategoryId,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCategoryId`  
 Určuje ID kategorie, do kterého chcete-li na tlačítko Vložit.  
  
 [v]`button`  
 Určuje, na tlačítko Vložit.  
  
 [v]`iInsertBefore`  
 Určuje index založený na nule tlačítka panelu nástrojů před kterou je tlačítko Vložit.  
  
 [v]`lpszCategory`  
 Určuje řetězec kategorie vložit tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 `AddButton` Metoda ignoruje tlačítka, která mají identifikátory standardních příkazů (například ID_FILE_MRU_FILE1), příkazy, které nejsou povolené (viz [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) a fiktivní tlačítka.  
  
 Tato metoda vytvoří nový objekt stejného typu jako `button` (obvykle [CMFCToolBarButton třída](../../mfc/reference/cmfctoolbarbutton-class.md)) s použitím modulu runtime třídy tlačítka. Potom zavolá [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) pro kopírování dat členů tlačítka a vloží kopie do zadané kategorii.  
  
 Při vložení tlačítko Nový, obdrží `OnAddToCustomizePage` oznámení.  
  
 Pokud `iInsertBefore` je -1, připojí se k seznamu kategorií tlačítko; v opačném případě je vložen před položka se zadaným indexem.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `AddButton` metodu `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [posuvníku ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]  
  
##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu  
 Načte nabídky z prostředků a volání [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) této nabídky přidat do seznamu příkazů na **příkazy** stránky.  
  
```  
BOOL AddMenu(UINT uiMenuResId);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiMenuResId`  
 Určuje ID prostředku nabídky načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud byl úspěšně; přidán nabídky v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve volání `AddMenuCommands`, `bPopup` je `FALSE`. V důsledku toho dané metody nepřidává žádné další položky nabídky, které obsahují podnabídky do seznamu příkazů. Tato metoda přidání položek nabídky v dílčích do seznamu příkazů.  
  
##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands  
 Přidá položky do seznamu příkazů v **příkazy** stránky představují všechny položky v nabídce zadaný.  
  
```  
void AddMenuCommands(
    const CMenu* pMenu,  
    BOOL bPopup,  
    LPCTSTR lpszCategory=NULL,  
    LPCTSTR lpszMenuPath=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pMenu`  
 Ukazatel na cmenu – objekt, který chcete přidat.  
  
 [v]`bPopup`  
 Určuje, zda chcete vložit položky místní nabídky do seznamu příkazů.  
  
 [v]`lpszCategory`  
 Název kategorie vložit v nabídce.  
  
 [v]`lpszMenuPath`  
 Předponu, která se přidá k názvu při příkazu se zobrazí v **všechny kategorie** seznamu.  
  
### <a name="remarks"></a>Poznámky  
 `AddMenuCommands` Metoda smyčky přes všechny položky nabídky `pMenu`. Pro každou položku nabídky, která neobsahuje podnabídky, tato metoda vytvoří [CMFCToolBarButton třída](../../mfc/reference/cmfctoolbarbutton-class.md) objekt a volání [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda pro přidání položky nabídky jako panelu nástrojů tlačítko do seznamu příkazů **příkazy** stránky. V tomto procesu se ignorují oddělovačů.  
  
 Pokud `bPopup` je `TRUE`, pro každou položku nabídky, která obsahuje podnabídky tato metoda vytvoří [CMFCToolBarMenuButton třída](../../mfc/reference/cmfctoolbarmenubutton-class.md) objektu a vloží je do seznamu příkazů, voláním `AddButton`. V opačném případě se v seznamu příkazů, nezobrazují položky nabídky, které obsahují podnabídky. V obou případech při `AddMenuCommands` položku nabídky, zaznamená při podnabídce zavolá sama sebe rekurzivně a předání podnabídky jako ukazatel `pMenu` parametr a připojením algoritmu popisek v podnabídce `lpszMenuPath`.  
  
##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar  
 Panel nástrojů načte z prostředků. Pak u každého příkazu v nabídce volání [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda vložit tlačítka v seznamu příkazů na **příkazy** stránky v zadané kategorii.  
  
```  
BOOL AddToolBar(
    UINT uiCategoryId,  
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,  
    UINT uiToolbarResId);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCategoryId`  
 Určuje ID prostředku kategorie přidat panelu nástrojů.  
  
 [v]`uiToolbarResId`  
 Určuje ID prostředku nástrojů, jehož příkazy jsou vloženy do seznamu příkazů.  
  
 [v]`lpszCategory`  
 Určuje název kategorie, do které chcete přidat panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je metoda úspěšná. v opačném případě `FALSE`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `AddToolBar` metoda v `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek, který se používá k reprezentování každý příkaz se [CMFCToolBarButton třída](../../mfc/reference/cmfctoolbarbutton-class.md) objektu. Po přidání panelu nástrojů můžete nahradit tlačítko s ovládacím prvkem odvozeného typu voláním [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).  
  
##  <a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity  
 Ověří platnost seznam nástrojů uživatele.  
  
```  
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lstTools`  
 Seznam uživatelem definované nástroje ke kontrole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud seznam uživatelem definované nástroje je platná; jinak `FALSE`. Výchozí implementace vždy vrátí `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu k ověření platnosti objektů, které představují uživatelem definované nástroje vrácený [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).  
  
 Přepsání `CheckToolsValidity` metodu v třídě odvozené z `CMFCToolBarsCustomizeDialog` Pokud chcete ověřit nástroje uživatele předtím, než uživatel zavře dialogové okno. Pokud tato metoda vrátí hodnotu `FALSE` když uživatel klikne, buď **Zavřít** tlačítko v pravém horním rohu dialogu nebo na tlačítko s názvem bez přípony **Zavřít** v pravém dolním rohu dialogu Zobrazí dialogové okno **nástroje** kartě místo zavření. Pokud tato metoda vrátí hodnotu `FALSE` když uživatel klikne na kartě přejděte směrem od **nástroje** kartě, nedojde k navigaci. By měl zobrazit pole odpovídající zprávu informovat uživatele byl problém způsobující selhání ověření.  
  
##  <a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog  
 Vytvoří `CMFCToolBarsCustomizeDialog` objektu.  
  
```  
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bAutoSetFromMenus = FALSE,  
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),  
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParentFrame`  
 Ukazatel na rámec nadřazené. Tento parametr nesmí být `NULL`.  
  
 [v]`bAutoSetFromMenus`  
 Logická hodnota, která určuje, zda chcete přidat příkazy nabídky ze všech nabídek do seznamu příkazů, na **příkazy** stránky. Pokud tento parametr je `TRUE`, jsou přidány příkazy nabídky. Příkazy nabídky, jinak nebudou přidány.  
  
 [v]`uiFlags`  
 Kombinace příznaky, které ovlivňují chování dialogového okna. Tento parametr může být jeden nebo více z následujících hodnot:  
  
- `AFX_CUSTOMIZE_MENU_SHADOWS`  
  
- `AFX_CUSTOMIZE_TEXT_LABELS`  
  
- `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
  
- `AFX_CUSTOMIZE_NOHELP`  
  
- `AFX_CUSTOMIZE_CONTEXT_HELP`  
  
- `AFX_CUSTOMIZE_NOTOOLS`  
  
- `AFX_CUSTOMIZE_MENUAMPERS`  
  
- `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
  
 [v]`plistCustomPages`  
 Ukazatel na seznam `CRuntimeClass` objekty, které určují další vlastní stránky.  
  
### <a name="remarks"></a>Poznámky  
 `plistCustomPages` Parametr odkazuje na seznam `CRuntimeClass` objekty, které určují další vlastní stránky. Konstruktor přidá další stránky do dialogového okna pomocí [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) metoda. Viz ukázka CustomPages pro příklad, který přidá další stránky, které **přizpůsobit** dialogové okno.  
  
 Další informace o hodnoty, které můžete předat `uiFlags` parametr, najdete v části [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [vlastní stránky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]  
  
##  <a name="create"></a>CMFCToolBarsCustomizeDialog::Create  
 Zobrazí **přizpůsobení** dialogové okno.  
  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je úspěšně; vytvořil seznam vlastností vlastního nastavení v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volání `Create` metoda až po plně inicializovat třídy.  
  
##  <a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars  
 Povolí nebo zakáže vytváření nových panelů nástrojů pomocí **přizpůsobit** dialogové okno.  
  
```  
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Chcete-li povolit panely nástrojů uživatelem definované; `FALSE` zakázat panely nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bEnable` je `TRUE`, **nový**, **přejmenovat** a **odstranit** tlačítka se zobrazují na **panely nástrojů** stránky.  
  
 Ve výchozím nastavení nebo pokud `bEnable` je `FALSE`, nejsou zobrazeny tato tlačítka a uživatel nemůže definovat nových panelů nástrojů.  
  
##  <a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList  
 Naplní poskytnutého `CListBox` objekt s příkazy v **všechny příkazy** kategorie.  
  
```  
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`wndListOfCommands`  
 Odkaz na `CListBox` objektu k naplnění.  
  
### <a name="remarks"></a>Poznámky  
 **Všechny příkazy** kategorie obsahuje příkazy všechny kategorie. [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda přidá příkaz, který je přidružen tlačítka poskytnutého **všechny příkazy** kategorie za vás.  
  
 Tato metoda vymaže obsah ze zadaných `CListBox` objekt před naplnění pomocí příkazů v **všechny příkazy** kategorie.  
  
 `CMFCMousePropertyPage` Třída tato metoda používá k naplnění seznamu poklikejte na soubor událostí.  
  
##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox  
 Naplní poskytnutého `CComboBox` objekt s názvem kategorie každý příkaz v **přizpůsobit** dialogové okno.  
  
```  
void FillCategoriesComboBox(
    CComboBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`wndCategory`  
 Odkaz na `CComboBox` objektu k naplnění.  
  
 [v]`bAddEmpty`  
 Logická hodnota, která určuje, zda chcete přidat do pole se seznamem, která nemají příkazy kategorií. Pokud tento parametr je `TRUE`, prázdný kategorie jsou přidány do pole se seznamem. Prázdný kategorií, jinak nebudou přidány.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je stejná jako [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) metoda s tím rozdílem, že tato metoda funguje s `CComboBox` objektu.  
  
 Tato metoda nevymaže obsah `CComboBox` objekt před jeho naplnění. Zaručuje, že **všechny příkazy** kategorie je poslední položky v poli se seznamem.  
  
 Můžete přidat nové kategorie příkaz pomocí [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda. Název existující kategorii můžete změnit pomocí [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metoda.  
  
 `CMFCToolBarsKeyboardPropertyPage` a `CMFCKeyMapDialog` třídy použít tuto metodu ke kategorizaci mapování klávesnice.  
  
##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox  
 Naplní poskytnutého `CListBox` objekt s názvem kategorie každý příkaz v **přizpůsobit** dialogové okno.  
  
```  
void FillCategoriesListBox(
    CListBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`wndCategory`  
 Odkaz na `CListBox` objektu k naplnění.  
  
 [v]`bAddEmpty`  
 Logická hodnota, která určuje, zda chcete přidat do seznamu, která nemají příkazy kategorií. Pokud tento parametr je `TRUE`, prázdný kategorie jsou přidány do seznamu. Prázdný kategorií, jinak nebudou přidány.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je stejná jako [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) metoda s tím rozdílem, že tato metoda funguje s `CListBox` objektu.  
  
 Tato metoda nevymaže obsah `CListBox` objekt před jeho naplnění. Zaručuje, že **všechny příkazy** kategorie je poslední položky v seznamu.  
  
 Můžete přidat nové kategorie příkaz pomocí [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda. Název existující kategorii můžete změnit pomocí [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metoda.  
  
 `CMFCToolBarsCommandsPropertyPage` Třída používá tato metoda zobrazíte seznam příkazů, která souvisí s každou kategorii příkazu.  
  
##  <a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName  
 Načte název, který je přidružen ID daného příkazu.  
  
```  
LPCTSTR GetCommandName(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu pro načtení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Název, který je přidružen ID daného příkazu, nebo `NULL` Pokud příkaz neexistuje.  
  
##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory  
 Načte počet položek v seznamu Zadaný popisek daného textu.  
  
```  
int GetCountInCategory(
    LPCTSTR lpszItemName,  
    const CObList& lstCommands) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszItemName`  
 Textový popisek tak, aby odpovídaly.  
  
 [v]`lstCommands`  
 Odkaz na seznam, který obsahuje `CMFCToolBarButton` objekty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v zadaných seznamu jejíž text popisku rovná `lpszItemName`.  
  
### <a name="remarks"></a>Poznámky  
 Každý prvek v seznamu zadaný objekt musí být typu `CMFCToolBarButton`. Tato metoda srovnává `lpszItemName` s [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) – datový člen.  
  
##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags  
 Načte sadu příznaky, které ovlivňují chování dialogového okna.  
  
```  
UINT GetFlags() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Sada příznaky, které ovlivňují chování dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte hodnotu `uiFlags` parametr, který je předaný konstruktoru. Vrácená hodnota může být jeden nebo více z následujících hodnot:  
  
 `AFX_CUSTOMIZE_MENU_SHADOWS`  
 Umožňuje uživateli zadat stínové vzhled v nabídce.  
  
 `AFX_CUSTOMIZE_TEXT_LABELS`  
 Umožňuje uživateli zadat, zda jsou text popisky zobrazeny pod obrázky tlačítka panelu nástrojů.  
  
 `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
 Umožňuje uživateli zadat styl nabídky animace.  
  
 `AFX_CUSTOMIZE_NOHELP`  
 Odebere z dialogového okna přizpůsobení na tlačítko Nápověda.  
  
 `AFX_CUSTOMIZE_CONTEXT_HELP`  
 Umožňuje `WS_EX_CONTEXTHELP` vizuální styl.  
  
 `AFX_CUSTOMIZE_NOTOOLS`  
 Odebere **nástroje** stránky z dialogového okna přizpůsobení. Tento příznak je platný, pokud vaše aplikace používá `CUserToolsManager` třídy.  
  
 `AFX_CUSTOMIZE_MENUAMPERS`  
 Umožňuje titulky tlačítko tak, aby obsahovala ampersand (  **&** ) znaků.  
  
 `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
 Odebere **ikony. velké ikony** možnost z dialogového okna přizpůsobení.  
  
 Další informace o `WS_EX_CONTEXTHELP` vizuální styl, najdete v části [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
##  <a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool  
 Reaguje na změny v nástroji uživatele ihned po k ní dojde.  
  
```  
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`pSelTool`  
 Ukazatel na objekt uživatele nástroj, který byl změněn.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rozhraním framework, když uživatel změní vlastnosti uživatelem definované nástroje. Výchozí implementace neprovede žádnou akci. Potlačí tuto metodu do třídy odvozené od `CMFCToolBarsCustomizeDialog` k provedení zpracování po dojde ke změně nástroj uživatele.  
  
##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey  
 Ověří klávesové zkratky, jak je definuje uživatele.  
  
```  
virtual BOOL OnAssignKey(ACCEL* pAccel);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`pAccel`  
 Ukazatel na přidělení navrhované klávesnice, který je vyjádřeno [AKCELERACE](http://msdn.microsoft.com/library/windows/desktop/ms646340) struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud klíč lze přiřadit, nebo `FALSE` Pokud klíč nemůže být přiřazen. Výchozí implementace vždy vrátí `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě provést další zpracování, když uživatel přiřadí nové klávesové zkratky nebo k ověření klávesové zkratky jako uživatel definuje. Chcete-li zabránit přiřazeny zástupce, vraťte `FALSE`. Si také zobrazit okno se zprávou nebo jinak informovat uživatele z důvodu, proč byl odmítnut klávesové zkratky.  
  
##  <a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool  
 Provede vlastní zpracováním, když ke změně nástroj pro uživatele Pokud je uživatel Chystáte se použít ke změně.  
  
```  
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`pSelTool`  
 Ukazatel na nástroj objekt uživatele, který má být nahrazen.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem po vlastnosti uživatelem definované nástroje Chystáte se změnit. Výchozí implementace neprovede žádnou akci. Přepsání `OnBeforeChangeTool` metodu v třídě odvozené z `CMFCToolBarsCustomizeDialog` Pokud chcete provést zpracování, než dojde ke změně nástroj pro uživatele, jako je například uvolnění prostředků, `pSelTool` používá.  
  
##  <a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage  
 Spustí editoru bitové kopie, takže uživatel může přizpůsobit tlačítka nebo nabídky položky ikonu na panelu nástrojů.  
  
```  
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,  
    CBitmap& bitmap,  
    int nBitsPerPixel);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Ukazatel do nadřazeného okna.  
  
 [v]`bitmap`  
 Odkaz na objekt bitmap k provádění úprav.  
  
 [v]`nBitsPerPixel`  
 Bitmap – barva řešení v bitů na pixel.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je potvrzení změnu; v opačném případě `FALSE`. Výchozí implementace zobrazí dialogové okno a vrátí `TRUE` Pokud uživatel klikne na **OK**, nebo `FALSE` Pokud uživatel klikne na **zrušit** nebo **Zavřít** tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rozhraním framework, když uživatel spustí editor obrázků. Zobrazí implementace výchozí [CMFCImageEditorDialog třída](../../mfc/reference/cmfcimageeditordialog-class.md) dialogové okno. Přepsání `OnEditToolbarMenuImage` v odvozené třídě a pomocí editoru vlastní image.  
  
##  <a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog  
 Přepsání posílení inicializace list vlastností.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek volání [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) metoda.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), zobrazením **Zavřít** tlačítko, tím, že zajistí, že vyhovuje dialogové okno pro aktuální obrazovku a přesunutím **Pomoci** tlačítko do levého dolního rohu dialogu.  
  
##  <a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage  
 Zpracovává oznámení z rozhraní, **nástroje** stránky je možné inicializovat.  
  
```  
virtual void OnInitToolsPage();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Potlačí tuto metodu v odvozené třídě ke zpracování tohoto oznámení.  
  
##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy  
 Voláno rámcem po okno byl zničen.  
  
```  
virtual void PostNcDestroy();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace `CPropertySheet::PostNcDestroy`, obnovením aplikace pro předchozí režimu.  
  
 [CMFCToolBarsCustomizeDialog::Create](#create) metoda umístí do zvláštního režimu, který omezuje uživateli úkoly vlastního nastavení aplikace.  
  
##  <a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton  
 Tlačítko s ID zadaný příkaz odebere z Zadaná kategorie nebo ze všech kategorií.  
  
```  
int RemoveButton(
    UINT uiCategoryId,  
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,  
    UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCategoryId`  
 Určuje ID kategorie, ze kterého chcete-li tlačítko Odebrat.  
  
 [v]`uiCmdId`  
 Určuje ID příkazového tlačítka.  
  
 [v]`lpszCategory`  
 Určuje název kategorie, ze kterého chcete-li tlačítko Odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule tlačítko odebrané nebo -1, pokud zadaný příkaz ID nebyl nalezen v zadané kategorii. Pokud `uiCategoryId` -1, je vrácená hodnota je 0.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li tlačítko Odebrat ze všech kategorií, volejte první přetížení této metody a sady `uiCategoryId` na hodnotu -1.  
  
##  <a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::RenameCategory  
 Přejmenuje kategorii v poli seznamu kategorií na **příkazy** stránky.  
  
```  
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,  
    LPCTSTR lpszCategoryNew);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszCategoryOld`  
 Chcete-li změnit název kategorie.  
  
 [v]`lpszCategoryNew`  
 Název nové kategorie.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Název kategorie musí být jedinečný.  
  
##  <a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton  
 Nahradí tlačítka panelu nástrojů v seznamu příkazů na **příkazy** stránky.  
  
```  
void ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 Určuje příkaz tlačítko vyměnit.  
  
 [v]`button`  
 A `const` odkaz na objekt tlačítka panelu nástrojů, který nahrazuje původní tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Když [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), nebo [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) přidá příkaz **příkazy** stránky, že příkaz je ve formátu [CMFCToolBarButton třída](../../mfc/reference/cmfctoolbarbutton-class.md) objektu (nebo [CMFCToolBarMenuButton třída](../../mfc/reference/cmfctoolbarmenubutton-class.md) objekt nabídky položky obsahující podnabídky přidal `AddMenuCommands`). Tyto tři metody Automatické přidání příkazů také volá framework. Pokud chcete, aby příkaz, který má být reprezentován místo odvozeným typem, zavolejte `ReplaceButton` a předat tlačítko odvozeného typu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `ReplaceButton` metoda v `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]  
  
##  <a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory  
 Určuje, na které kategorie v seznamu kategorií **příkazy** stránka je kategorii uživatelů. Tato funkce musí volat před voláním [CMFCToolBarsCustomizeDialog::Create](#create).  
  
```  
BOOL SetUserCategory(LPCTSTR lpszCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszCategory`  
 Název kategorie.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je metoda úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Nastavení kategorie uživatel aktuálně nepoužívá rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet – třída](../../mfc/reference/cpropertysheet-class.md)
