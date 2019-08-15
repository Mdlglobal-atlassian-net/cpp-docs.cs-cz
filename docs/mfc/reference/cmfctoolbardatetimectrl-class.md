---
title: CMFCToolBarDateTimeCtrl – třída
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
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504763"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl – třída

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pro výběr data a času.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|`CMFCToolBarDateTimeCtrl` Vytvoří objekt.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Určuje, zda může uživatel roztáhnout tlačítko během přizpůsobení. (Overrides [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko. (Overrides [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Vyhrazeno pro budoucí použití.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Kopíruje text z tlačítka panelu nástrojů do nabídky.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Načte první `CMFCToolBarDateTimeCtrl` objekt v aplikaci, který má zadané ID příkazu.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Vrátí ukazatel na ovládací prvek pro výběr data a času.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Načte popisovač okna, který je přidružený k tlačítku panelu nástrojů. (Overrides [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Získá vybraný čas z ovládacího prvku pro výběr data a času a vloží jej do zadané struktury [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Vrátí vybraný čas z tlačítka ovládacího prvku pro výběr času, které má zadané ID příkazu.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Určuje, zda je zobrazeno ohraničení tlačítka, když uživatel vybere tlačítko. (Overrides [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracovává zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) . (Overrides [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Volá se rozhraním, když se přidá tlačítko do dialogového okna **přizpůsobit** . (Overrides [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Volá se rozhraním, aby se počítala velikost tlačítka pro zadaný kontext zařízení a stav docking. (Overrides [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko. (Overrides [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Volá se rozhraním, když uživatel klikne na ovládací prvek. (Potlačení [CMFCToolBarButton:: Click](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Volá se rozhraním, když nadřazený panel nástrojů zpracovává zprávu WM_CTLCOLOR. (Overrides [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Volá se rozhraním, aby se vykreslilo tlačítko pomocí zadaných stylů a možností. (Overrides [CMFCToolBarButton:: nakreslit](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Volá se rozhraním, aby se nakreslilo tlačítko v podokně **příkazy** dialogového okna **přizpůsobit** . (Overrides [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Volá se rozhraním, když se změní globální písmo. (Overrides [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Volá se rozhraním, když se přesune nadřazený panel nástrojů. (Overrides [CMFCToolBarButton::-Move](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Volá se rozhraním, když se tlačítko zobrazí jako viditelné nebo neviditelné. (Overrides [CMFCToolBarButton:: inshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Volá se rozhraním, když se změní jeho velikost nebo pozice na nadřazeném panelu nástrojů a tato změna způsobí změnu velikosti tlačítka. (Overrides [CMFCToolBarButton::-size](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Volá se rozhraním, když nadřazený panel nástrojů aktualizuje svůj text popisku. (Overrides [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Přečte tento objekt z archivu nebo ho zapíše do archivu (Overrides [CMFCToolBarButton:: serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).).|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Nastaví styl tlačítka panelu nástrojů. (Overrides [CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Nastaví datum a čas v ovládacím prvku pro výběr času.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Nastaví datum a čas ve všech instancích ovládacího prvku pro výběr času, který má zadané ID příkazu.|

## <a name="remarks"></a>Poznámky

Příklad použití ovládacího prvku pro výběr data a času naleznete v ukázkovém projektu ToolbarDateTimePicker. Informace o tom, jak přidat řídicí tlačítka na panely nástrojů, [najdete v tématu Návod: Vložení ovládacích prvků na](../../mfc/walkthrough-putting-controls-on-toolbars.md)panely nástrojů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxtoolbardatetimectrl.h

##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

Určuje, zda může uživatel roztáhnout tlačítko během přizpůsobení.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní neumožňuje uživateli roztáhnout tlačítko panelu nástrojů během přizpůsobení. Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že umožňuje uživateli roztáhnout tlačítko panelu nástrojů data a času během přizpůsobení.

##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Vytvoří a inicializuje objekt [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) .

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
pro ID ovládacího prvku

*iImage*<br/>
pro Index obrázku v `CMFCToolBarImages` objektu panelu nástrojů

*dwStyle*<br/>
pro Styl `CMFCToolBarDateTimeCtrlImpl` okna, které se vytvoří, když uživatel klikne na tlačítko

*iWidth*<br/>
pro Šířka ovládacího prvku (v pixelech).

### <a name="remarks"></a>Poznámky

Tento objekt je inicializován do systémového data a času. Styl okna interního `CMFCToolBarDateTimeCtrlImpl` objektu obsahuje parametr *dwStyle* a styly WS_CHILD a WS_VISIBLE. Tyto styly nemůžete změnit pomocí `CMFCToolBarDateTimeCtrl::SetStyle`. Slouží `SetStyle` ke změně stylu `CMFCToolBarDateTimeCtrl` ovládacího prvku.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarDateTimeCtrl` třídy. Tento fragment kódu je součástí [ukázky ovládacího prvku pro výběr data a času na panelu nástrojů](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom

Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
pro Odkaz na zdrojové tlačítko, ze kterého se má kopírovat.

### <a name="remarks"></a>Poznámky

Voláním této metody zkopírujte další tlačítko panelu nástrojů na toto tlačítko panelu nástrojů. *Src* musí být typu `CMFCToolBarDateTimeCtrl`.

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

Kopíruje text z tlačítka panelu nástrojů do nabídky.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
pro Odkaz na tlačítko cílové nabídky

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) načtením prostředku řetězce, který je spojen s ID příkazu ovládacího prvku. Další informace o řetězcových zdrojích naleznete v tématu [CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Načte první `CMFCToolBarDateTimeCtrl` objekt v aplikaci, který má zadané ID příkazu.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko, které se má načíst

### <a name="return-value"></a>Návratová hodnota

První `CMFCToolBarDateTimeCtrl` objekt v aplikaci, který má zadané ID příkazu, nebo hodnotu null, pokud žádné `CMFCToolBarDateTimeCtrl` objekty nemají zadané ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda sdíleného nástroje je používána metodami, jako je [CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall) a [CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall) pro nastavení nebo získání času a data všech instancí ovládacího prvku pro výběr času, který má zadané ID příkazu.

##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Vrátí ukazatel na ovládací prvek pro výběr data a času.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek pro výběr data a času; nebo hodnotu NULL, pokud ovládací prvek neexistuje.

### <a name="remarks"></a>Poznámky

Třída inicializuje datový člen při vložení objektu na panel nástrojů. `CMFCToolBarDateTimeCtrl` `CMFCToolBarDateTimeCtrl` `m_pWndDateTime`

##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl:: GetHwnd

Načte popisovač okna, který je přidružený k tlačítku panelu nástrojů.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna, který je spojen s tlačítkem panelu nástrojů data a času.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje metodu [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) .

##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl:: GetTime

Získá vybraný čas z ovládacího prvku výběru přidruženého data a času a vloží ho do zadané struktury [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
mimo V prvním přetížení objekt [třídy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , který obdrží informace o čase systému. Ve druhém přetížení se objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obdrží informace o čase systému.

*pTimeDest*<br/>
mimo Ukazatel na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , který obdrží informace o čase systému. Nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

V prvním přetížení, nenulové, pokud je čas úspěšně zapsán do objektu [třídy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ; v opačném případě 0. Ve druhé a třetí přetížení je návratová hodnota DWORD, která je rovna členu dwFlag, který byl nastaven ve struktuře [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) .

### <a name="remarks"></a>Poznámky

Metoda nastaví člena struktury [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) na dwFlags, aby označoval, zda je výběr data a času nastaven na datum a čas. Pokud se hodnota rovná GDT_NONE, je ovládací prvek nastaven na `no date` stav a používá styl DTS_SHOWNONE. Pokud se hodnota vrátí jako GDT_VALID, je systémový čas úspěšně uložen do cílového umístění.

##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Vrátí čas vybraný uživatelem v ovládacím prvku pro výběr času, který má zadané ID příkazu.

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
pro Určuje ID příkazu tlačítka panelu nástrojů.

*timeDest*<br/>
mimo V prvním přetížení objekt [třídy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , který obdrží informace o čase systému. Ve druhém přetížení se objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obdrží informace o čase systému.

*pTimeDest*<br/>
mimo Ukazatel na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , který obdrží informace o čase systému. Nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud rozhraní nemůže najít tlačítko panelu nástrojů, které odpovídá ID příkazu *uiCmd*, návratová hodnota je nula v prvním přetížení a GDT_NONE v dalších přetíženích. Pokud je nalezeno tlačítko panelu nástrojů, návratová hodnota je stejná jako návratová hodnota ze volání [CMFCToolBarDateTimeCtrl:: GetTime](#gettime) na tomto tlačítku. Návratová hodnota nula nebo GDT_NONE může nastat při nalezení tlačítka, což indikuje, že volání `GetTime` nevrátilo platné datum z nějakého jiného důvodu.

### <a name="remarks"></a>Poznámky

Tato metoda hledá tlačítko panelu nástrojů, které má zadané ID příkazu a volá metodu [CMFCToolBarDateTimeCtrl:: GetTime](#gettime) na toto tlačítko.

##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Určuje, zda je zobrazeno ohraničení tlačítka, když uživatel vybere tlačítko.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko při výběru zobrazí jeho ohraničení; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda vrací nenulovou hodnotu, pokud je ovládací prvek viditelný.

##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Určuje, zda tlačítko zpracovává zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
pro Zpráva s oznámením, která je přidružena k příkazu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tlačítko zpracuje zprávu WM_COMMAND, nebo FALSE, aby označovala, že by měla být zpráva zpracována nadřazeným panelem nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když se chystá odeslat zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) do nadřazeného okna.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním oznámení [DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange) . Aktualizuje stav interního času a aktualizuje vlastnost čas všech `CMFCToolBarDateTimeCtrl` objektů se stejným ID příkazu.

##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Volá se rozhraním, když se přidá tlačítko do dialogového okna **přizpůsobit** .

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), zkopírováním vlastností z prvního ovládacího prvku data a času v jakémkoli panelu nástrojů, který má stejné ID příkazu jako tento objekt. Tato metoda neprovede žádnou akci, pokud žádný panel nástrojů nemá ovládací prvek data a času, který má stejné ID příkazu jako tento objekt.

Další informace o dialogovém okně **přizpůsobit** naleznete v tématu [Třída CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) tak, že znovu vytvoří interní `CMFCToolBarDateTimeCtrlImpl` objekt.

##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl:: Click

Volá se rozhraním, když uživatel klikne na ovládací prvek.

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

Tato metoda přepisuje implementaci základní třídy, [CMFCToolBarButton:: Click](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), vrácením nenulové hodnoty, pokud je interní `CMFCToolBarDateTimeCtrlImpl` objekt viditelný.

##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

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

Popisovač globálního štětce, který rozhraní používá k vykreslování pozadí tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy, [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), nastavením barvy textu a pozadí poskytnutého kontextu zařízení na globální text a barvy pozadí v uvedeném pořadí.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, najdete v tématu [Struktura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Volá se rozhraním, když se změní globální písmo.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) změnou písma ovládacího prvku na typ globálního písma.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, najdete v tématu [Struktura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::-Move

Volá se rozhraním, když se přesune nadřazený panel nástrojů.

```
virtual void OnMove();
```

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci výchozí třídy ( [CMFCToolBarButton::](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)s přesunutím) aktualizací pozice interního `CMFCToolBarDateTimeCtrlImpl` objektu.

##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl:: inshow

Volá se rozhraním, když se tlačítko zobrazí jako viditelné nebo neviditelné.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
pro Určuje, zda je tlačítko viditelné. Pokud má tento parametr hodnotu TRUE, tlačítko je viditelné. V opačném případě není tlačítko viditelné.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: inshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) zobrazením tlačítka, pokud je *bShow* true. V opačném případě tato metoda skrývá tlačítko.

##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl::-size

Volá se rozhraním, když se změní jeho velikost nebo pozice na nadřazeném panelu nástrojů a tato změna způsobí změnu velikosti tlačítka.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
pro Nová šířka tlačítka v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci výchozí třídy ( [CMFCToolBarButton:: s velikostí](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) aktualizací velikosti a pozice interního `CMFCToolBarDateTimeCtrlImpl` objektu.

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
pro Nadřazené okno

*iButtonIndex*<br/>
pro Index tlačítka založený na nule v nadřazené kolekci tlačítek.

*wndToolTip*<br/>
pro Ovládací prvek, který zobrazuje text popisku

*str*<br/>
mimo `CString` Objekt, který obdrží aktualizovaný text popisku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud metoda aktualizuje text popisku; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) zobrazením textu popisku, který je spojen s tlačítkem. Pokud tlačítko není ukotveno vodorovně, tato metoda neprovede žádnou akci a vrátí hodnotu FALSE.

##  <a name="settime"></a>CMFCToolBarDateTimeCtrl:: SetTime –

Nastaví datum a čas v ovládacím prvku pro výběr času.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
pro V první verzi odkaz na objekt [třídy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , který obsahuje čas, do kterého bude ovládací prvek nastaven. Ve druhé verzi je ukazatel na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obsahuje čas, do kterého bude ovládací prvek nastaven.

*pTimeNew*<br/>
pro Ukazatel na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje čas, do kterého bude ovládací prvek nastaven.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nastaví čas v ovládacím prvku pro výběr data a času voláním [atributu CDateTimeCtrl:: SetTime –](../../mfc/reference/cdatetimectrl-class.md#settime).

##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

Nastaví datum a čas ve všech instancích ovládacího prvku pro výběr času, který má zadané ID příkazu.

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
pro Určuje ID příkazu tlačítka panelu nástrojů.

*timeNew*<br/>
pro V první verzi objekt [třídy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obsahující čas, do kterého bude ovládací prvek nastaven. Ve druhé verzi je ukazatel na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , který obsahuje čas, do kterého bude ovládací prvek nastaven.

*pTimeNew*<br/>
pro Ukazatel na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , která obsahuje čas, do kterého bude ovládací prvek nastaven.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vyhledá tlačítko panelu nástrojů se zadaným ID příkazu a nastaví čas v ovládacím prvku pro výběr data a času voláním [CMFCToolBarDateTimeCtrl:: SetTime –](#settime).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
