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
ms.openlocfilehash: 3e988d789ca6a038ce41bca829850f6509fd9df1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504732"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton Class

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pro úpravy ( [Třída CEdit](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|`CMFCToolBarEditBoxButton` Vytvoří objekt.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Určuje, zda může uživatel roztáhnout tlačítko během přizpůsobení. (Overrides [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko. (Overrides [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek pro úpravy v tlačítku.|
|`CMFCToolBarEditBoxButton::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Načte první `CMFCToolBarEditBoxButton` objekt v aplikaci, který má zadané ID příkazu.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Načte text ovládacího prvku panelu nástrojů v prvním textovém poli, který má zadané ID příkazu.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Načte ID prostředku místní nabídky, která je přidružená k tlačítku.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Načte ohraničovací obdélník tlačítka pro úpravy v části Upravit pole.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Vrátí ukazatel na ovládací prvek pro úpravy, který je vložený v tlačítku.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Načte popisovač okna, který je přidružený k tlačítku panelu nástrojů. (Overrides [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Načte oblast klientské oblasti tlačítka, které musí být překresleny. (Overrides [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Určuje, zda je zobrazeno ohraničení tlačítka, když uživatel klikne na tlačítko. (Overrides [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Určuje, zda tlačítka pro úpravy pole mají plochý styl.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracovává zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) . (Overrides [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Volá se rozhraním, když se přidá tlačítko do dialogového okna **přizpůsobit** . (Overrides [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Volá se rozhraním, aby se počítala velikost tlačítka pro zadaný kontext zařízení a stav docking. (Overrides [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko. (Overrides [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Volá se rozhraním, když uživatel klikne na tlačítko myši. (Potlačení [CMFCToolBarButton:: Click](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Volá se rozhraním, když nadřazený panel nástrojů zpracovává zprávu WM_CTLCOLOR. (Overrides [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Volá se rozhraním, aby se vykreslilo tlačítko pomocí zadaných stylů a možností. (Overrides [CMFCToolBarButton:: nakreslit](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Volá se rozhraním, aby se nakreslilo tlačítko v podokně **příkazy** dialogového okna **přizpůsobit** . (Overrides [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Volá se rozhraním, když se změní globální písmo. (Overrides [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Volá se rozhraním, když se přesune nadřazený panel nástrojů. (Overrides [CMFCToolBarButton::-Move](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Volá se rozhraním, když se tlačítko zobrazí jako viditelné nebo neviditelné. (Overrides [CMFCToolBarButton:: inshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Volá se rozhraním, když se změní jeho velikost nebo pozice na nadřazeném panelu nástrojů a tato změna způsobí změnu velikosti tlačítka. (Overrides [CMFCToolBarButton::-size](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Volá se rozhraním, když nadřazený panel nástrojů aktualizuje svůj text popisku. (Overrides [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Přečte tento objekt z archivu nebo ho zapíše do archivu. (Overrides [CMFCToolBarButton:: serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Naplní poskytnutý `CAccessibilityData` objekt daty přístupnosti z tlačítka panelu nástrojů. (Overrides [CMFCToolBarButton:: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Nastaví text v ovládacím prvku tlačítko pro úpravy.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Najde tlačítko pro úpravy, které má zadané ID příkazu, a nastaví text v ovládacím prvku pro úpravy daného tlačítka.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Určuje ID prostředku místní nabídky, která je přidružena k tlačítku.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Určuje plochý vzhled tlačítek pro úpravu pole v aplikaci.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Určuje styl tlačítka. (Overrides [CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Poznámky

Chcete-li přidat tlačítko pro úpravy pole na panel nástrojů, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Sestavte `CMFCToolBarEditBoxButton` objekt.

3. V obslužné rutině zprávy, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte tlačítko zástupný text novým polem se seznamem pomocí [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace najdete v tématu [Návod: Vložení ovládacích prvků na](../../mfc/walkthrough-putting-controls-on-toolbars.md)panely nástrojů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody ve `CMFCToolBarEditBoxButton` třídě. Tento příklad ukazuje, jak určit, že uživatel může během přizpůsobení roztáhnout tlačítko, určit, že se zobrazí ohraničení tlačítka, když uživatel klikne na tlačítko, nastaví text v ovládacím prvku textové pole, určí vzhled tlačítek upravit pole v aplikace. Kationt a určete styl ovládacího prvku textové pole panelu nástrojů.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbareditboxbutton. h

##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

Určuje, zda může uživatel roztáhnout tlačítko během přizpůsobení.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní neumožňuje uživateli roztáhnout tlačítko panelu nástrojů během přizpůsobení. Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že umožňuje uživateli roztáhnout tlačítko panelu nástrojů pro textové pole během přizpůsobení.

##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Vytvoří objekt [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) .

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
pro Určuje ID ovládacího prvku.

*iImage*<br/>
pro Určuje index založený na nule obrázku na panelu nástrojů. Obrázek se nachází v objektu [třídy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) , který udržuje třída [třídy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*dwStyle*<br/>
pro Určuje styl ovládacího prvku pro úpravy.

*iWidth*<br/>
pro Určuje šířku textového ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nastaví styl ovládacího prvku pro úpravy na následující kombinaci:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

Výchozí šířka ovládacího prvku je 150 pixelů.

##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom

Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
pro Odkaz na zdrojové tlačítko, ze kterého se má kopírovat.

### <a name="remarks"></a>Poznámky

Voláním této metody zkopírujte další tlačítko panelu nástrojů na toto tlačítko panelu nástrojů. *Src* musí být typu `CMFCToolBarEditBoxButton`.

##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit

Vytvoří nový ovládací prvek pro úpravy v tlačítku.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Určuje nadřazené okno ovládacího prvku pro úpravy. Nesmí mít hodnotu NULL.

*OBD*<br/>
pro Určuje velikost a polohu ovládacího prvku pro úpravy.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený ovládací prvek pro úpravy; má hodnotu NULL, pokud je vytvoření a příloha ovládacího prvku neúspěšná.

### <a name="remarks"></a>Poznámky

`CMFCToolBarEditBoxButton` Vytvoříte objekt ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `CreateEdit`, čímž se vytvoří ovládací prvek Windows Edit a připojí se `CMFCToolBarEditBoxButton` k objektu.

##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Načte první `CMFCToolBarEditBoxButton` objekt v aplikaci, který má zadané ID příkazu.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko, které se má načíst

### <a name="return-value"></a>Návratová hodnota

První `CMFCToolBarEditBoxButton` objekt v aplikaci, který má zadané ID příkazu, nebo hodnotu null, pokud takový objekt neexistuje.

### <a name="remarks"></a>Poznámky

Tato metoda sdíleného nástroje používá metody jako [CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall) a [CMFCToolBarEditBoxButton:: GetContentsAll](#getcontentsall) k nastavení nebo získání textu prvního ovládacího prvku panelu nástrojů pro úpravu pole, který má zadané ID příkazu.

##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Načte text ovládacího prvku panelu nástrojů v prvním textovém poli, který má zadané ID příkazu.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko, ze kterého se má načíst obsah

### <a name="return-value"></a>Návratová hodnota

`CString` Objekt obsahující text prvního ovládacího prvku panelu nástrojů pro úpravu pole, který má zadané ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí prázdný řetězec, pokud žádné `CMFCToolBarEditBoxButton` objekty neobsahují zadané ID příkazu.

##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Načte ID prostředku místní nabídky, která je přidružená k tlačítku.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Návratová hodnota

ID prostředku místní nabídky, která je přidružena k tlačítku nebo 0, pokud tlačítko nemá přidruženou místní nabídku.

### <a name="remarks"></a>Poznámky

Rozhraní používá ID prostředku k vytvoření místní nabídky, když uživatel klikne pravým tlačítkem myši na tlačítko.

##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Načte ohraničovací obdélník tlačítka pro úpravy v části Upravit pole.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parametry

*rectBorder*<br/>
mimo Odkaz na `CRect` objekt, který přijímá ohraničující obdélník.

### <a name="remarks"></a>Poznámky

Tato metoda načte ohraničující obdélník ovládacího prvku pro úpravy v souřadnicích klienta. Zvětšuje velikost obdélníku v každém směru o jeden pixel.

Metoda [CMFCVisualManager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) volá tuto metodu, když kreslí ohraničení kolem `CMFCToolBarEditBoxButton` objektu.

##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Vrátí ukazatel na ovládací prvek [třídy CEdit](../../mfc/reference/cedit-class.md) , který je vložen do tlačítka.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek [třídy CEdit](../../mfc/reference/cedit-class.md) , který tlačítko obsahuje. Má hodnotu null, pokud `CEdit` ovládací prvek ještě nebyl vytvořen.

### <a name="remarks"></a>Poznámky

`CEdit` Ovládací prvek vytvoříte voláním [CMFCToolBarEditBoxButton:: CreateEdit](#createedit).

##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton:: GetHwnd

Načte popisovač okna, který je přidružený k tlačítku panelu nástrojů.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna, který je spojen s tlačítkem.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje metodu [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) vrácením popisovače okna části pro úpravu ovládacího prvku tlačítka upravit pole.

##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Načte oblast klientské oblasti tlačítka, které musí být překresleny.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Návratová hodnota

`CRect` Objekt, který určuje oblast, která musí být překreslena.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), zahrnutím do oblasti v oblasti textového popisku.

##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Určuje, zda je zobrazeno ohraničení tlačítka, když uživatel klikne na tlačítko.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko při výběru zobrazí jeho ohraničení; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), vrácením nenulové hodnoty, pokud je ovládací prvek viditelný.

##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode

Určuje, zda tlačítka pro úpravy pole mají plochý styl.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má tlačítko plochý styl; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení mají tlačítka pro úpravy plochý styl. Pomocí metody [CMFCToolBarEditBoxButton:: SetFlatMode](#setflatmode) můžete změnit vzhled plochých stylů pro vaši aplikaci.

##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Určuje, zda tlačítko zpracovává zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
pro Zpráva s oznámením, která je přidružena k příkazu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tlačítko zpracuje zprávu WM_COMMAND, nebo FALSE, aby označovala, že zpráva musí být zpracována nadřazeným panelem nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když se chystá odeslat zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) do nadřazeného okna.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním oznámení [EN_UPDATE](/windows/win32/Controls/en-update) . Pro každé textové pole se stejným ID příkazu jako tento objekt nastaví textový popisek na textový popisek tohoto objektu.

##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

Volá se rozhraním, když se přidá tlačítko do dialogového okna **přizpůsobit** .

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) tak, že zkopíruje vlastnosti z ovládacího prvku textové pole na jakémkoli panelu nástrojů, který má stejné ID příkazu jako tento objekt. Tato metoda neprovede žádnou akci, pokud žádný panel nástrojů nemá ovládací prvek textové pole, který má stejné ID příkazu jako tento objekt.

Další informace o dialogovém okně **přizpůsobit** naleznete v tématu [Třída CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) tak, že znovu vytvoří interní `CEdit` objekt.

##  <a name="onclick"></a>CMFCToolBarEditBoxButton:: Click

Volá se rozhraním, když uživatel klikne na tlačítko myši.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Nepoužívané.

*bDelay*<br/>
pro Nepoužívané.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zpracovává zprávu kliknutí; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton:: Click](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) tak, že vrátí nenulovou hodnotu, pokud je interní `CEdit` objekt viditelný.

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

Volá se rozhraním, když nadřazený panel nástrojů zpracovává zprávu WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazí tlačítko.

*nCtlColor*<br/>
pro Nepoužívané.

### <a name="return-value"></a>Návratová hodnota

Popisovač globálního okna štětce.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) nastavením barvy textu a pozadí poskytnutého kontextu zařízení na globální barvy textu a pozadí (v uvedeném pořadí).

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, najdete v tématu [Struktura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Volá se rozhraním, když se změní globální písmo.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) změnou písma ovládacího prvku na typ globálního písma.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, najdete v tématu [Struktura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove

Volá se rozhraním, když se přesune nadřazený panel nástrojů.

```
virtual void OnMove();
```

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci výchozí třídy ( [CMFCToolBarButton::](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)s přesunutím) aktualizací pozice interního `CEdit` objektu.

##  <a name="onshow"></a>  CMFCToolBarEditBoxButton::OnShow

Volá se rozhraním, když se tlačítko zobrazí jako viditelné nebo neviditelné.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
pro Určuje, zda je tlačítko viditelné. Pokud má tento parametr hodnotu TRUE, tlačítko je viditelné. V opačném případě není tlačítko viditelné.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: inshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) zobrazením tlačítka, pokud je *bShow* true. V opačném případě tato metoda skrývá tlačítko.

##  <a name="onsize"></a>CMFCToolBarEditBoxButton::-size

Volá se rozhraním, když se změní jeho velikost nebo pozice na nadřazeném panelu nástrojů a tato změna způsobí změnu velikosti tlačítka.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
pro Nová šířka tlačítka v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci výchozí třídy, [CMFCToolBarButton::-size](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizací velikosti a pozice interního `CEdit` objektu.

##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip

Volá se rozhraním, když nadřazený panel nástrojů aktualizuje svůj text popisku.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Nepoužívané.

*iButtonIndex*<br/>
pro Nepoužívané.

*wndToolTip*<br/>
pro Ovládací prvek, který zobrazuje text popisku

*str*<br/>
mimo `CString` Objekt, který obdrží aktualizovaný text popisku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud metoda aktualizuje text popisku; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) zobrazením textu popisku, který je přidružen k části pro úpravy tlačítka. Pokud je interní `CEdit` objekt null nebo popisovač `CEdit` okna objektu neidentifikuje existující okno, tato metoda neprovede žádnou akci a vrátí hodnotu false.

##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

Nastaví text v ovládacím prvku textové pole.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parametry

*sContents*<br/>
pro Určuje nový text, který se má nastavit.

##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Najde objekt [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) , který má zadané ID příkazu, a nastaví zadaný text v rámci jeho textového pole.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro Určuje ID příkazu ovládacího prvku, pro který bude změněn text.

*strContents*<br/>
pro Určuje nový text, který se má nastavit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl text nastaven; 0, `CMFCToolBarEditBoxButton` Pokud ovládací prvek se zadaným ID příkazu neexistuje.

##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Určuje ID prostředku místní nabídky, která je přidružena k tlačítku.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID prostředku místní nabídky

### <a name="remarks"></a>Poznámky

Rozhraní používá ID prostředku k vytvoření místní nabídky, když uživatel klikne pravým tlačítkem myši na tlačítko panelu nástrojů.

##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

Určuje plochý vzhled tlačítek pro úpravu pole v aplikaci.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
pro Plochý styl pro tlačítka pro úpravy Je-li tento parametr TRUE, je povolen plochý vzhled stylu; v opačném případě je zjednodušený vzhled stylu zakázán.

### <a name="remarks"></a>Poznámky

Výchozí plochý styl pro tlačítka pro úpravy pole je TRUE. Pomocí metody [CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode) načtěte vzhled plochého stylu pro vaši aplikaci.

##  <a name="setstyle"></a>CMFCToolBarEditBoxButton:: SetStyle

Určuje styl ovládacího prvku pro textové pole panelu nástrojů.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
pro Nový styl, který se má nastavit

### <a name="remarks"></a>Poznámky

Tato metoda nastaví [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) na *nStyle* také zakáže textové pole, když je aplikace v režimu přizpůsobení, a umožňuje ji, když aplikace není v režimu přizpůsobení (viz [CMFCToolBar:: SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) a [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Seznam platných příznaků stylu naleznete v tématu [styly ovládacích prvků panelu nástrojů](../../mfc/reference/toolbar-control-styles.md) .

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
