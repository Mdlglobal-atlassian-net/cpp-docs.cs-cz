---
title: Cmfctoolbarscustomizedialog – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 026c7392c3eb93b37a712059939683e3e0ab852c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628992"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>Cmfctoolbarscustomizedialog – třída

Dialogové okno nemodální karty ( [cpropertysheet – třída](../../mfc/reference/cpropertysheet-class.md)), která umožňuje uživateli přizpůsobovat panely nástrojů, nabídky, klávesové zkratky, uživatelské nástroje a vizuální styl v aplikaci. Obvykle uživatel přistupuje k dialogovému oknu výběrem **vlastní** z **nástroje** nabídky.

**Vlastní** dialogové okno obsahuje šest karet: **příkazy**, **panely nástrojů**, **nástroje**, **klávesnice**,  **Nabídka**, a **možnosti**.

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
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Vloží tlačítka panelu nástrojů do seznamu příkazů na **příkazy** stránky|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Načte nabídky z prostředků a volání [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) na přidání této nabídky do seznamu příkazů **příkazy** stránky.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Načte nabídky z prostředků a volání [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) na přidání této nabídky do seznamu příkazů **příkazy** stránky.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Načte panel nástrojů z prostředků. Pak pro každý příkaz v nabídce volání [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda vložte tlačítko v seznamu příkazů na **příkazy** stránku v rámci zadané kategorie.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|Zobrazí **přizpůsobení** dialogové okno.|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Vyhrazeno pro budoucí použití.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Povolí nebo zakáže, vytváření nových panelů nástrojů pomocí **vlastní** dialogové okno.|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Naplní zadaných `CListBox` objekt pomocí příkazů v **všechny příkazy** kategorie.|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Naplní zadaných `CComboBox` objekt s názvem kategorie každý příkaz v **vlastní** dialogové okno.|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Naplní zadaných `CListBox` objekt s názvem kategorie každý příkaz v **vlastní** dialogové okno.|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Načte název, který je přidružen ID daného příkazu.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Získá počet položek v seznamu, které mají zadaný text popisku.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Načte sadu příznaků, které ovlivňují chování dialogového okna.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Spustí editoru obrázků, ve kterém může uživatel přizpůsobit tlačítka nebo nabídka položky ikonu na panelu nástrojů.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Přepsání pro rozšíření Inicializace seznamu vlastností. (Přepíše [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Volá se rozhraním po zlikvidování okna. (Přepíše `CPropertySheet::PostNcDestroy`.)|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Tlačítko s Identifikátorem zadaný příkaz odebere z určené kategorii nebo ze všech kategorií.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Přejmenuje na kategorii v seznamu kategorií **příkazy** kartu.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Nahradí tlačítko v seznamu příkazů na **příkazy** karta se nový objekt tlačítka panelu nástrojů.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Přidá do seznamu kategorií, které se zobrazí v kategorii **příkazy** kartu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Volá se rozhraním, které určuje, jestli je platný seznam uživatelem definované nástroje.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Volá se rozhraním, když se změní vlastnosti uživatelsky definovaného nástroje.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Určuje, zda zadaný klávesové zkratky je možné přiřadit k akci.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Určuje, zda je možné změnit uživatelsky definovaného nástroje.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Volá se rozhraním, když uživatel vybere **nástroje** karty je požadovaný.|

## <a name="remarks"></a>Poznámky

Pro zobrazení **vlastní** dialogové okno pole, vytvoření `CMFCToolBarsCustomizeDialog` objektu a volání [CMFCToolBarsCustomizeDialog::Create](#create) – metoda.

Zatímco **vlastní** se dialogové okno, aplikace pracuje, jak do zvláštního režimu, který omezuje uživateli úkolů vlastního nastavení.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCToolBarsCustomizeDialog` třídy. Tento příklad ukazuje, jak nahradit tlačítka panelu nástrojů v rozevíracím seznamu příkazů na **příkazy** stránce, povolit vytváření nových panelů nástrojů pomocí **vlastní** dialogové okno a zobrazení  **Přizpůsobení** dialogové okno. Tento fragment kódu je součástí [IE demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxToolBarsCustomizeDialog.h

##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton

Vloží tlačítka panelu nástrojů do seznamu příkazů na **příkazy** stránky.

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

*uiCategoryId*<br/>
[in] Určuje ID kategorie, do které se má vložit tlačítka.

*Tlačítko*<br/>
[in] Určuje tlačítko pro vložení.

*iInsertBefore*<br/>
[in] Určuje index založený na nule, před kterou je tlačítko Vložit tlačítka panelu nástrojů.

*lpszCategory*<br/>
[in] Určuje řetězec kategorie tlačítko Vložit.

### <a name="remarks"></a>Poznámky

`AddButton` Metoda ignoruje tlačítka, která mají identifikátory standardních příkazů (jako je například ID_FILE_MRU_FILE1), příkazy, které nejsou povolené (viz [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) a zástupný tlačítka.

Tato metoda vytvoří nový objekt stejného typu jako `button` (obvykle [cmfctoolbarbutton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)) pomocí modulu runtime třídy tlačítka. Poté zavolá [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) ke zkopírování tlačítka, datové členy a vloží kopii do zadané kategorie.

Při vložení nového tlačítka přijme `OnAddToCustomizePage` oznámení.

Pokud `iInsertBefore` se -1, na tlačítko se připojí k seznamu kategorií; v opačném případě se vloží před položku se zadaným indexem.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `AddButton` metodu `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [posuvník ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu

Načte nabídky z prostředků a volání [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) na přidání této nabídky do seznamu příkazů **příkazy** stránky.

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*uiMenuResId*<br/>
[in] Určuje ID prostředku nabídky pro načtení.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud nabídka byla úspěšně; přidán v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Při volání funkce `AddMenuCommands`, *bPopup* je FALSE. V důsledku toho tato metoda nepřidá položky nabídky, které obsahují podnabídky do seznamu příkazů. Tato metoda přidá položky nabídky v podnabídek do seznamu příkazů.

##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands

Přidá položky do seznamu příkazů ve **příkazy** stránky představující všechny položky v nabídce zadané.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[in] Ukazatel na objekt cmenu –, který chcete přidat.

*bPopup*<br/>
[in] Určuje, jestli se má vložit položky místní nabídky do seznamu příkazů.

*lpszCategory*<br/>
[in] Název kategorie k vložení v nabídce.

*lpszMenuPath*<br/>
[in] Předponu, která se přidá k názvu po příkazu se zobrazí v **všechny kategorie** seznamu.

### <a name="remarks"></a>Poznámky

`AddMenuCommands` Metoda smyčce prochází všechny položky nabídky o *pMenu*. Pro každou položku nabídky, která neobsahuje podnabídky, tato metoda vytvoří [cmfctoolbarbutton – třída](../../mfc/reference/cmfctoolbarbutton-class.md) objektu a volání [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody jako panel nástrojů přidat položky nabídky tlačítko pro seznam příkazů, které **příkazy** stránky. V tomto procesu jsou ignorovány oddělovače.

Pokud *bPopup* má hodnotu TRUE, pro každou položku nabídky, která obsahuje podnabídku tato metoda vytvoří [cmfctoolbarmenubutton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md) objektu a vloží je do seznamu příkazů voláním `AddButton`. V opačném případě položky nabídky, které obsahují podnabídky se nezobrazují v seznamu příkazů. V obou případech při `AddMenuCommands` položku nabídky, zaznamená se podnabídky zavolá sama sebe rekurzivně a předání ukazatele do podnabídky jako *pMenu* parametr a připojením popisek v podnabídce *lpszMenuPath*.

##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar

Načte panel nástrojů z prostředků. Pak pro každý příkaz v nabídce volání [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda vložte tlačítko v seznamu příkazů na **příkazy** stránku v rámci zadané kategorie.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>Parametry

*uiCategoryId*<br/>
[in] Určuje ID prostředku kategorie pro přidání panelu nástrojů.

*uiToolbarResId*<br/>
[in] Určuje ID prostředku panelu nástrojů, příkazy jsou vloženy do seznamu příkazů.

*lpszCategory*<br/>
[in] Určuje název kategorie, do které chcete přidat panel nástrojů.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je metoda úspěšná. v opačném případě FALSE.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `AddToolBar` metodu `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [slovo panel vzorku](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Poznámky

Ovládací prvek, který se používá k reprezentování každý příkaz je [cmfctoolbarbutton – třída](../../mfc/reference/cmfctoolbarbutton-class.md) objektu. Po přidání panelu nástrojů můžete nahradit tlačítko s ovládacím prvkem odvozeného typu voláním [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

Ověří platnost seznamu nástrojů pro uživatele.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parametry

*lstTools*<br/>
[in] Seznam uživatelem definované nástroje ke kontrole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je platná; seznam uživatelem definované nástroje v opačném případě FALSE. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu k ověření platnosti objektů, které představují uživatelem definované nástroje vrácený [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Přepsat `CheckToolsValidity` metodu v třídě odvozené z `CMFCToolBarsCustomizeDialog` Pokud chcete ověřit uživatelské nástroje předtím, než uživatel zavře dialogové okno. Pokud tato metoda vrátí hodnotu FALSE, když uživatel klikne na tlačítko buď **Zavřít** tlačítko v pravém horním rohu dialogového okna nebo na tlačítko s popiskem **Zavřít** v pravém dolním rohu dialogového okna, dialogové okno Zobrazí **nástroje** kartu místo pravou. Pokud tato metoda vrátí hodnotu FALSE, když uživatel klikne na kartě pro navigaci směrem od **nástroje** kartu, nedojde k navigaci. By měl zobrazit odpovídající zprávu pole informovat uživatele byl problém způsobující selhání ověření.

##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

Vytvoří `CMFCToolBarsCustomizeDialog` objektu.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[in] Ukazatel na nadřazeného rámce. Tento parametr nesmí mít hodnotu NULL.

*bAutoSetFromMenus*<br/>
[in] Logická hodnota, která určuje, jestli se má přidat příkazy nabídky ze všech nabídek do seznamu příkazů na **příkazy** stránky. Pokud tento parametr má hodnotu TRUE, přidají se příkazy nabídky. Příkazy nabídky, jinak nebudou přidány.

*uiFlags*<br/>
[in] Kombinace příznaků, které ovlivňují chování dialogového okna. Tento parametr může být jeden nebo více z následujících hodnot:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[in] Ukazatel na seznam `CRuntimeClass` objekty, které určují další vlastní stránky.

### <a name="remarks"></a>Poznámky

*PlistCustomPages* parametr odkazuje na seznam `CRuntimeClass` objekty, které určují další vlastní stránky. Konstruktor přidá další stránky do dialogového okna s použitím [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) metody. Najdete v ukázce CustomPages příklad, který přidá další stránky, které **vlastní** dialogové okno.

Další informace o hodnoty, které můžete předat *uiFlags* parametr, naleznete v tématu [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [ukázková vlastní stránky](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

Zobrazí **přizpůsobení** dialogové okno.

```
virtual BOOL Create();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě přizpůsobení seznamu vlastností je vytvořen úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Volání `Create` metoda až po plně inicializovat třídu.

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Povolí nebo zakáže, vytváření nových panelů nástrojů pomocí **vlastní** dialogové okno.

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] TRUE, pokud chcete povolit panely nástrojů definovaný uživatelem; FALSE, pokud chcete zakázat panely nástrojů.

### <a name="remarks"></a>Poznámky

Pokud *bEnable* má hodnotu TRUE, **nový**, **přejmenovat** a **odstranit** tlačítek se zobrazí na **panely nástrojů** stránka.

Ve výchozím nastavení nebo pokud *bEnable* NEPRAVDA, nezobrazí tato tlačítka a uživatel nemůže definovat nových panelů nástrojů.

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

Naplní zadaných `CListBox` objekt pomocí příkazů v **všechny příkazy** kategorie.

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parametry

*wndListOfCommands*<br/>
[out] Odkaz na `CListBox` objekt pro naplnění.

### <a name="remarks"></a>Poznámky

**Všechny příkazy** kategorie obsahuje příkazy všechny kategorie. [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda přidá příkaz, který je přidružený k zadané tlačítka **všechny příkazy** kategorie za vás.

Tato metoda vymaže obsah ze zadaných `CListBox` objektu před naplnění pomocí příkazů v **všechny příkazy** kategorie.

`CMFCMousePropertyPage` Třída používá tuto metodu k naplnění pole se seznamem dvakrát klikněte na událost.

##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Naplní zadaných `CComboBox` objekt s názvem kategorie každý příkaz v **vlastní** dialogové okno.

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndCategory*<br/>
[out] Odkaz na `CComboBox` objekt pro naplnění.

*bAddEmpty*<br/>
[in] Logická hodnota, která určuje, jestli se má přidat kategorie pro pole se seznamem, u kterých se příkazy. Pokud tento parametr je hodnota TRUE, prázdná kategorie se přidají do pole se seznamem. V opačném případě prázdné kategorie nejsou přidány.

### <a name="remarks"></a>Poznámky

Tato metoda je stejně jako [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) metoda s tím rozdílem, že tato metoda funguje s `CComboBox` objektu.

Tato metoda nevymaže obsah `CComboBox` objektu před jeho naplnění. To zaručuje, že **všechny příkazy** kategorie je poslední položku v poli se seznamem.

Můžete přidávat nové kategorie příkaz s použitím [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody. Můžete změnit název existující kategorie pomocí [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metody.

`CMFCToolBarsKeyboardPropertyPage` a `CMFCKeyMapDialog` třídy pomocí této metody můžete kategorizovat mapování klávesnice.

##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Naplní zadaných `CListBox` objekt s názvem kategorie každý příkaz v **vlastní** dialogové okno.

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndCategory*<br/>
[out] Odkaz na `CListBox` objekt pro naplnění.

*bAddEmpty*<br/>
[in] Logická hodnota, která určuje, jestli se má přidat do seznamu, které nemají příkazy kategorie. Pokud je tento parametr hodnotu TRUE, prázdná kategorie se přidají do seznamu. V opačném případě prázdné kategorie nejsou přidány.

### <a name="remarks"></a>Poznámky

Tato metoda je stejně jako [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) metoda s tím rozdílem, že tato metoda funguje s `CListBox` objektu.

Tato metoda nevymaže obsah `CListBox` objektu před jeho naplnění. To zaručuje, že **všechny příkazy** kategorie je poslední položku v seznamu.

Můžete přidávat nové kategorie příkaz s použitím [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody. Můžete změnit název existující kategorie pomocí [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metody.

`CMFCToolBarsCommandsPropertyPage` Třída používá tuto metodu, chcete-li zobrazit seznam příkazů, který je spojen s každou kategorii příkaz.

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

Načte název, který je přidružen ID daného příkazu.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] ID příkazu pro načtení.

### <a name="return-value"></a>Návratová hodnota

Název, který je přidružen ID daného příkazu, nebo hodnota NULL, pokud příkaz neexistuje.

##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory

Získá počet položek v seznamu, které mají zadaný text popisku.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
[in] Textový popisek tak, aby odpovídaly.

*lstCommands*<br/>
[in] Odkaz na seznam, který obsahuje `CMFCToolBarButton` objekty.

### <a name="return-value"></a>Návratová hodnota

Počet položek v zadaných seznamu jejichž textový popisek rovná *lpszItemName*.

### <a name="remarks"></a>Poznámky

Každý prvek v seznamu zadaný objekt musí být typu `CMFCToolBarButton`. Tato metoda srovnává *lpszItemName* s [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) datový člen.

##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags

Načte sadu příznaků, které ovlivňují chování dialogového okna.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Návratová hodnota

Sada příznaků, které ovlivňují chování dialogového okna.

### <a name="remarks"></a>Poznámky

Tato metoda načte hodnotu *uiFlags* parametr, který je předán konstruktoru. Návratová hodnota může být jeden nebo více z následujících hodnot:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Umožňuje uživateli určit vzhled stínové nabídky.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Umožňuje uživateli určit, zda textové popisky se zobrazí pod obrázky tlačítka panelu nástrojů.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Umožňuje uživateli zadat nabídka animace style.  |
|AFX_CUSTOMIZE_NOHELP|Odebere tlačítko Nápověda v dialogovém okně přizpůsobení.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Umožňuje WS_EX_CONTEXTHELP vizuálního stylu.  |
|AFX_CUSTOMIZE_NOTOOLS|Odebere **nástroje** stránky v dialogovém okně přizpůsobení. Tento příznak není platný, pokud vaše aplikace používá `CUserToolsManager` třídy.  |
|AFX_CUSTOMIZE_MENUAMPERS|Povolí tlačítko popisky tak, aby obsahovala ampersand ( **&**) znaků.  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Odebere **velké ikony** možnosti v dialogovém okně přizpůsobení.  |

Další informace o vizuální styl WS_EX_CONTEXTHELP najdete v tématu [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Reaguje na změnu uživatelský nástroj ihned po k ní dojde.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool*<br/>
[out v] Ukazatel na objekt uživatele nástroje, které se změnily.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když uživatel změní vlastnosti uživatelsky definovaného nástroje. Výchozí implementace nemá žádný účinek. Potlačí tuto metodu v třídě odvozené z `CMFCToolBarsCustomizeDialog` provádět zpracování poté, co dojde ke změně uživatelský nástroj.

##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey

Ověří klávesové zkratky, jak je definuje uživatele.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*pAccel*<br/>
[out v] Ukazatel na přidělení navrhovaných klávesnice, vyjádřený jako [AKCELERACE](/windows/desktop/api/winuser/ns-winuser-tagaccel) struktury.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud klíč může být přiřazené, nebo hodnotu NEPRAVDA, pokud klíč se nedá přiřadit. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě provést další zpracování, když uživatel přiřadí nové klávesové zkratky nebo ověřit klávesové zkratky jako uživatel definuje. Aby se zabránilo zástupce z přiřazení, vrátí hodnotu FALSE. Byste měli také zobrazí okno se zprávou nebo jinak informovat uživatele důvod proč byla odmítnuta klávesové zkratky.

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Provede vlastní zpracováním, když ke změně uživatelský nástroj uživatele se použít ke změně.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool*<br/>
[out v] Ukazatel na objekt uživatele nástroj, který má být nahrazen.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když vlastnosti uživatelsky definovaného nástroje se má změnit. Výchozí implementace nemá žádný účinek. Přepsat `OnBeforeChangeTool` metodu v třídě odvozené z `CMFCToolBarsCustomizeDialog` Pokud chcete provést zpracování předtím, než dojde ke změně uživatelský nástroj, jako je například uvolnění prostředků, která *pSelTool* používá.

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Spustí editoru obrázků, ve kterém může uživatel přizpůsobit tlačítka nebo nabídka položky ikonu na panelu nástrojů.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Ukazatel do nadřazeného okna.

*Rastrový obrázek*<br/>
[in] Odkaz na objekt bitmap upravit.

*nBitsPerPixel*<br/>
[in] Bitmapové barevné rozlišení v bitů na pixel.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud změna zápisu; v opačném případě FALSE. Výchozí implementace zobrazí dialogové okno a vrátí TRUE, pokud uživatel klikne **OK**, nebo hodnotu NEPRAVDA, pokud uživatel klikne **zrušit** nebo **Zavřít** tlačítko.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když uživatel spustí editor obrázků. Zobrazí výchozí implementace [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md) dialogové okno. Přepsat `OnEditToolbarMenuImage` v odvozené třídě použití vlastní image editoru.

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

Přepsání pro rozšíření Inicializace seznamu vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výsledek volání [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) metody.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), zobrazením **Zavřít** tlačítko, ujistěte se, že vyhovuje dialogových oken pro aktuální obrazovku a přechodem **Pomáhají** tlačítko do levého dolního rohu dialogového okna.

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

Zpracovává oznámení z rozhraní framework, která **nástroje** stránky je možné inicializovat.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace nemá žádný účinek. Potlačí tuto metodu v odvozené třídě ke zpracování tohoto oznámení.

##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy

Volá se rozhraním po zlikvidování okna.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy `CPropertySheet::PostNcDestroy`, obnovením aplikace do předchozí režimu.

[CMFCToolBarsCustomizeDialog::Create](#create) metoda vloží do zvláštního režimu, který omezuje uživateli úkolů vlastního nastavení aplikace.

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

Tlačítko s Identifikátorem zadaný příkaz odebere z určené kategorii nebo ze všech kategorií.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCategoryId*<br/>
[in] Určuje ID kategorie, ze kterého mají být odebrány tlačítka.

*uiCmdId*<br/>
[in] Určuje Identifikátor příkazu tlačítka.

*lpszCategory*<br/>
[in] Určuje název kategorie, ze kterého mají být odebrány tlačítka.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule odebrané tlačítko nebo -1, pokud se v určené kategorii se nenašlo ID zadaného příkazu. Pokud *uiCategoryId* -1, je vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Chcete-li tlačítko Odebrat ze všech kategorií, zavolejte první přetížení této metody a sada *uiCategoryId* na hodnotu -1.

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

Přejmenuje na kategorii v seznamu kategorií **příkazy** stránky.

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parametry

*lpszCategoryOld*<br/>
[in] Chcete-li změnit název kategorie.

*lpszCategoryNew*<br/>
[in] Název nové kategorie.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Název kategorie musí být jedinečný.

##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton

Nahradí tlačítka panelu nástrojů v rozevíracím seznamu příkazů na **příkazy** stránky.

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Určuje příkaz tlačítka, které mají být nahrazeny.

*Tlačítko*<br/>
[in] A **const** odkaz na objekt tlačítka panelu nástrojů, který nahrazuje původní tlačítko.

### <a name="remarks"></a>Poznámky

Když [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), nebo [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) přidá příkaz **příkazy** stránce, že příkaz je ve formě [cmfctoolbarbutton – třída](../../mfc/reference/cmfctoolbarbutton-class.md) objektu (nebo [cmfctoolbarmenubutton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md) objekt nabídky Položka, která obsahuje podnabídku přidal `AddMenuCommands`). Rozhraní volá také tyto tři metody pro přidání příkazů automaticky. Pokud chcete příkazu, který bude reprezentovat místo toho odvozeným typem, volání `ReplaceButton` a předejte mu tlačítko odvozeného typu.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `ReplaceButton` metodu `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

Určuje, na která kategorie v seznamu kategorií **příkazy** stránka je kategorie uživatelů. Lze zavolat tuto funkci, dříve než zavoláte [CMFCToolBarsCustomizeDialog::Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parametry

*lpszCategory*<br/>
[in] Název kategorie.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je metoda úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Kategorie nastavení hlavního názvu uživatele není aktuálně používané rozhraním.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet – třída](../../mfc/reference/cpropertysheet-class.md)
