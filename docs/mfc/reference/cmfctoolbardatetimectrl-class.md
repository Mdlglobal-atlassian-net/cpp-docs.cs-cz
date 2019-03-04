---
title: CMFCToolBarDateTimeCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: c93d8a2a18518cad8b6fb7fe014828011f78a653
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280989"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl Class

Tlačítka panelu nástrojů obsahující ovládací prvek pro výběr data a času.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Vytvoří `CMFCToolBarDateTimeCtrl` objektu.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Určuje, jestli uživatel může roztáhnout tlačítko během přizpůsobování. (Přepíše [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Zkopíruje aktuální tlačítko Vlastnosti jiné tlačítko panelu nástrojů. (Přepíše [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Vyhrazeno pro budoucí použití.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Zkopíruje text tlačítka na panelu nástrojů do nabídky.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Načte první `CMFCToolBarDateTimeCtrl` objektu v aplikaci, která má ID zadaného příkazu.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Vrací ukazatel na prvek Výběr data a času.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Načte popisovač okna, která souvisí s tlačítka panelu nástrojů. (Přepíše [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Získá ve vybraném čase z ovládacího prvku pro výběr data a času a vloží jej do zadaného [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktury.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Vrátí hodnotu ve vybraném čase z na tlačítko ovládacího prvku pro výběr času, který má ID zadaného příkazu.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Určuje, zda se zobrazí ohraničení tlačítka, když uživatel vybere tlačítko. (Přepíše [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracovává [wm_command –](/windows/desktop/menurc/wm-command) zprávy. (Přepíše [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Volá se rozhraním, když se přidá tlačítko do **vlastní** dialogové okno. (Přepíše [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Volá se rozhraním pro výpočet velikosti tlačítko pro zadané zařízení kontext a stav dokování. (Přepíše [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním při vložení do nového panelu nástrojů na tlačítko. (Přepíše [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Volá se rozhraním, když uživatel klikne ovládací prvek. (Přepíše [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Volá se rozhraním, když nadřazeného panelu nástrojů zpracovává WM_CTLCOLOR – zpráva. (Přepíše [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Volá se rozhraním, chcete-li nakreslit tlačítko s použitím zadaného styly a možnosti. (Přepíše [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Volá se rozhraním, chcete-li nakreslit tlačítko **příkazy** podokně **vlastní** dialogové okno. (Přepíše [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Volá se rozhraním, když došlo ke změně globální písma. (Overrides [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Volá se rozhraním, když se přesune nadřazeného panelu nástrojů. (Přepíše [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Volá se rozhraním při tlačítka stane viditelné nebo neviditelné. (Přepíše [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Volá se rozhraním, když nadřazeného panelu nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že tlačítko Změnit velikost. (Přepíše [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Volá se rozhraním, když nadřazeného panelu nástrojů aktualizuje její přejede myší. (Overrides [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Čte tento objekt z archivu nebo zapíše do archivu (přepíše [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Nastaví styl tlačítka panelu nástrojů. (Přepíše [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Nastaví datum a čas v ovládacím prvku pro výběr času.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Nastaví datum a čas ve všech instancích ovládacího prvku pro výběr času, které mají ID zadaného příkazu.|

## <a name="remarks"></a>Poznámky

Příklad použití ovládacího prvku pro výběr data a času naleznete v tématu ToolbarDateTimePicker ukázkového projektu. Informace o tom, jak přidat ovládací prvek tlačítka na panely nástrojů najdete v tématu [názorný postup: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxtoolbardatetimectrl.h

##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched

Určuje, jestli uživatel může roztáhnout tlačítko během přizpůsobování.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní neumožňuje uživateli během přizpůsobování roztáhnout tlačítka panelu nástrojů. Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že uživatel během přizpůsobování roztáhnout data a času tlačítka panelu nástrojů.

##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Vytvoří a inicializuje [cmfctoolbardatetimectrl –](../../mfc/reference/cmfctoolbardatetimectrl-class.md) objektu.

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] ID ovládacího prvku.

*iImage*<br/>
[in] Index bitové kopie v panelu nástrojů `CMFCToolBarImages` objektu.

*dwStyle*<br/>
[in] Styl `CMFCToolBarDateTimeCtrlImpl` okno, které se vytvoří, když uživatel klikne na tlačítko.

*iWidth*<br/>
[in] Šířka ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

Tento objekt je inicializován na systémové datum a čas. Styl okna vnitřního `CMFCToolBarDateTimeCtrlImpl` objekt zahrnuje *dwStyle* parametr a WS_CHILD a WS_VISIBLE styly. Tyto styly nelze změnit pomocí `CMFCToolBarDateTimeCtrl::SetStyle`. Použití `SetStyle` změnit styl `CMFCToolBarDateTimeCtrl` ovládacího prvku.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarDateTimeCtrl` třídy. Tento fragment kódu je součástí [nástrojů Výběr data a času ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

Zkopíruje aktuální tlačítko Vlastnosti jiné tlačítko panelu nástrojů.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Odkaz na tlačítko zdroj ze kterého chcete kopírovat.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem kopírování jiné tlačítko panelu nástrojů do tohoto tlačítka panelu nástrojů. *src* musí být typu `CMFCToolBarDateTimeCtrl`.

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

Zkopíruje text tlačítka na panelu nástrojů do nabídky.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*Tlačítko nabídky*<br/>
[in] Odkaz na tlačítko nabídky Cíl.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) načtením prostředek řetězce, který je spojen s Identifikátorem příkazu ovládacího prvku. Další informace o řetězcové prostředky, najdete v části [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd

Načte první `CMFCToolBarDateTimeCtrl` objektu v aplikaci, která má ID zadaného příkazu.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pro načtení.

### <a name="return-value"></a>Návratová hodnota

První `CMFCToolBarDateTimeCtrl` objektu v aplikaci, která má ID zadaného příkazu nebo hodnota NULL, pokud žádné `CMFCToolBarDateTimeCtrl` objekty mají ID zadaného příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda sdílený nástroj používá metody, jako [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) a [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) nastavit nebo získat času a data všech instancí času ovládací prvek výběru, které mají ID zadaného příkazu.

##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Vrací ukazatel na prvek Výběr data a času.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek Výběr data a času; nebo hodnota NULL, pokud ovládací prvek neexistuje.

### <a name="remarks"></a>Poznámky

`CMFCToolBarDateTimeCtrl` Třídy inicializuje `m_pWndDateTime` datový člen při vložení `CMFCToolBarDateTimeCtrl` objektu na panelu nástrojů.

##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd

Načte popisovač okna, která souvisí s tlačítka panelu nástrojů.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna, která souvisí s datem a časem tlačítka panelu nástrojů.

### <a name="remarks"></a>Poznámky

Přepíše tuto metodu [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metody.

##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime

Získá ve vybraném čase z přidružené datum a čas ovládací prvek pro výběr a umístí jej v zadané [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktura

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
[out] V první přetížení [COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který se zobrazí informace o času systému. V druhé přetížení [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který se zobrazí informace o času systému.

*pTimeDest*<br/>
[out] Ukazatel [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktura přijímat informace o času systému. Nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

V první přetížení nenulové, pokud čas je úspěšně zapsána do [COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md) objektu; jinak 0. V druhé a třetí přetížení, vrácená hodnota je typu DWORD, který je roven dwFlag člena, která byla nastavena v [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) struktury.

### <a name="remarks"></a>Poznámky

Nastaví metodu [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) struktury člena dwFlags označující, zda nástroj pro výběr data a času je nastavena na datum a čas. Pokud je hodnota GDT_NONE, ovládacího prvku nastavená na `no date` stav a používá DTS_SHOWNONE styl. Pokud je vrácená hodnota GDT_VALID, systémového času úspěšně uloženy v cílovém umístění.

##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll

Vrátí čas vybraných uživatelem z na tlačítko ovládacího prvku pro výběr času, který má ID zadaného příkazu.

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Určuje ID příkazu pro tlačítka panelu nástrojů.

*timeDest*<br/>
[out] V první přetížení [COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který se zobrazí informace o času systému. V druhé přetížení [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který se zobrazí informace o času systému.

*pTimeDest*<br/>
[out] Ukazatel [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktura přijímat informace o času systému. Nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud rozhraní framework nemůže najít odpovídající Identifikátor příkazu tlačítka panelu nástrojů *uiCmd*, vrácená hodnota je nula v první přetížení a GDT_NONE v dalšími přetíženími. Pokud je nalezen tlačítka panelu nástrojů, vrácená hodnota je stejná jako návratová hodnota z volání [CMFCToolBarDateTimeCtrl::GetTime](#gettime) na toto tlačítko. Návratová hodnota nula nebo GDT_NONE může dojít, když tlačítko nenajde, což znamená, že volání `GetTime` nevrátil platné datum nějakého jiného důvodu.

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá tlačítka panelu nástrojů, která má ID zadaného příkazu a volání [CMFCToolBarDateTimeCtrl::GetTime](#gettime) metodu na toto tlačítko.

##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder

Určuje, zda se zobrazí ohraničení tlačítka, když uživatel vybere tlačítko.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zobrazí jeho ohraničení. při výběru; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí nenulovou hodnotu, pokud je ovládací prvek viditelný.

##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand

Určuje, zda tlačítko zpracovává [wm_command –](/windows/desktop/menurc/wm-command) zprávy.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
[in] Zprávy oznámení, který je přidružený příkaz.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tlačítko zpracovává wm_command – zprávy nebo hodnotu NEPRAVDA označuje, že zprávy by měl být zpracovány nadřazeného panelu nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když je odeslat [wm_command –](/windows/desktop/menurc/wm-command) zprávu nadřazenému oknu.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním [dtn_datetimechange –](/windows/desktop/Controls/dtn-datetimechange) oznámení. Čas vnitřního stavu aktualizací a aktualizuje vlastnosti času všech `CMFCToolBarDateTimeCtrl` objektů se stejným Apple ID.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Volá se rozhraním, když se přidá tlačítko do **vlastní** dialogové okno.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), tím, že kopírování vlastnosti z první datum a čas ovládacího prvku v libovolný nástrojů, který má stejné ID příkazu jako tento objekt. Tato metoda nemá žádný účinek, pokud ovládací prvek datum a čas, který má stejné ID příkazu jako tento objekt nemá žádné nástrojů.

Další informace o **vlastní** dialogovém okně naleznete v tématu [cmfctoolbarscustomizedialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Volá se rozhraním při vložení do nového panelu nástrojů na tlačítko.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) prostřednictvím přetvoření vnitřní `CMFCToolBarDateTimeCtrlImpl` objektu.

##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick

Volá se rozhraním, když uživatel klikne ovládací prvek.

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

Tato metoda přepíše metodu základní třídy implementace [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), tak, že vrací nenulovou hodnotu, pokud vnitřní `CMFCToolBarDateTimeCtrlImpl` je objekt viditelný.

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

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

Popisovač pro globální štětec, který systém použije k vykreslení na pozadí tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše metodu základní třídy implementace [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), tím, že nastavení textu a pozadí barvy kontextu zadané zařízení globální textu a barvy pozadí v uvedeném pořadí.

Další informace o globální možnosti, které jsou k dispozici pro vaši aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Volá se rozhraním, když došlo ke změně globální písma.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) tak, že změníte písmo ovládacího prvku, který globální písma.

Další informace o globální možnosti, které jsou k dispozici pro vaši aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove

Volá se rozhraním, když se přesune nadřazeného panelu nástrojů.

```
virtual void OnMove();
```

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje výchozí implementaci třídy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) aktualizací pozice vnitřního `CMFCToolBarDateTimeCtrlImpl` objektu.

##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow

Volá se rozhraním při tlačítka stane viditelné nebo neviditelné.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] Určuje, zda je viditelný na tlačítko. Pokud tento parametr má hodnotu TRUE, je viditelný na tlačítko. V opačném případě na tlačítko se nezobrazuje.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) tím, že pokud se zobrazuje tlačítko *bShow* má hodnotu TRUE. Jinak tato metoda skryje tlačítko.

##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize

Volá se rozhraním, když nadřazeného panelu nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že tlačítko Změnit velikost.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
[in] Novou šířku tlačítka v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje výchozí implementaci třídy ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) aktualizací velikost a umístění vnitřního `CMFCToolBarDateTimeCtrlImpl` objektu.

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
[in] Nadřazené okno.

*iButtonIndex*<br/>
[in] Index založený na nule tlačítko v nadřazené tlačítko kolekce.

*wndToolTip*<br/>
[in] Ovládací prvek, který zobrazí text popisku.

*str*<br/>
[out] A `CString` objekt, který přijme aktualizovaná přejede myší.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud metoda aktualizuje přejede myší; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) tím, že zobrazuje text popisku, který je přidružený k tlačítku. Pokud tlačítko není ukotven vodorovně, tato metoda neprovede žádnou akci a vrátí hodnotu FALSE.

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

Nastaví datum a čas v ovládacím prvku pro výběr času.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
[in] V první verzi odkaz na [COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje čas, ke kterému bude ovládací prvek nastavit. V druhou verzi, ukazatel [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, ke kterému bude ovládací prvek nastavit.

*pTimeNew*<br/>
[in] Ukazatel [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obsahuje čas, ke kterému bude ovládací prvek nastavit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Nastaví dobu v ovládacím prvku Výběr data a času voláním [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll

Nastaví datum a čas ve všech instancích ovládacího prvku pro výběr času, které mají ID zadaného příkazu.

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Určuje ID příkazu pro tlačítka panelu nástrojů.

*timeNew*<br/>
[in] V první verzi [COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje čas, ke kterému bude ovládací prvek nastavit. V druhou verzi, ukazatel [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, ke kterému bude ovládací prvek nastavit.

*pTimeNew*<br/>
[in] Ukazatel [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obsahuje čas, ke kterému bude ovládací prvek nastavit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Vyhledá tlačítka panelu nástrojů s ID zadaného příkazu a nastaví dobu v ovládacím prvku Výběr data a času voláním [CMFCToolBarDateTimeCtrl::SetTime](#settime).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Návod: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
