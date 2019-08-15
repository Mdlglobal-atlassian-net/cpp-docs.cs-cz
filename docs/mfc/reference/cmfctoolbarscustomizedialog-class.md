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
ms.openlocfilehash: 239532c78491f121423ca42a2c3dfc306997c841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504694"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog – třída

Dialogové okno nemodální karty ( [Třída CPropertySheet –](../../mfc/reference/cpropertysheet-class.md)), které umožňuje uživateli přizpůsobit panely nástrojů, nabídky, klávesové zkratky, uživatelsky definované nástroje a vizuální styl v aplikaci. Uživatel obvykle přistupuje k tomuto dialogovému oknu výběrem možnosti **přizpůsobit** v nabídce **nástroje** .

Dialogové okno **přizpůsobit** má šest karet: **Příkazy**, **panely nástrojů**, **nástroje**, **klávesnice**, **Nabídka**a **Možnosti**.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|`CMFCToolBarsCustomizeDialog` Vytvoří objekt.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)|Vloží tlačítko panelu nástrojů do seznamu příkazů na stránce **příkazy** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: PřidatNabídku](#addmenu)|Načte nabídku z prostředků a volá [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) pro přidání této nabídky do seznamu příkazů na stránce **příkazy** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)|Načte nabídku z prostředků a volá [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) pro přidání této nabídky do seznamu příkazů na stránce **příkazy** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar)|Načte panel nástrojů z prostředků. Potom pro každý příkaz v nabídce zavolá metodu [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) pro vložení tlačítka do seznamu příkazů na stránce **příkazy** v rámci zadané kategorie.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: Create](#create)|Zobrazí dialogové okno **vlastní nastavení** .|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Vyhrazeno pro budoucí použití.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Povolí nebo zakáže vytváření nových panelů nástrojů pomocí dialogového okna **přizpůsobit** .|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Naplní zadaný `CListBox` objekt příkazy z kategorie **všechny příkazy** .|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Naplní zadaný `CComboBox` objekt názvem každé kategorie příkazů v dialogovém okně **přizpůsobit** .|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Naplní zadaný `CListBox` objekt názvem každé kategorie příkazů v dialogovém okně **přizpůsobit** .|
|[CMFCToolBarsCustomizeDialog:: GetCommand](#getcommandname)|Načte název, který je přidružený k danému ID příkazu.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Načte počet položek v zadaném seznamu, které mají daný textový popisek.|
|[CMFCToolBarsCustomizeDialog:: GetFlags](#getflags)|Načte sadu příznaků, které mají vliv na chování dialogového okna.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Spustí editor obrázků, aby uživatel mohl přizpůsobit tlačítko panelu nástrojů nebo ikonu položky nabídky.|
|[CMFCToolBarsCustomizeDialog:: OnInitDialog](#oninitdialog)|Přepsání pro rozšíření Inicializace seznamu vlastností. (Overrides [CPropertySheet –:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::P ostNcDestroy](#postncdestroy)|Volá se rozhraním po zničení okna. (Overrides `CPropertySheet::PostNcDestroy`.)|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: RemoveButton](#removebutton)|Odebere tlačítko se zadaným ID příkazu ze zadané kategorie nebo ze všech kategorií.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)|Přejmenuje kategorii do pole se seznamem kategorií na kartě **příkazy** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton)|Nahrazuje tlačítko v seznamu příkazů na kartě **příkazy** pomocí nového objektu tlačítka panelu nástrojů.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: SetUserCategory](#setusercategory)|Přidá kategorii do seznamu kategorií, které se zobrazí na kartě **příkazy** .|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity)|Volá se rozhraním, aby se určilo, jestli je seznam uživatelsky definovaných nástrojů platný.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnAfterChangeTool](#onafterchangetool)|Volá se rozhraním, když se změní vlastnosti uživatelsky definovaného nástroje.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnAssignKey](#onassignkey)|Určuje, zda lze k akci přiřadit zadanou klávesovou zkratku.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool](#onbeforechangetool)|Určuje, zda lze změnit uživatelsky definovaný nástroj.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Volá se rozhraním, když uživatel zvolí kartu **nástroje** .|

## <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno **přizpůsobit** , vytvořte `CMFCToolBarsCustomizeDialog` objekt a zavolejte metodu [CMFCToolBarsCustomizeDialog:: Create](#create) .

I když je dialogové okno **přizpůsobit** aktivní, aplikace funguje ve speciálním režimu, který omezuje uživatele na úlohy přizpůsobení.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody ve `CMFCToolBarsCustomizeDialog` třídě. Tento příklad ukazuje, jak nahradit tlačítko panelu nástrojů v seznamu příkazů na stránce **příkazy** , povolit vytváření nových panelů nástrojů pomocí dialogového okna **přizpůsobit** a zobrazení dialogového okna **přizpůsobení** . Tento fragment kódu je součástí ukázky [Ukázka IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxToolBarsCustomizeDialog. h

##  <a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton

Vloží tlačítko panelu nástrojů do seznamu příkazů na stránce **příkazy** .

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
pro Určuje ID kategorie, do které se má tlačítko Vložit.

*tlačítko*<br/>
pro Určuje tlačítko, které má být vloženo.

*iInsertBefore*<br/>
pro Určuje index tlačítka panelu nástrojů vycházející od nuly, před kterým bylo tlačítko vloženo.

*lpszCategory*<br/>
pro Určuje řetězec kategorie pro vložení tlačítka.

### <a name="remarks"></a>Poznámky

Metoda ignoruje tlačítka, která mají standardní ID příkazů (například ID_FILE_MRU_FILE1), příkazy, které nejsou povoleny (viz [CMFCToolBar:: IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) a zástupné tlačítka. `AddButton`

Tato metoda vytvoří nový objekt stejného typu jako `button` (obvykle [třídy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)) pomocí třídy runtime tlačítka. Pak zavolá [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) pro zkopírování datových členů tlačítka a vloží kopii do určené kategorie.

Po vložení tlačítka Nový obdrží `OnAddToCustomizePage` oznámení.

Pokud `iInsertBefore` je-1, tlačítko je připojeno k seznamu kategorií; v opačném případě je vloženo před položkou se zadaným indexem.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `AddButton` metodu `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [ukázky posuvníku](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog:: PřidatNabídku

Načte nabídku z prostředků a volá [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) pro přidání této nabídky do seznamu příkazů na stránce **příkazy** .

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*uiMenuResId*<br/>
pro Určuje ID prostředku nabídky, která se má načíst.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se nabídka úspěšně přidala; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

V volání `AddMenuCommands` *bPopup* je hodnota false. V důsledku toho tato metoda nepřidá položky nabídky, které obsahují podnabídky, do seznamu příkazů. Tato metoda přidá položky nabídky do podnabídek do seznamu příkazů.

##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands

Přidá položky do seznamu příkazů na stránce **příkazy** , které reprezentují všechny položky v zadané nabídce.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
pro Ukazatel na objekt CMenu –, který chcete přidat.

*bPopup*<br/>
pro Určuje, zda se mají vložit položky místní nabídky do seznamu příkazů.

*lpszCategory*<br/>
pro Název kategorie pro vložení nabídky

*lpszMenuPath*<br/>
pro Předpona, která je přidána k názvu při zobrazení příkazu v seznamu **všechny kategorie** .

### <a name="remarks"></a>Poznámky

Metoda `AddMenuCommands` se cykluje u všech položek nabídky *pMenu*. Pro každou položku nabídky, která neobsahuje podnabídku, tato metoda vytvoří objekt [třídy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) a zavolá metodu [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) pro přidání položky nabídky jako tlačítka panelu nástrojů do seznamu příkazů na  **Stránka příkazy** . Oddělovače jsou v tomto procesu ignorovány.

Pokud má *bPopup* hodnotu true, pro každou položku nabídky, která obsahuje podnabídku, tato metoda vytvoří objekt [třídy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) a vloží jej do seznamu příkazů voláním `AddButton`. Jinak se položky nabídky, které obsahují podnabídky, nezobrazí v seznamu příkazů. V obou případech při výskytu položky nabídky s podnabídkou, která volá sama sebe, předává `AddMenuCommands` ukazatel do podnabídky jako parametr *pMenu* a připojuje popisek podnabídky k *lpszMenuPath*.

##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar

Načte panel nástrojů z prostředků. Potom pro každý příkaz v nabídce zavolá metodu [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) pro vložení tlačítka do seznamu příkazů na stránce **příkazy** v rámci zadané kategorie.

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
pro Určuje ID prostředku kategorie, do které chcete přidat panel nástrojů.

*uiToolbarResId*<br/>
pro Určuje ID prostředku panelu nástrojů, jehož příkazy jsou vloženy do seznamu příkazů.

*lpszCategory*<br/>
pro Určuje název kategorie, do které se má panel nástrojů přidat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `AddToolBar` metodu `CMFCToolBarsCustomizeDialog` ve třídě. Tento fragment kódu je součástí ukázky panelu [aplikace Word](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Poznámky

Ovládací prvek, který se používá k reprezentaci každého příkazu, je objekt [třídy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) . Po přidání panelu nástrojů lze tlačítko Nahradit ovládacím prvkem odvozeného typu voláním [CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton).

##  <a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity

Ověří platnost seznamu uživatelských nástrojů.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parametry

*lstTools*<br/>
pro Seznam uživatelsky definovaných nástrojů, které se mají kontrolovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je seznam uživatelsky definovaných nástrojů platný. v opačném případě FALSE. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu pro ověření platnosti objektů, které reprezentují uživatelsky definované nástroje vrácené funkcí [CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity).

Přepsat metodu ve třídě odvozené z `CMFCToolBarsCustomizeDialog` , pokud chcete ověřit uživatelské nástroje před tím, než uživatel zavře dialogové okno. `CheckToolsValidity` Pokud tato metoda vrátí hodnotu FALSE, když uživatel klikne buď na tlačítko **Zavřít** v pravém horním rohu dialogového okna, nebo na tlačítko s popiskem **Zavřít** v pravém dolním rohu dialogového okna, dialogové okno zobrazí kartu **nástroje** místo ukončuje. Pokud tato metoda vrátí hodnotu FALSE, pokud uživatel klikne na kartu a opustíte kartu **nástroje** , navigace neproběhne. Měli byste zobrazit příslušné okno se zprávou pro informování uživatele o problému, který způsobil selhání ověřování.

##  <a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

`CMFCToolBarsCustomizeDialog` Vytvoří objekt.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
pro Ukazatel na nadřazený rámec. Tento parametr nesmí mít hodnotu NULL.

*bAutoSetFromMenus*<br/>
pro Logická hodnota, která určuje, zda se mají přidat příkazy nabídky ze všech nabídek do seznamu příkazů na stránce **příkazy** . Pokud má tento parametr hodnotu TRUE, přidají se příkazy nabídky. V opačném případě se příkazy nabídky nepřidaly.

*uiFlags*<br/>
pro Kombinace příznaků, které mají vliv na chování dialogového okna. Tento parametr může být jednou nebo více z následujících hodnot:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
pro Ukazatel na seznam `CRuntimeClass` objektů, které určují další vlastní stránky.

### <a name="remarks"></a>Poznámky

Parametr *plistCustomPages* odkazuje na seznam `CRuntimeClass` objektů, které určují další vlastní stránky. Konstruktor přidá do dialogového okna více stránek pomocí metody [CRuntimeClass:: CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) . Příklad, který do dialogového okna **přizpůsobit** přidá další stránky, najdete v ukázce CustomPages.

Další informace o hodnotách, které lze předat v parametru *uiFlags* , naleznete v tématu [CMFCToolBarsCustomizeDialog::](#getflags)GetFlags.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarsCustomizeDialog` třídy. Tento fragment kódu je součástí [ukázky vlastních stránek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>CMFCToolBarsCustomizeDialog:: Create

Zobrazí dialogové okno **vlastní nastavení** .

```
virtual BOOL Create();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, je-li úspěšně vytvořen seznam vlastností přizpůsobení; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`Create` Volejte metodu až po úplné inicializaci třídy.

##  <a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Povolí nebo zakáže vytváření nových panelů nástrojů pomocí dialogového okna **přizpůsobit** .

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE, pokud chcete povolit uživatelsky definované panely nástrojů; FALSE, pokud chcete zakázat panely nástrojů.

### <a name="remarks"></a>Poznámky

Pokud má *bEnable* hodnotu true, **tlačítka Nový**, **Přejmenovat** a **Odstranit** se zobrazí na stránce **panely nástrojů** .

Ve výchozím nastavení, nebo pokud má *bEnable* hodnotu false, tato tlačítka se nezobrazí a uživatel nemůže definovat nové panely nástrojů.

##  <a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList

Naplní zadaný `CListBox` objekt příkazy z kategorie **všechny příkazy** .

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parametry

*wndListOfCommands*<br/>
mimo Odkaz na `CListBox` objekt, který se má naplnit

### <a name="remarks"></a>Poznámky

Kategorie **všechny příkazy** obsahuje příkazy všech kategorií. Metoda [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) přidá příkaz, který je přidružen k uvedenému tlačítku, do kategorie **všechny příkazy** .

Tato metoda vymaže obsah zadaného `CListBox` objektu před jeho naplnění příkazy z kategorie **všechny příkazy** .

`CMFCMousePropertyPage` Třída používá tuto metodu k naplnění seznamu událostí dvojitého kliknutí.

##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Naplní zadaný `CComboBox` objekt názvem každé kategorie příkazů v dialogovém okně **přizpůsobit** .

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndCategory*<br/>
mimo Odkaz na `CComboBox` objekt, který se má naplnit

*bAddEmpty*<br/>
pro Logická hodnota určující, zda mají být přidány kategorie do pole se seznamem, které nemají příkazy. Pokud má tento parametr hodnotu TRUE, do pole se seznamem se přidají prázdné kategorie. V opačném případě se prázdné kategorie nepřidaly.

### <a name="remarks"></a>Poznámky

Tato metoda je podobná metodě [CMFCToolBarsCustomizeDialog:: FillCategoriesListBox](#fillcategorieslistbox) s tím rozdílem, že tato `CComboBox` metoda funguje s objektem.

Tato metoda nevymaže obsah `CComboBox` objektu před jeho naplnění. Zaručuje, že kategorie **všechny příkazy** je poslední položkou v poli se seznamem.

Nové kategorie příkazů můžete přidat pomocí metody [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) . Název existující kategorie můžete změnit pomocí metody [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) .

Třídy `CMFCToolBarsKeyboardPropertyPage` a`CMFCKeyMapDialog` používají tuto metodu ke kategorizaci mapování klávesnice.

##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Naplní zadaný `CListBox` objekt názvem každé kategorie příkazů v dialogovém okně **přizpůsobit** .

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndCategory*<br/>
mimo Odkaz na `CListBox` objekt, který se má naplnit

*bAddEmpty*<br/>
pro Logická hodnota, která určuje, zda mají být do seznamu přidány kategorie, které nemají příkazy. Pokud je tento parametr TRUE, do pole se seznamem se přidají prázdné kategorie. V opačném případě se prázdné kategorie nepřidaly.

### <a name="remarks"></a>Poznámky

Tato metoda je podobná metodě [CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox](#fillcategoriescombobox) s tím rozdílem, že tato `CListBox` metoda funguje s objektem.

Tato metoda nevymaže obsah `CListBox` objektu před jeho naplnění. Zaručuje, že kategorie **všechny příkazy** je poslední položkou v seznamu.

Nové kategorie příkazů můžete přidat pomocí metody [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) . Název existující kategorie můžete změnit pomocí metody [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) .

`CMFCToolBarsCommandsPropertyPage` Třída používá tuto metodu k zobrazení seznamu příkazů, které jsou přidruženy k jednotlivým kategoriím příkazů.

##  <a name="getcommandname"></a>CMFCToolBarsCustomizeDialog:: GetCommand

Načte název, který je přidružený k danému ID příkazu.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu, který se má načíst

### <a name="return-value"></a>Návratová hodnota

Název, který je přidružen k danému ID příkazu, nebo hodnotu NULL, pokud příkaz neexistuje.

##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory

Načte počet položek v zadaném seznamu, které mají daný textový popisek.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
pro Textový popisek, který se má shodovat.

*lstCommands*<br/>
pro Odkaz na seznam, který obsahuje `CMFCToolBarButton` objekty.

### <a name="return-value"></a>Návratová hodnota

Počet položek v zadaném seznamu, jejichž textový popisek se rovná *lpszItemName*.

### <a name="remarks"></a>Poznámky

Každý prvek v seznamu poskytnutých objektů musí být typu `CMFCToolBarButton`. Tato metoda porovnává *lpszItemName* s datovým členem [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) .

##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog:: GetFlags

Načte sadu příznaků, které mají vliv na chování dialogového okna.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Návratová hodnota

Sada příznaků ovlivňujících chování dialogového okna.

### <a name="remarks"></a>Poznámky

Tato metoda načte hodnotu parametru *uiFlags* , která je předána konstruktoru. Návratovou hodnotou může být jedna nebo více z následujících hodnot:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Umožňuje uživateli zadat vzhled nabídky.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Umožňuje uživateli určit, zda budou textové popisky zobrazeny pod obrázky tlačítek panelu nástrojů.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Umožňuje uživateli zadat styl animace nabídky.  |
|AFX_CUSTOMIZE_NOHELP|Odebere tlačítko Help v dialogovém okně přizpůsobení.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Povolí vizuální styl WS_EX_CONTEXTHELP.  |
|AFX_CUSTOMIZE_NOTOOLS|Odebere stránku **nástroje** z dialogového okna přizpůsobení. Tento příznak je platný, pokud vaše aplikace používá `CUserToolsManager` třídu.  |
|AFX_CUSTOMIZE_MENUAMPERS|Umožňuje titulkům tlačítek obsahovat znak ampersand ( **&** ).  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Odebere možnost **velké ikony** z dialogového okna přizpůsobení.  |

Další informace o vizuálním stylu WS_EX_CONTEXTHELP naleznete v tématu [Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

##  <a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Reaguje na změnu v uživatelském nástroji hned po jejím výskytu.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool*<br/>
[in, out] Ukazatel na objekt uživatelského nástroje, který byl změněn.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když uživatel změní vlastnosti uživatelsky definovaného nástroje. Výchozí implementace neprovádí žádnou akci. Přepište tuto metodu ve třídě odvozené z `CMFCToolBarsCustomizeDialog` k provedení zpracování po provedení změny v uživatelském nástroji.

##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey

Ověří klávesové zkratky podle jejich definování uživatelem.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*pAccel*<br/>
[in, out] Ukazatel na navrhovanou klávesnici přiřazení, která je vyjádřena jako struktura [akcelerace](/windows/win32/api/winuser/ns-winuser-accel) .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se klíč dá přiřadit, nebo FALSE, pokud se klíč nedá přiřadit. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu v odvozené třídě, aby provedlo dodatečné zpracování, když uživatel přiřadí novou klávesovou zkratku, nebo ověří klávesové zkratky, jak je definuje uživatel. Chcete-li zabránit přiřazení zástupce, vraťte hodnotu FALSE. Měli byste také zobrazit okno se zprávou nebo jinak informovat uživatele o příčině, proč se klávesová zkratka zamítla.

##  <a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Provádí vlastní zpracování, když se uživatel chystá použít změnu v uživatelském nástroji.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool*<br/>
[in, out] Ukazatel na objekt uživatelského nástroje, který má být nahrazen.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když se chystá Změna vlastností uživatelsky definovaného nástroje. Výchozí implementace neprovádí žádnou akci. Přepsat metodu ve třídě odvozené z `CMFCToolBarsCustomizeDialog` , pokud chcete provést zpracování, než dojde ke změně uživatelského nástroje, například uvolnění prostředků, které pSelTool používá. `OnBeforeChangeTool`

##  <a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Spustí editor obrázků, aby uživatel mohl přizpůsobit tlačítko panelu nástrojů nebo ikonu položky nabídky.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nadřazené okno.

*bitmap*<br/>
pro Odkaz na objekt rastrového obrázku, který má být upraven.

*nBitsPerPixel*<br/>
pro Rozlišení barvy rastrového obrázku v bitech na pixel.

### <a name="return-value"></a>Návratová hodnota

TRUE, je-li potvrzena změna; v opačném případě FALSE. Výchozí implementace zobrazí dialogové okno a vrátí hodnotu TRUE, pokud uživatel klikne na tlačítko **OK**, nebo na hodnotu NEPRAVDA, pokud uživatel klikne na tlačítko **Storno** nebo na tlačítko **Zavřít** .

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když uživatel spustí editor obrázků. Výchozí implementace zobrazí dialogové okno [třídy CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md) . Přepsat `OnEditToolbarMenuImage` v odvozené třídě, aby používala vlastní editor obrázků.

##  <a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog:: OnInitDialog

Přepsání pro rozšíření Inicializace seznamu vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výsledek volání metody [CPropertySheet –:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) .

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, [CPropertySheet –:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), zobrazením tlačítka **Zavřít** tím, že zajistí, že dialogové okno odpovídá aktuální velikosti obrazovky, a přesunutím tlačítka **nápovědy** do levého dolního rohu. z dialogového okna.

##  <a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage

Zpracovává oznámení z rozhraní, které se chystá inicializovat stránku **nástrojů** .

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovádí žádnou akci. Tuto metodu lze pro zpracování tohoto oznámení přepsat v odvozené třídě.

##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::P ostNcDestroy

Volá se rozhraním po zničení okna.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, `CPropertySheet::PostNcDestroy`a to obnovením aplikace do předchozího režimu.

Metoda [CMFCToolBarsCustomizeDialog:: Create](#create) vloží aplikaci do speciálního režimu, který omezí uživatele na úlohy přizpůsobení.

##  <a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton

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
pro Určuje ID kategorie, ze které se má tlačítko Odebrat.

*uiCmdId*<br/>
pro Určuje ID příkazu pro tlačítko.

*lpszCategory*<br/>
pro Určuje název kategorie, ze které se má tlačítko Odebrat.

### <a name="return-value"></a>Návratová hodnota

Index tlačítka odebraného od nuly nebo hodnota-1, pokud zadané ID příkazu nebylo v zadané kategorii nalezeno. Pokud je *uiCategoryId* -1, návratová hodnota je 0.

### <a name="remarks"></a>Poznámky

Chcete-li odebrat tlačítko ze všech kategorií, zavolejte první přetížení této metody a nastavte *uiCategoryId* na hodnotu-1.

##  <a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::RenameCategory

Přejmenuje kategorii do pole se seznamem kategorií na stránce **příkazy** .

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parametry

*lpszCategoryOld*<br/>
pro Název kategorie, který se má změnit

*lpszCategoryNew*<br/>
pro Název nové kategorie

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Název kategorie musí být jedinečný.

##  <a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton

Nahrazuje tlačítko panelu nástrojů v seznamu příkazů na stránce **příkazy** .

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro Určuje příkaz, který má být nahrazen.

*tlačítko*<br/>
pro Odkaz **const** na objekt tlačítka panelu nástrojů, který nahrazuje staré tlačítko.

### <a name="remarks"></a>Poznámky

Pokud [CMFCToolBarsCustomizeDialog:: PřidatNabídku](#addmenu), [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)nebo [CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar) přidá příkaz na stránku **příkazy** , tento příkaz je ve formě [ Objekt třídy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) (nebo objekt [třídy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) pro položku nabídky, která obsahuje podnabídku, kterou `AddMenuCommands`přidal). Rozhraní také volá tyto tři metody pro automatické přidávání příkazů. Pokud chcete místo toho použít příkaz, který je reprezentován odvozeným typem, zavolejte `ReplaceButton` a předejte tlačítko odvozeného typu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `ReplaceButton` metodu `CMFCToolBarsCustomizeDialog` ve třídě. Tento fragment kódu je součástí ukázkového [vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory

Určuje kategorii uživatele v seznamu kategorií na stránce **příkazy** . Tuto funkci je nutné volat před voláním [CMFCToolBarsCustomizeDialog:: Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parametry

*lpszCategory*<br/>
pro Název kategorie

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Nastavení kategorie uživatele není aktuálně používáno rozhraním Framework.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet – třída](../../mfc/reference/cpropertysheet-class.md)
