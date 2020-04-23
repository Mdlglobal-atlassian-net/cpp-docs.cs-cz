---
title: CMFCToolBarsCustomizeDialog – třída
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
ms.openlocfilehash: 29e2c3d0238ac5a084ea916d95ad953f8c4aedce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753399"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog – třída

Nemodlavé dialogové okno karty [(CPropertySheet Class),](../../mfc/reference/cpropertysheet-class.md)které umožňuje uživateli přizpůsobit panely nástrojů, nabídky, klávesové zkratky, uživatelem definované nástroje a vizuální styl v aplikaci. Uživatel obvykle přistupuje k tomuto dialogovému oknu výběrem **možnosti Přizpůsobit** z nabídky **Nástroje.**

Dialogové okno **Přizpůsobit** obsahuje šest karet: **Příkazy**, **Panely nástrojů**, **Nástroje**, **Klávesnice**, **Nabídka**a **Možnosti**.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CmFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Vytvoří `CMFCToolBarsCustomizeDialog` objekt.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CmFCToolBarsCustomizeDialog::Tlačítko Přidat](#addbutton)|Vloží tlačítko panelu nástrojů do seznamu příkazů na stránce **Příkazy.**|
|[CmFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Načte nabídku z prostředků a zavolá [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pro přidání této nabídky do seznamu příkazů na stránce **Příkazy.**|
|[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Načte nabídku z prostředků a zavolá [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pro přidání této nabídky do seznamu příkazů na stránce **Příkazy.**|
|[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Načte panel nástrojů ze zdrojů. Potom pro každý příkaz v nabídce volá [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda vložit tlačítko v seznamu příkazů na stránce **Příkazy** v zadané kategorii.|
|[CmFCToolBarsCustomizeDialog::Vytvořit](#create)|Zobrazí dialogové okno **Přizpůsobení.**|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Vyhrazeno pro budoucí použití.|
|[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Povolí nebo zakáže vytváření nových panelů nástrojů pomocí dialogového okna **Přizpůsobit.**|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Naplní zadaný `CListBox` objekt příkazy v kategorii **Všechny příkazy.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Naplní poskytnutý `CComboBox` objekt názvem každé kategorie příkazů v dialogovém okně **Přizpůsobit.**|
|[CmFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Naplní poskytnutý `CListBox` objekt názvem každé kategorie příkazů v dialogovém okně **Přizpůsobit.**|
|[CmFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Načte název, který je přidružen k dané ID příkazu.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Načte počet položek v poskytnutém seznamu, které mají daný textový popisek.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Načte sadu příznaků, které ovlivňují chování dialogového okna.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Spustí editor obrázků, aby si uživatel mohl přizpůsobit tlačítko panelu nástrojů nebo ikonu položky nabídky.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Přepíše pro zvětšení inicializace seznamu vlastností. (Přepíše [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Volat rámci po okno bylo zničeno. (Přepíše `CPropertySheet::PostNcDestroy`.)|
|[CmFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Odebere tlačítko se zadaným ID příkazu ze zadané kategorie nebo ze všech kategorií.|
|[CMFCToolBarsCustomizeDialog::Přejmenovatkategorie](#renamecategory)|Přejmenuje kategorii v seznamu kategorií na kartě **Příkazy.**|
|[CmFCToolBarsCustomizeDialog::Příkaz Nahradit](#replacebutton)|Nahradí tlačítko v seznamu příkazů na kartě **Příkazy** novým objektem tlačítka panelu nástrojů.|
|[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Přidá kategorii do seznamu kategorií, které budou zobrazeny na kartě **Příkazy.**|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Volat rámci k určení, zda je platný seznam uživatelem definovaných nástrojů.|
|[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Volat rámci při změně vlastností uživatelem definovaného nástroje.|
|[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Určuje, zda lze k akci přiřadit zadanou klávesovou zkratku.|
|[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Určuje, zda lze změnit nástroj definovaný uživatelem.|
|[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Volána rámci, když uživatel zvolí **karty Nástroje** je požadováno.|

## <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno `CMFCToolBarsCustomizeDialog` **Přizpůsobit,** vytvořte objekt a zavolejte metodu [CMFCToolBarsCustomizeDialog::Create.](#create)

Když je dialogové okno **Přizpůsobit** aktivní, aplikace pracuje ve speciálním režimu, který omezuje uživatele na úkoly přizpůsobení.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCToolBarsCustomizeDialog` metody ve třídě. Příklad ukazuje, jak nahradit tlačítko panelu nástrojů v seznamu příkazů na stránce **Příkazy,** povolit vytváření nových panelů nástrojů pomocí dialogového okna **Přizpůsobit** a zobrazit dialogové okno **Přizpůsobení.** Tento fragment kódu je součástí [ukázky ukázky aplikace IE .](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxToolBarsCustomizeDialog.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CmFCToolBarsCustomizeDialog::Tlačítko Přidat

Vloží tlačítko panelu nástrojů do seznamu příkazů na stránce **Příkazy.**

```cpp
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
[v] Určuje ID kategorie, do které chcete tlačítko vložit.

*Tlačítko*<br/>
[v] Určuje tlačítko, které chcete vložit.

*iInsertBefore*<br/>
[v] Určuje nulový index tlačítka panelu nástrojů, před kterým je tlačítko vloženo.

*lpszKategorie*<br/>
[v] Určuje řetězec kategorie pro vložení tlačítka.

### <a name="remarks"></a>Poznámky

Metoda `AddButton` ignoruje tlačítka, která mají standardní id příkazů (například ID_FILE_MRU_FILE1), příkazy, které nejsou povoleny (viz [CMFCToolBar::IsCommandPermitted)](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)a fiktivní tlačítka.

Tato metoda vytvoří nový objekt stejného typu jako `button` (obvykle [CMFCToolBarButton Class)](../../mfc/reference/cmfctoolbarbutton-class.md)pomocí runtime třídy tlačítka. Potom volá [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) zkopírovat datové členy tlačítka a vloží kopii do zadané kategorie.

Po vložení nového tlačítka obdrží `OnAddToCustomizePage` oznámení.

Pokud `iInsertBefore` je -1, tlačítko je připojen o seznam kategorií; v opačném případě je vložen před položku se zadaným indexem.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `AddButton` používat metodu třídy. `CMFCToolBarsCustomizeDialog` Tento fragment kódu je součástí [ukázky slideru](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CmFCToolBarsCustomizeDialog::AddMenu

Načte nabídku z prostředků a zavolá [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pro přidání této nabídky do seznamu příkazů na stránce **Příkazy.**

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*uiMenuResId*<br/>
[v] Určuje ID prostředku nabídky, kterou chcete načíst.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla nabídka přidána úspěšně; jinak FALSE.

### <a name="remarks"></a>Poznámky

Ve volání `AddMenuCommands`je *bPopup* nepravda. V důsledku toho tato metoda nepřidává položky nabídky, které obsahují podnabídky do seznamu příkazů. Tato metoda přidá položky nabídky v podnabídkách do seznamu příkazů.

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands

Přidá položky do seznamu příkazů na stránce **Příkazy,** aby reprezentovaly všechny položky v zadané nabídce.

```cpp
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parametry

*pNabídka*<br/>
[v] Ukazatel na cmenu objekt upřidat.

*bPopup*<br/>
[v] Určuje, zda mají být položky místní nabídky vloženy do seznamu příkazů.

*lpszKategorie*<br/>
[v] Název kategorie pro vložení nabídky.

*lpszMenuPath*<br/>
[v] Předpona, která je přidána do názvu, když je příkaz zobrazen v seznamu **Všechny kategorie.**

### <a name="remarks"></a>Poznámky

Metoda `AddMenuCommands` se smyčku přes všechny položky nabídky *pMenu*. Pro každou položku nabídky, která neobsahuje podnabídku, tato metoda vytvoří objekt [třídy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) a zavolá metodu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) a přidá položku nabídky jako tlačítko panelu nástrojů do seznamu příkazů na stránce **Příkazy.** Oddělovače jsou v tomto procesu ignorovány.

Pokud je *bPopup* TRUE, pro každou položku nabídky, která obsahuje podnabídku, tato metoda vytvoří objekt [třídy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) a vloží jej do seznamu příkazů voláním `AddButton`. V opačném případě nejsou položky nabídky, které obsahují podnabídky, zobrazeny v seznamu příkazů. V obou případech, když `AddMenuCommands` narazí na položku nabídky s podnabídkou volá sám rekurzivně, předání ukazatele do podnabídky jako parametr *pMenu* a připojení popisku podnabídky k *lpszMenuPath*.

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar

Načte panel nástrojů ze zdrojů. Potom pro každý příkaz v nabídce volá [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda vložit tlačítko v seznamu příkazů na stránce **Příkazy** v zadané kategorii.

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
[v] Určuje ID prostředku kategorie, do které chcete panel nástrojů přidat.

*uiToolbarResId*<br/>
[v] Určuje ID prostředku panelu nástrojů, jehož příkazy jsou vloženy do seznamu příkazů.

*lpszKategorie*<br/>
[v] Určuje název kategorie, do které chcete panel nástrojů přidat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak FALSE.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `AddToolBar` používat metodu ve `CMFCToolBarsCustomizeDialog` třídě. Tento fragment kódu je součástí [ukázky aplikace Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Poznámky

Ovládací prvek, který se používá k reprezentaci každého příkazu je [CMFCToolBarButton class objektu.](../../mfc/reference/cmfctoolbarbutton-class.md) Po přidání panelu nástrojů můžete nahradit tlačítko ovládacím prvkem odvozeného typu voláním [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity

Ověří platnost seznamu uživatelských nástrojů.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parametry

*lstNástroje*<br/>
[v] Seznam uživatelem definovaných nástrojů ke kontrole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je seznam uživatelem definovaných nástrojů platný. jinak FALSE. Výchozí implementace vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Rámec volá tuto metodu k ověření platnosti objektů, které představují uživatelem definované nástroje vrácené [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Přepište `CheckToolsValidity` metodu ve třídě `CMFCToolBarsCustomizeDialog` odvozené z, pokud chcete ověřit uživatelské nástroje před uživatelem zavře dialogové okno. Pokud tato metoda vrátí hodnotu NEPRAVDA, když uživatel klepne na tlačítko **Zavřít** v pravém horním rohu dialogového okna nebo na tlačítko označené **Zavřít** v pravém dolním rohu dialogového okna, zobrazí se v dialogovém okně místo zavření karta **Nástroje.** Pokud tato metoda vrátí hodnotu NEPRAVDA, když uživatel klepne na kartu a přejde z karty **Nástroje,** navigace se neuskuteční. Měli byste zobrazit příslušné okno se zprávou informovat uživatele o problému, který způsobil selhání ověření.

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CmFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

Vytvoří `CMFCToolBarsCustomizeDialog` objekt.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[v] Ukazatel na nadřazený rámec. Tento parametr nesmí mít hodnotu NULL.

*bAutoSetFromMenus*<br/>
[v] Logická hodnota, která určuje, zda mají být příkazy nabídky ze všech nabídek uvedeny do seznamu příkazů na stránce **Příkazy.** Pokud je tento parametr TRUE, budou přidány příkazy nabídky. V opačném případě nejsou přidány příkazy nabídky.

*uiFlags*<br/>
[v] Kombinace příznaků, které ovlivňují chování dialogového okna. Tento parametr může být jedna nebo více z následujících hodnot:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[v] Ukazatel na seznam `CRuntimeClass` objektů, které určují další vlastní stránky.

### <a name="remarks"></a>Poznámky

Parametr *plistCustomPages* odkazuje na seznam `CRuntimeClass` objektů, které určují další vlastní stránky. Konstruktor přidá do dialogového okna další stránky pomocí metody [CRuntimeClass::CreateObject.](../../mfc/reference/cruntimeclass-structure.md#createobject) Příklad, který přidává další stránky do dialogového okna **Přizpůsobit,** najdete v příkladu ukázku vlastních stránek.

Další informace o hodnotách, které můžete předat v parametru *uiFlags,* naleznete v tématu [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [ukázky vlastních stránek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CmFCToolBarsCustomizeDialog::Vytvořit

Zobrazí dialogové okno **Přizpůsobení.**

```
virtual BOOL Create();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je seznam vlastností vlastního nastavení úspěšně vytvořen; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání `Create` metody pouze po úplné inicializaci třídy.

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Povolí nebo zakáže vytváření nových panelů nástrojů pomocí dialogového okna **Přizpůsobit.**

```cpp
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro povolení uživatelem definovaných panelů nástrojů; Nepravda pro zakázání panelů nástrojů.

### <a name="remarks"></a>Poznámky

Pokud je *bEnable* TRUE, zobrazí se na stránce **Panely nástrojů** tlačítka **Nový**, **Přejmenovat** a **Odstranit.**

Ve výchozím nastavení, nebo pokud *bEnable* je FALSE, tato tlačítka nejsou zobrazeny a uživatel nemůže definovat nové panely nástrojů.

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList

Naplní zadaný `CListBox` objekt příkazy v kategorii **Všechny příkazy.**

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parametry

*wndListOfCommands*<br/>
[out] Odkaz na `CListBox` objekt, který má být naplněn.

### <a name="remarks"></a>Poznámky

Kategorie **Všechny příkazy** obsahuje příkazy všech kategorií. Metoda [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) přidá příkaz, který je přidružen k poskytnutému tlačítku, do kategorie **Všechny příkazy** za vás.

Tato metoda vymaže `CListBox` obsah zadaný objekt před vyplněním příkazy v kategorii **Všechny příkazy.**

Třída `CMFCMousePropertyPage` používá tuto metodu k naplnění seznamu událostí poklepání.

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Naplní poskytnutý `CComboBox` objekt názvem každé kategorie příkazů v dialogovém okně **Přizpůsobit.**

```cpp
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndKategorie*<br/>
[out] Odkaz na `CComboBox` objekt, který má být naplněn.

*bPřidatprázdné*<br/>
[v] Logická hodnota, která určuje, zda se mají přidat kategorie do pole se seznamem, které nemají příkazy. Pokud je tento parametr TRUE, prázdné kategorie jsou přidány do pole se seznamem. V opačném případě nebudou přidány prázdné kategorie.

### <a name="remarks"></a>Poznámky

Tato metoda je jako [metoda CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) s `CComboBox` tím rozdílem, že tato metoda pracuje s objektem.

Tato metoda nevymaže `CComboBox` obsah objektu před jeho naplněním. Zaručuje, že kategorie **Všechny příkazy** je poslední položkou v poli se seznamem.

Nové kategorie příkazů můžete přidat pomocí metody [CMFCToolBarsCustomizeDialog::AddButton.](#addbutton) Název existující kategorie můžete změnit pomocí metody [CMFCToolBarsCustomizeDialog::RenameCategory.](#renamecategory)

`CMFCToolBarsKeyboardPropertyPage` Třídy `CMFCKeyMapDialog` a používají tuto metodu ke kategorizaci mapování klávesnice.

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CmFCToolBarsCustomizeDialog::FillCategoriesListBox

Naplní poskytnutý `CListBox` objekt názvem každé kategorie příkazů v dialogovém okně **Přizpůsobit.**

```cpp
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndKategorie*<br/>
[out] Odkaz na `CListBox` objekt, který má být naplněn.

*bPřidatprázdné*<br/>
[v] Logická hodnota, která určuje, zda má být do seznamu přidat kategorie, které nemají příkazy. Pokud je tento parametr TRUE, budou do seznamu přidány prázdné kategorie. V opačném případě nebudou přidány prázdné kategorie.

### <a name="remarks"></a>Poznámky

Tato metoda je jako [METODA CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) s `CListBox` tím rozdílem, že tato metoda pracuje s objektem.

Tato metoda nevymaže `CListBox` obsah objektu před jeho naplněním. Zaručuje, že kategorie **Všechny příkazy** je poslední položkou v seznamu.

Nové kategorie příkazů můžete přidat pomocí metody [CMFCToolBarsCustomizeDialog::AddButton.](#addbutton) Název existující kategorie můžete změnit pomocí metody [CMFCToolBarsCustomizeDialog::RenameCategory.](#renamecategory)

Třída `CMFCToolBarsCommandsPropertyPage` používá tuto metodu k zobrazení seznamu příkazů, které jsou přidruženy ke každé kategorii příkazů.

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CmFCToolBarsCustomizeDialog::GetCommandName

Načte název, který je přidružen k dané ID příkazu.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu k načtení.

### <a name="return-value"></a>Návratová hodnota

Název, který je přidružen k danému ID příkazu, nebo NULL, pokud příkaz neexistuje.

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory

Načte počet položek v poskytnutém seznamu, které mají daný textový popisek.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
[v] Textový popisek, který má odpovídat.

*příkazy lst*<br/>
[v] Odkaz na seznam, `CMFCToolBarButton` který obsahuje objekty.

### <a name="return-value"></a>Návratová hodnota

Počet položek v poskytnutém seznamu, jehož textový popisek se rovná *lpszItemName*.

### <a name="remarks"></a>Poznámky

Každý prvek v seznamu zadaných objektů `CMFCToolBarButton`musí být typu . Tato metoda porovnává *lpszItemName* s datovým členem [CMFCToolBarButton::m_strText.](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags

Načte sadu příznaků, které ovlivňují chování dialogového okna.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Návratová hodnota

Sada příznaků, které ovlivňují chování dialogového okna.

### <a name="remarks"></a>Poznámky

Tato metoda načte hodnotu parametru *uiFlags,* který je předán konstruktoru. Vrácená hodnota může být jedna nebo více z následujících hodnot:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Umožňuje uživateli určit vzhled stínu nabídky.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Umožňuje uživateli určit, zda jsou textové popisky zobrazeny pod obrazy tlačítek panelu nástrojů.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Umožňuje uživateli zadat styl animace nabídky.  |
|AFX_CUSTOMIZE_NOHELP|Odebere tlačítko nápovědy z dialogového okna přizpůsobení.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Umožňuje WS_EX_CONTEXTHELP vizuální styl.  |
|AFX_CUSTOMIZE_NOTOOLS|Odebere stránku **Nástroje** z dialogového okna přizpůsobení. Tento příznak je platný, `CUserToolsManager` pokud vaše aplikace používá třídu.  |
|AFX_CUSTOMIZE_MENUAMPERS|Umožňuje titulkům tlačítka, aby obsahovaly znak ampersand ( **&**).  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Odebere možnost **Velké ikony** z dialogového okna přizpůsobení.  |

Další informace o vizuálním stylu WS_EX_CONTEXTHELP naleznete v [tématu Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Reaguje na změnu v uživatelském nástroji ihned po jeho výskytu.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelNástroj*<br/>
[dovnitř, ven] Ukazatel na objekt nástroje uživatele, který byl změněn.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci při uživatel změní vlastnosti uživatelem definované ho nástroje. Výchozí implementace neprovede žádné provádění. Přepsat tuto metodu ve třídě `CMFCToolBarsCustomizeDialog` odvozené od provádět zpracování po změně uživatelského nástroje dojde.

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey

Ověřuje klávesové zkratky podle toho, jak je uživatel definuje.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*cAccel*<br/>
[dovnitř, ven] Ukazatel na navrhované klávesnice assigment, který je vyjádřen jako [struktura ACCEL.](/windows/win32/api/winuser/ns-winuser-accel)

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud klíč lze přiřadit, nebo NEPRAVDA, pokud klíč nelze přiřadit. Výchozí implementace vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě provádět další zpracování, když uživatel přiřadí novou klávesovou zkratku, nebo ověřit klávesové zkratky podle definice uživatele. Chcete-li zabránit přiřazení zástupce, vraťte hodnotu NEPRAVDA. Měli byste také zobrazit okno se zprávou nebo jinak informovat uživatele o důvodu, proč byla klávesová zkratka odmítnuta.

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Provádí vlastní zpracování při změně uživatelského nástroje, když se uživatel chystá použít změnu.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelNástroj*<br/>
[dovnitř, ven] Ukazatel na objekt nástroje uživatele, který má být nahrazen.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci při změně vlastností uživatelem definovaného nástroje. Výchozí implementace neprovede žádné provádění. Přepsat metodu `OnBeforeChangeTool` ve třídě odvozené z, `CMFCToolBarsCustomizeDialog` pokud chcete provést zpracování před dojde ke změně uživatelského nástroje, jako je například uvolnění prostředků, které používá *pSelTool.*

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Spustí editor obrázků, aby si uživatel mohl přizpůsobit tlačítko panelu nástrojů nebo ikonu položky nabídky.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno.

*Bitmapové*<br/>
[v] Odkaz na bitmapový objekt, který má být upraven.

*nBitsPerPixel*<br/>
[v] Bitmapové rozlišení barev v bitech na pixel.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je změna potvrzena; jinak FALSE. Výchozí implementace zobrazí dialogové okno a vrátí hodnotu PRAVDA, pokud uživatel klepne na **tlačítko OK**, nebo NEPRAVDA, pokud uživatel klepne na tlačítko **Storno** nebo **Zavřít.**

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci při spuštění editoru obrázků uživatelem. Výchozí implementace zobrazí dialogové okno [třídy CMFCImageEditorDialog.](../../mfc/reference/cmfcimageeditordialog-class.md) Přepište `OnEditToolbarMenuImage` v odvozené třídě použít vlastní editor obrázků.

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog

Přepíše pro zvětšení inicializace seznamu vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výsledek volání metody [CPropertySheet::OnInitDialog.](../../mfc/reference/cpropertysheet-class.md#oninitdialog)

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)zobrazením tlačítka **Zavřít,** tím, že se ujistíte, že dialogové okno odpovídá aktuální velikosti obrazovky, a přesunutím tlačítka **Nápověda** do levého dolního rohu dialogového okna.

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage

Zpracovává oznámení z rozhraní, které **tools** stránka se chystá inicializovat.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné provádění. Přepsat tuto metodu v odvozené třídě zpracovat toto oznámení.

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy

Volat rámci po okno bylo zničeno.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní `CPropertySheet::PostNcDestroy`třídy , obnovením aplikace do předchozího režimu.

[CmFCToolBarsCustomizeDialog::Create](#create) Metoda umístí aplikaci do speciálního režimu, který omezuje uživatele na úkoly přizpůsobení.

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CmFCToolBarsCustomizeDialog::RemoveButton

Odebere tlačítko se zadaným ID příkazu ze zadané kategorie nebo ze všech kategorií.

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
[v] Určuje ID kategorie, ze které má být tlačítko odebráno.

*uiCmdId*<br/>
[v] Určuje ID příkazu tlačítka.

*lpszKategorie*<br/>
[v] Určuje název kategorie, ze které má být tlačítko odebráno.

### <a name="return-value"></a>Návratová hodnota

Nulový index odebraného tlačítka nebo -1, pokud zadané ID příkazu nebylo v zadané kategorii nalezeno. Pokud *uiCategoryId* je -1, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Chcete-li odebrat tlačítko ze všech kategorií, zavolejte první přetížení této metody a nastavte *uiCategoryId* na -1.

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::Přejmenovatkategorie

Přejmenuje kategorii v seznamu kategorií na stránce **Příkazy.**

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parametry

*lpszKategorieStaré*<br/>
[v] Název kategorie změnit.

*lpszCategoryNovinka*<br/>
[v] Nový název kategorie.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Název kategorie musí být jedinečný.

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CmFCToolBarsCustomizeDialog::Příkaz Nahradit

Nahradí tlačítko panelu nástrojů v seznamu příkazů na stránce **Příkazy.**

```cpp
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] Určuje příkaz tlačítka, které má být nahrazeno.

*Tlačítko*<br/>
[v] **Odkaz na** objekt tlačítka panelu nástrojů, který nahrazuje staré tlačítko.

### <a name="remarks"></a>Poznámky

Když [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog:::AddMenuCommands](#addmenucommands)nebo [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) přidá příkaz na stránku **Příkazy,** tento příkaz je ve formě objektu [třídy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) (nebo [objektu třídy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) pro položku nabídky, která obsahuje podnabídku přidanou ). `AddMenuCommands` Rozhraní Framework také volá tyto tři metody přidat příkazy automaticky. Pokud chcete, aby příkaz byl reprezentován odvozeným `ReplaceButton` typem, volání a předání tlačítka odvozeného typu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `ReplaceButton` používat metodu ve `CMFCToolBarsCustomizeDialog` třídě. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory

Určuje, která kategorie v seznamu kategorií na stránce **Příkazy** je kategorie uživatele. Tuto funkci je nutné volat před voláním [CMFCToolBarsCustomizeDialog::Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parametry

*lpszKategorie*<br/>
[v] Název kategorie.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Nastavení kategorie uživatele není aktuálně používáno v rámci.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet – třída](../../mfc/reference/cpropertysheet-class.md)
