---
title: CMFCToolBarEditBoxButton Class
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
ms.openlocfilehash: ac07ff4e6bf97518e2c659a9d6df9bd721b6b806
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291610"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton Class

Tlačítka panelu nástrojů obsahující ovládací prvek úprav ( [cedit – třída](../../mfc/reference/cedit-class.md)).

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
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Určuje, jestli uživatel může roztáhnout tlačítko během přizpůsobování. (Přepíše [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Zkopíruje aktuální tlačítko Vlastnosti jiné tlačítko panelu nástrojů. (Přepíše [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek úprav na tlačítku.|
|`CMFCToolBarEditBoxButton::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Načte první `CMFCToolBarEditBoxButton` objektu v aplikaci, která má ID zadaného příkazu.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Načte text první upravit pole ovládacím prvkem panel nástrojů, která má ID zadaného příkazu.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Načte ID prostředku, který je přidružený k tlačítku nabídku.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Načte ohraničující obdélník úpravy součástí tlačítko Upravit pole.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Vrací ukazatel na ovládací prvek pro úpravy, které jsou součástí tlačítka.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Načte popisovač okna, která souvisí s tlačítka panelu nástrojů. (Přepíše [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Načte oblast klientské oblasti tlačítka, které musí být překreslení. (Přepíše [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Určuje, zda se zobrazí ohraničení tlačítka, když uživatel klikne na tlačítko. (Přepíše [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Určuje, zda tlačítka Upravit pole mají bez stromové struktury stylu.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracovává [wm_command –](/windows/desktop/menurc/wm-command) zprávy. (Přepíše [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Volá se rozhraním, když se přidá tlačítko do **vlastní** dialogové okno. (Přepíše [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Volá se rozhraním pro výpočet velikosti tlačítko pro zadané zařízení kontext a stav dokování. (Přepíše [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním při vložení do nového panelu nástrojů na tlačítko. (Přepíše [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Volá se rozhraním, když uživatel klikne na tlačítko myši. (Přepíše [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Volá se rozhraním, když nadřazeného panelu nástrojů zpracovává WM_CTLCOLOR – zpráva. (Přepíše [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Volá se rozhraním, chcete-li nakreslit tlačítko s použitím zadaného styly a možnosti. (Přepíše [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Volá se rozhraním, chcete-li nakreslit tlačítko **příkazy** podokně **vlastní** dialogové okno. (Přepíše [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Volá se rozhraním, když došlo ke změně globální písma. (Overrides [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Volá se rozhraním, když se přesune nadřazeného panelu nástrojů. (Přepíše [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Volá se rozhraním při tlačítka stane viditelné nebo neviditelné. (Přepíše [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Volá se rozhraním, když nadřazeného panelu nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že tlačítko Změnit velikost. (Přepíše [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Volá se rozhraním, když nadřazeného panelu nástrojů aktualizuje její přejede myší. (Overrides [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Čte tento objekt z archivu nebo zapíše do archivu. (Přepíše [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Naplní zadaných `CAccessibilityData` objekt usnadnění daty z panelu nástrojů. (Přepíše [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Nastaví text v textovém poli tlačítka.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Vyhledá tlačítko Upravit ovládací prvek, který má ID zadaného příkazu a nastaví text v textovém poli toto tlačítko.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Určuje ID prostředku, který je přidružený k tlačítku nabídku.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Určuje plochý vzhled tlačítka Upravit pole v aplikaci.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Určuje styl tlačítka. (Přepíše [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Poznámky

Chcete-li přidat tlačítko pro úpravy pole do panelu nástrojů, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Vytvoření `CMFCToolBarEditBoxButton` objektu.

3. V popisovači zpráv, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte zástupné tlačítko Nová tlačítka pole se seznamem pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace najdete v tématu [názorný postup: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCToolBarEditBoxButton` třídy. Tento příklad ukazuje, jak určit, že uživatel můžete roztáhnout tlačítko během přizpůsobování, určit, že když uživatel klikne na tlačítko se zobrazí ohraničení tlačítka, nastavit text v textové pole, zadejte plochý vzhled tlačítka Upravit pole v aplikace CE a zadejte styl panelu nástrojů upravit ovládací prvek pole.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Požadavky

**Header:** afxtoolbareditboxbutton.h

##  <a name="canbestretched"></a>  CMFCToolBarEditBoxButton::CanBeStretched

Určuje, jestli uživatel může roztáhnout tlačítko během přizpůsobování.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní neumožňuje uživateli během přizpůsobování roztáhnout tlačítka panelu nástrojů. Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že uživatel roztáhnout tlačítko panelu nástrojů pro úpravy pole během přizpůsobování.

##  <a name="cmfctoolbareditboxbutton"></a>  CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Vytvoří [cmfctoolbareditboxbutton –](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objektu.

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Určuje ID ovládacího prvku.

*iImage*<br/>
[in] Určuje index založený na nule Obrázek panelu nástrojů. Na obrázku se nachází v [cmfctoolbarimages – třída](../../mfc/reference/cmfctoolbarimages-class.md) objekt, který [cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md) třída udržuje.

*dwStyle*<br/>
[in] Určuje styl ovládacího prvku úprav.

*iWidth*<br/>
[in] Určuje šířku v pixelech ovládacích prvků pro úpravy.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nastaví následující kombinace stylu ovládacího prvku úprav:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

Výchozí šířka ovládacího prvku je 150 pixelů.

##  <a name="copyfrom"></a>  CMFCToolBarEditBoxButton::CopyFrom

Zkopíruje aktuální tlačítko Vlastnosti jiné tlačítko panelu nástrojů.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Odkaz na tlačítko zdroj ze kterého chcete kopírovat.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem kopírování jiné tlačítko panelu nástrojů do tohoto tlačítka panelu nástrojů. *src* musí být typu `CMFCToolBarEditBoxButton`.

##  <a name="createedit"></a>  CMFCToolBarEditBoxButton::CreateEdit

Vytvoří nový ovládací prvek úprav na tlačítku.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Určuje nadřazené okno ovládacího prvku pro úpravy. Nesmí být NULL.

*Rect*<br/>
[in] Určuje velikost a umístění textové pole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený textové pole; To má hodnotu NULL, pokud selžou i přílohy a vytvoření ovládacího prvku.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CMFCToolBarEditBoxButton` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `CreateEdit`, což vytvoří ovládací prvek pro úpravy Windows a připojí ho k `CMFCToolBarEditBoxButton` objektu.

##  <a name="getbycmd"></a>  CMFCToolBarEditBoxButton::GetByCmd

Načte první `CMFCToolBarEditBoxButton` objektu v aplikaci, která má ID zadaného příkazu.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pro načtení.

### <a name="return-value"></a>Návratová hodnota

První `CMFCToolBarEditBoxButton` objektu v aplikaci, která má ID zadaného příkazu nebo hodnota NULL, pokud žádný takový objekt neexistuje.

### <a name="remarks"></a>Poznámky

Tato metoda sdílený nástroj používá metody, jako [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) a [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) nastavení nebo získání textu první nástrojů upravit pole ovládací prvek, který má ID zadaného příkazu.

##  <a name="getcontentsall"></a>  CMFCToolBarEditBoxButton::GetContentsAll

Načte text první upravit pole ovládacím prvkem panel nástrojů, která má ID zadaného příkazu.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka, ze kterého se má načíst obsah.

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje text první upravit pole ovládacím prvkem panel nástrojů, která má ID zadaného příkazu.

### <a name="remarks"></a>Poznámky

Pokud ne, vrátí tato metoda prázdný řetězec `CMFCToolBarEditBoxButton` objekty mají ID zadaného příkazu.

##  <a name="getcontextmenuid"></a>  CMFCToolBarEditBoxButton::GetContextMenuID

Načte ID prostředku, který je přidružený k tlačítku nabídku.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Návratová hodnota

ID prostředku, který je přidružený tlačítka nebo 0, pokud tlačítko nemá žádné přidružené nabídku nabídku.

### <a name="remarks"></a>Poznámky

Rozhraní používá ID prostředku k vytvoření nabídku, když uživatel klepne pravým tlačítkem myši na tlačítko.

##  <a name="geteditborder"></a>  CMFCToolBarEditBoxButton::GetEditBorder

Načte ohraničující obdélník úpravy součástí tlačítko Upravit pole.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parametry

*rectBorder*<br/>
[out] Odkaz na `CRect` objekt, který přijme ohraničující obdélník.

### <a name="remarks"></a>Poznámky

Tato metoda načte ohraničující obdélník ovládacích prvků pro úpravy v souřadnicích klienta. Velikost pravoúhelníku v každém směru rozšiřuje o jeden pixel.

[CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) metoda volá tuto metodu po ohraničení kolem `CMFCToolBarEditBoxButton` objektu.

##  <a name="geteditbox"></a>  CMFCToolBarEditBoxButton::GetEditBox

Vrací ukazatel [cedit – třída](../../mfc/reference/cedit-class.md) ovládací prvek, který je vložený na tlačítku.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cedit – třída](../../mfc/reference/cedit-class.md) ovládací prvek, který obsahuje tlačítka. Má hodnotu NULL, pokud `CEdit` ovládací prvek nebyl dosud vytvořen.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CEdit` ovládací prvek voláním [CMFCToolBarEditBoxButton::CreateEdit](#createedit).

##  <a name="gethwnd"></a>  CMFCToolBarEditBoxButton::GetHwnd

Načte popisovač okna, která souvisí s tlačítka panelu nástrojů.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna, který je přidružený k tlačítku.

### <a name="remarks"></a>Poznámky

Přepíše tuto metodu [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metodu tak, že vrací popisovač okna upravit části ovládacího prvku tlačítko Upravit pole.

##  <a name="getinvalidaterect"></a>  CMFCToolBarEditBoxButton::GetInvalidateRect

Načte oblast klientské oblasti tlačítka, které musí být překreslení.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CRect` objekt, který určuje oblasti, která je nutné překreslit.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), včetně v oblasti oblasti textový popisek.

##  <a name="havehotborder"></a>  CMFCToolBarEditBoxButton::HaveHotBorder

Určuje, zda se zobrazí ohraničení tlačítka, když uživatel klikne na tlačítko.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zobrazí jeho ohraničení. při výběru; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), tak, že vrací nenulovou hodnotu, pokud je ovládací prvek viditelný.

##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode

Určuje, zda tlačítka Upravit pole mají bez stromové struktury stylu.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítka mají plochý; jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení mají tlačítka Upravit pole stylu bez stromové struktury. Použití [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) metodu, která změní plochý vzhled pro vaši aplikaci.

##  <a name="notifycommand"></a>  CMFCToolBarEditBoxButton::NotifyCommand

Určuje, zda tlačítko zpracovává [wm_command –](/windows/desktop/menurc/wm-command) zprávy.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
[in] Zprávy oznámení, který je přidružený příkaz.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tlačítko zpracovává wm_command – zprávy nebo hodnotu NEPRAVDA označuje, že zpráva musí být zpracovány nadřazeného panelu nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když je odeslat [wm_command –](/windows/desktop/menurc/wm-command) zprávu nadřazenému oknu.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním [EN_UPDATE](/windows/desktop/Controls/en-update) oznámení. Pro každého textového pole se stejným Identifikátorem příkazu jako tento objekt nastaví jeho textový popisek pro textový popisek tohoto objektu.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarEditBoxButton::OnAddToCustomizePage

Volá se rozhraním, když se přidá tlačítko do **vlastní** dialogové okno.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) tak, že zkopírujete vlastnosti z ovládacího prvku pro úpravy pole na všech nástrojů, který má stejné ID příkazu jako tento objekt. Tato metoda nemá žádný účinek, pokud není panel nástrojů nemá upravit ovládací prvek, který má stejné ID příkazu jako tento objekt.

Další informace o **vlastní** dialogovém okně naleznete v tématu [cmfctoolbarscustomizedialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarEditBoxButton::OnChangeParentWnd

Volá se rozhraním při vložení do nového panelu nástrojů na tlačítko.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Ukazatel do nového nadřazeného okna.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) prostřednictvím přetvoření vnitřní `CEdit` objektu.

##  <a name="onclick"></a>  CMFCToolBarEditBoxButton::OnClick

Volá se rozhraním, když uživatel klikne na tlačítko myši.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Nevyužité.

*bDelay*<br/>
[in] Nevyužité.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud na tlačítko zpracovává zprávy klikněte na tlačítko. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) tak, že vrací nenulovou hodnotu, pokud vnitřní `CEdit` je objekt viditelný.

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

Volá se rozhraním, když nadřazeného panelu nástrojů zpracovává WM_CTLCOLOR – zpráva.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Kontext zařízení, která se zobrazí tlačítko.

*nCtlColor*<br/>
[in] Nevyužité.

### <a name="return-value"></a>Návratová hodnota

Popisovač pro globální okno štětce.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) tak, že nastavíte barvy textu a pozadí kontextu zadané zařízení globální textu a barvy pozadí v uvedeném pořadí.

Další informace o globální možnosti, které jsou k dispozici pro vaši aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Volá se rozhraním, když došlo ke změně globální písma.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) tak, že změníte písmo ovládacího prvku, který globální písma.

Další informace o globální možnosti, které jsou k dispozici pro vaši aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove

Volá se rozhraním, když se přesune nadřazeného panelu nástrojů.

```
virtual void OnMove();
```

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje výchozí implementaci třídy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) aktualizací pozice vnitřního `CEdit` objektu

##  <a name="onshow"></a>  CMFCToolBarEditBoxButton::OnShow

Volá se rozhraním při tlačítka stane viditelné nebo neviditelné.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] Určuje, zda je viditelný na tlačítko. Pokud tento parametr má hodnotu TRUE, je viditelný na tlačítko. V opačném případě na tlačítko se nezobrazuje.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) tím, že pokud se zobrazuje tlačítko *bShow* má hodnotu TRUE. Jinak tato metoda skryje tlačítko.

##  <a name="onsize"></a>  CMFCToolBarEditBoxButton::OnSize

Volá se rozhraním, když nadřazeného panelu nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že tlačítko Změnit velikost.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
[in] Novou šířku tlačítka v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje výchozí implementaci třídy [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizací, velikost a umístění vnitřního `CEdit` objektu.

##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip

Volá se rozhraním, když nadřazeného panelu nástrojů aktualizuje její přejede myší.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Nevyužité.

*iButtonIndex*<br/>
[in] Nevyužité.

*wndToolTip*<br/>
[in] Ovládací prvek, který zobrazí text popisku.

*str*<br/>
[out] A `CString` objekt, který přijme aktualizovaná přejede myší.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud metoda aktualizuje přejede myší; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) tím, že zobrazuje text popisku, který je spojen s úpravy část tlačítka. Pokud interní `CEdit` objekt má hodnotu NULL nebo popisovač okna `CEdit` objektů neidentifikuje existujícímu oknu, tato metoda neprovede žádnou akci a vrátí hodnotu FALSE.

##  <a name="setcontents"></a>  CMFCToolBarEditBoxButton::SetContents

Nastaví text v textové pole.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parametry

*sContents*<br/>
[in] Určuje nastavení nového textu.

##  <a name="setcontentsall"></a>  CMFCToolBarEditBoxButton::SetContentsAll

Vyhledá [cmfctoolbareditboxbutton –](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objekt, který má zadaný příkaz ID a nastaví zadaný text v rámci jeho textového pole.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Určuje ID příkazu, pro kterou se změní text ovládacího prvku.

*strContents*<br/>
[in] Určuje nastavení nového textu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla nastavena text; 0, pokud `CMFCToolBarEditBoxButton` ovládací prvek s ID zadaného příkazu, který neexistuje.

##  <a name="setcontextmenuid"></a>  CMFCToolBarEditBoxButton::SetContextMenuID

Určuje ID prostředku, který je přidružený k tlačítku nabídku.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] ID prostředku v místní nabídce.

### <a name="remarks"></a>Poznámky

Rozhraní používá ID prostředku k vytvoření nabídku, když uživatel klepne pravým tlačítkem myši na tlačítko panelu nástrojů.

##  <a name="setflatmode"></a>  CMFCToolBarEditBoxButton::SetFlatMode

Určuje plochý vzhled tlačítka Upravit pole v aplikaci.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
[in] Plochý pro tlačítka Upravit pole. Pokud tento parametr má hodnotu TRUE, je povoleno plochý vzhled; Plochý vzhled jinak je zakázaná.

### <a name="remarks"></a>Poznámky

Výchozí styl ploché tlačítka Upravit pole má hodnotu TRUE. Použití [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) metodu pro načtení plochý vzhled pro vaši aplikaci.

##  <a name="setstyle"></a>  CMFCToolBarEditBoxButton::SetStyle

Určuje styl panelu nástrojů upravit ovládací prvek pole.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
[in] Nový styl nastavení.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) k *nStyle* když se aplikace je v režimu vlastní nastavení a povolí ho, když aplikace není v režimu vlastní (viz takézakážedotextovéhopole[ CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) a [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Zobrazit [– styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md) seznam příznaky platný styl.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
