---
title: CMFCToolBarEditBoxButton Třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 064ebe1c8fe377064d410d09e5ef60ed628df2f3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754008"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton Třída

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pro úpravy ( [Třída cedit).](../../mfc/reference/cedit-class.md)

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Vytvoří `CMFCToolBarEditBoxButton` objekt.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Určuje, zda může uživatel tlačítko během vlastního nastavení roztáhnout. (Přepíše [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko. (Přepíše [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek pro úpravy v tlačítku.|
|`CMFCToolBarEditBoxButton::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Načte první `CMFCToolBarEditBoxButton` objekt v aplikaci, který má zadané ID příkazu.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Načte text prvního ovládacího prvku panelu nástrojů pro úpravy, který má zadané ID příkazu.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Načte ID prostředku místní nabídky, která je přidružena k tlačítku.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Načte ohraničovací obdélník editační části tlačítka textového rámečku.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Vrátí ukazatel na ovládací prvek pro úpravy, který je vložen do tlačítka.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Načte popisovač okna, který je přidružen k tlačítku panelu nástrojů. (Přepíše [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Načte oblast klientské oblasti tlačítka, které musí být překresleno. (Přepíše [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Určuje, zda se po klepnutí na tlačítko zobrazí ohraničení tlačítka. (Přepíše [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsflatMode](#isflatmode)|Určuje, zda mají tlačítka textového rámečku plochý styl.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracuje [zprávu WM_COMMAND.](/windows/win32/menurc/wm-command) (Přepíše [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Volat rámci při přidání tlačítka do dialogového okna **Přizpůsobit.** (Přepíše [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Volat rámci vypočítat velikost tlačítka pro zadaný kontext zařízení a dokovací stav. (Přepíše [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Volat rámci při vložení tlačítka do nového panelu nástrojů. (Přepíše [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Volat rámci po kliknutí uživatele na tlačítko myši. (Přepíše [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Volat rámci při nadřazený panel nástrojů zpracovává WM_CTLCOLOR zprávu. (Přepíše [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Volat rámci nakreslit tlačítko pomocí zadaných stylů a možností. (Přepíše [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Volat rámci nakreslit tlačítko v podokně **příkazy** dialogového okna **Přizpůsobit.** (Přepíše [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Volat rámci při změně globální písmo. (Přepíše [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Volat rámci při přesune nadřazený panel nástrojů. (Přepíše [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Volat rámci při tlačítko stane viditelné nebo neviditelné. (Přepíše [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Volat rámci při nadřazený panel nástrojů změní svou velikost nebo umístění a tato změna způsobí, že tlačítko změnit velikost. (Přepíše [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Volat rámci při nadřazený panel nástrojů aktualizuje text popisného popisu. (Přepíše [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Přečte tento objekt z archivu nebo jej zapíše do archivu. (Přepíše [CMFCToolBarButton::Serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Naplní poskytnutý `CAccessibilityData` objekt daty usnadnění přístupu z tlačítka panelu nástrojů. (Přepíše [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Nastaví text v ovládacím prvku upravit tlačítko.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Najde ovládací tlačítko pro úpravy, které má zadané ID příkazu, a nastaví text v ovládacím prvku upravit toto tlačítko.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Určuje ID prostředku místní nabídky, která je přidružena k tlačítku.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Určuje plochý vzhled stylu tlačítek editačního rámečku v aplikaci.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Určuje styl tlačítka. (Přepíše [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Poznámky

Chcete-li na panel nástrojů přidat tlačítko textového pole, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Vytvořte `CMFCToolBarEditBoxButton` objekt.

3. V obslužné rutině zprávy, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte tlačítko fiktivní ho za nové pole se seznamem pomocí tlačítka [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace naleznete [v tématu Návod: Uvedení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCToolBarEditBoxButton` metody ve třídě. Příklad ukazuje, jak určit, že uživatel může roztáhnout tlačítko během vlastního nastavení, určit, že se po klepnutí na tlačítko zobrazí ohraničení tlačítka, nastaví text v ovládacím prvku textového pole, určí plochý vzhled tlačítek editačního pole v aplikaci a určí styl ovládacího prvku editačního rámečku panelu nástrojů.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbareditboxbutton.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

Určuje, zda může uživatel tlačítko během vlastního nastavení roztáhnout.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní neumožňuje uživateli roztáhnout tlačítko panelu nástrojů během vlastního nastavení. Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že umožňuje uživateli roztáhnout tlačítko panelu nástrojů editačního rámečku během přizpůsobení.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Vytvoří objekt [CMFCToolBarEditBoxButton.](../../mfc/reference/cmfctoolbareditboxbutton-class.md)

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] Určuje ID ovládacího prvku.

*iImage*<br/>
[v] Určuje nulový index obrazu panelu nástrojů. Obraz je umístěn v objektu [třídy CMFCToolBarImages,](../../mfc/reference/cmfctoolbarimages-class.md) který udržuje [třídu TŘÍDY CMFCToolBar.](../../mfc/reference/cmfctoolbar-class.md)

*dwStyl*<br/>
[v] Určuje styl ovládacího prvku úprav.

*iŠířka*<br/>
[v] Určuje šířku ovládacího prvku úprav v obrazových bodech.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nastaví styl ovládacího prvku pro úpravy na následující kombinaci:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

Výchozí šířka ovládacího prvku je 150 pixelů.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom

Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Odkaz na zdrojové tlačítko, ze kterého chcete kopírovat.

### <a name="remarks"></a>Poznámky

Volánítéto metody zkopírovat jiné tlačítko panelu nástrojů na toto tlačítko panelu nástrojů. *src* musí být `CMFCToolBarEditBoxButton`typu .

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit

Vytvoří nový ovládací prvek pro úpravy v tlačítku.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Určuje nadřazené okno ovládacího prvku pro úpravy. Nesmí být null.

*Rect*<br/>
[v] Určuje velikost a umístění ovládacího prvku pro úpravy.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený ovládací prvek úprav; je null, pokud se nezdaří vytvoření a příloha ovládacího prvku.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CMFCToolBarEditBoxButton` dvou krocích. Nejprve volání konstruktoru `CreateEdit`a potom volání , který vytvoří ovládací `CMFCToolBarEditBoxButton` prvek pro úpravy systému Windows a připojí jej k objektu.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Načte první `CMFCToolBarEditBoxButton` objekt v aplikaci, který má zadané ID příkazu.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pro načtení.

### <a name="return-value"></a>Návratová hodnota

První `CMFCToolBarEditBoxButton` objekt v aplikaci, který má zadané ID příkazu nebo NULL, pokud žádný takový objekt neexistuje.

### <a name="remarks"></a>Poznámky

Tato sdílená metoda nástroje je používána metodami, jako je [NAPŘÍKLAD CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) a [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) pro nastavení nebo získání textu prvního ovládacího prvku panelu nástrojů pro úpravy, který má zadané ID příkazu.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Načte text prvního ovládacího prvku panelu nástrojů pro úpravy, který má zadané ID příkazu.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka, ze kterého chcete načíst obsah.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CString` který obsahuje text prvního ovládacího prvku panelu nástrojů pro úpravy, který má zadané ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí prázdný `CMFCToolBarEditBoxButton` řetězec, pokud žádné objekty nemají zadané ID příkazu.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Načte ID prostředku místní nabídky, která je přidružena k tlačítku.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Návratová hodnota

ID prostředku místní nabídky, která je přidružena k tlačítku, nebo 0, pokud tlačítko nemá žádnou přidruženou místní nabídku.

### <a name="remarks"></a>Poznámky

Rozhraní Framework používá ID prostředku k vytvoření místní nabídky, když uživatel klepne pravým tlačítkem myši na tlačítko.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Načte ohraničovací obdélník editační části tlačítka textového rámečku.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parametry

*rectBorder*<br/>
[out] Odkaz na `CRect` objekt, který přijímá ohraničující obdélník.

### <a name="remarks"></a>Poznámky

Tato metoda načte ohraničující obdélník ovládacího prvku upravit v souřadnicích klienta. Zvětší velikost obdélníku v každém směru o jeden pixel.

Metoda [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) volá tuto metodu, když `CMFCToolBarEditBoxButton` nakreslí ohraničení kolem objektu.

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Vrátí ukazatel na ovládací prvek [CEdit Class,](../../mfc/reference/cedit-class.md) který je vložen do tlačítka.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek [CEdit Class,](../../mfc/reference/cedit-class.md) který tlačítko obsahuje. Je null, `CEdit` pokud ovládací prvek ještě nebyl vytvořen.

### <a name="remarks"></a>Poznámky

Ovládací prvek `CEdit` vytvoříte voláním [příkazu CMFCToolBarEditBoxButton::CreateEdit](#createedit).

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

Načte popisovač okna, který je přidružen k tlačítku panelu nástrojů.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna, který je přidružen k tlačítku.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše [metodu CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) vrácením popisovače okna ovládací části upravit ovládací prvek tlačítka upravit pole.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Načte oblast klientské oblasti tlačítka, které musí být překresleno.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CRect` který určuje oblast, která musí být překreslena.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), zahrnutím oblasti textového popisku do oblasti.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Určuje, zda se po klepnutí na tlačítko zobrazí ohraničení tlačítka.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zobrazí jeho ohraničení, když je vybráno; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), vrácením nenulové hodnoty, pokud je ovládací prvek viditelný.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsflatMode

Určuje, zda mají tlačítka textového rámečku plochý styl.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud mají tlačítka plochý styl; jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení mají tlačítka pole pro úpravy plochý styl. Pomocí metody [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) změňte vzhled plochého stylu pro vaši aplikaci.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Určuje, zda tlačítko zpracuje [zprávu WM_COMMAND.](/windows/win32/menurc/wm-command)

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
[v] Zpráva s oznámením, která je přidružena k příkazu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud tlačítko zpracovává zprávu WM_COMMAND nebo NEPRAVDA, což znamená, že zpráva musí být zpracována nadřazeným panelem nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu, když se chystá odeslat [zprávu WM_COMMAND](/windows/win32/menurc/wm-command) do nadřazeného okna.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním [oznámení EN_UPDATE.](/windows/win32/Controls/en-update) Pro každé textové pole se stejným ID příkazu jako tento objekt nastaví textový popisek na textový popisek tohoto objektu.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

Volat rámci při přidání tlačítka do dialogového okna **Přizpůsobit.**

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [(CMFCToolBarButton::OnAddToCustomizePage)](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)zkopírováním vlastností z ovládacího prvku textového pole v libovolném panelu nástrojů, který má stejné ID příkazu jako tento objekt. Tato metoda neprovede žádnou akci, pokud žádný panel nástrojů nemá ovládací prvek textového rámečku, který má stejné ID příkazu jako tento objekt.

Další informace o dialogovém **okně Přizpůsobit** naleznete v tématu [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Volat rámci při vložení tlačítka do nového panelu nástrojů.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) opětovným vytvořením vnitřního `CEdit` objektu.

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick

Volat rámci po kliknutí uživatele na tlačítko myši.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Nepoužité.

*bZpoždění*<br/>
[v] Nepoužité.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zpracuje zprávu o kliknutí; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) vrácením nenulové hodnoty, pokud je viditelný vnitřní `CEdit` objekt.

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

Volat rámci při nadřazený panel nástrojů zpracovává WM_CTLCOLOR zprávu.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který zobrazí tlačítko.

*nCtlColor*<br/>
[v] Nepoužité.

### <a name="return-value"></a>Návratová hodnota

Úchyt globální štětce okna.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) nastavením barev textu a pozadí kontextu poskytnutého zařízení na globální text a barvy pozadí.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, naleznete [v tématu AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Volat rámci při změně globální písmo.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) změnou písma ovládacího prvku na písmo globálního písma.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, naleznete [v tématu AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

Volat rámci při přesune nadřazený panel nástrojů.

```
virtual void OnMove();
```

### <a name="remarks"></a>Poznámky

Tato metoda přepíše výchozí implementaci třídy ( [CMFCToolBarButton::OnMove)](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)aktualizací polohy vnitřního `CEdit` objektu.

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

Volat rámci při tlačítko stane viditelné nebo neviditelné.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] Určuje, zda je tlačítko viditelné. Pokud je tento parametr TRUE, tlačítko je viditelné. V opačném případě tlačítko není viditelné.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) zobrazením tlačítka, pokud *je hodnota bShow* TRUE. V opačném případě tato metoda skryje tlačítko.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize

Volat rámci při nadřazený panel nástrojů změní svou velikost nebo umístění a tato změna způsobí, že tlačítko změnit velikost.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iVelikost*<br/>
[v] Nová šířka tlačítka v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše výchozí implementaci třídy [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizací `CEdit` velikosti a umístění vnitřního objektu.

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

Volat rámci při nadřazený panel nástrojů aktualizuje text popisného popisu.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Nepoužité.

*iButtonIndex*<br/>
[v] Nepoužité.

*soubor nástrojů wnd*<br/>
[v] Ovládací prvek, který zobrazuje text popisu.

*Str*<br/>
[out] Objekt, `CString` který obdrží aktualizovaný text popisu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud metoda aktualizuje text popisu; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) zobrazením textu popisku, který je spojen s editační částí tlačítka. Pokud je `CEdit` vnitřní objekt NULL nebo `CEdit` popisovač okna objektu neidentifikuje existující okno, tato metoda neprovede žádnou akci a vrátí hodnotu FALSE.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

Nastaví text v ovládacím prvku textového pole.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parametry

*sObsah*<br/>
[v] Určuje nový text, který má být nastaven.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Najde objekt [CMFCToolBarEditBoxButton,](../../mfc/reference/cmfctoolbareditboxbutton-class.md) který má zadané ID příkazu a nastaví zadaný text v textovém poli.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] Určuje ID příkazu ovládacího prvku, pro který bude text změněn.

*Strcontents*<br/>
[v] Určuje nový text, který má být nastaven.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl text nastaven; 0, `CMFCToolBarEditBoxButton` pokud ovládací prvek se zadaným ID příkazu neexistuje.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Určuje ID prostředku místní nabídky, která je přidružena k tlačítku.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID prostředku místní nabídky.

### <a name="remarks"></a>Poznámky

Rozhraní Framework používá ID prostředku k vytvoření místní nabídky, když uživatel klepne pravým tlačítkem myši na tlačítko panelu nástrojů.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

Určuje plochý vzhled stylu tlačítek editačního rámečku v aplikaci.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parametry

*bPlochý*<br/>
[v] Plochý styl pro tlačítka editačního rámečku. Pokud je tento parametr TRUE, je povolen vzhled plochého stylu; jinak je vzhled plochého stylu zakázán.

### <a name="remarks"></a>Poznámky

Výchozí plochý styl pro tlačítka textového rámečku je TRUE. Pomocí metody [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) načtěte vzhled plochého stylu pro vaši aplikaci.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle

Určuje styl ovládacího prvku editačního rámečku panelu nástrojů.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyl*<br/>
[v] Nový styl nastavit.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) na *nStyle* Také zakáže textové pole, když je aplikace v režimu Přizpůsobit, a povolí jej, když aplikace není v režimu Přizpůsobit (viz [CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) a [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Seznam platných příznaků stylu naleznete v tématu [Styly ovládacích prvků nástrojů.](../../mfc/reference/toolbar-control-styles.md)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
