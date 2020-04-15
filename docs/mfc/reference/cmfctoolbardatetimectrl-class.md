---
title: TŘÍDA CMFCToolBarDateTimeCtrl
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
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372178"
---
# <a name="cmfctoolbardatetimectrl-class"></a>TŘÍDA CMFCToolBarDateTimeCtrl

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pro výběr data a času.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl:::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Vytvoří `CMFCToolBarDateTimeCtrl` objekt.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Určuje, zda může uživatel tlačítko během vlastního nastavení roztáhnout. (Přepíše [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko. (Přepíše [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Vyhrazeno pro budoucí použití.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Zkopíruje text z tlačítka panelu nástrojů do nabídky.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Načte první `CMFCToolBarDateTimeCtrl` objekt v aplikaci, který má zadané ID příkazu.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Vrátí ukazatel ovládacího prvku pro výběr data a času.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Načte popisovač okna, který je přidružen k tlačítku panelu nástrojů. (Přepíše [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Získá vybraný čas z ovládacího prvku výběru data a času a vloží jej do zadané struktury [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Vrátí vybraný čas z ovládacího tlačítka pro výběr času, které má zadané ID příkazu.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Určuje, zda se po výběru tlačítka zobrazí ohraničení tlačítka. (Přepíše [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracuje [zprávu WM_COMMAND.](/windows/win32/menurc/wm-command) (Přepíše [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Volat rámci při přidání tlačítka do dialogového okna **Přizpůsobit.** (Přepíše [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Volat rámci vypočítat velikost tlačítka pro zadaný kontext zařízení a dokovací stav. (Přepíše [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Volat rámci při vložení tlačítka do nového panelu nástrojů. (Přepíše [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Volat rámci při uživatel i klepne na ovládací prvek. (Přepíše [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Volat rámci při nadřazený panel nástrojů zpracovává WM_CTLCOLOR zprávu. (Přepíše [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Volat rámci nakreslit tlačítko pomocí zadaných stylů a možností. (Přepíše [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Volat rámci nakreslit tlačítko v podokně **příkazy** dialogového okna **Přizpůsobit.** (Přepíše [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Volat rámci při změně globální písmo. (Přepíše [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Volat rámci při přesune nadřazený panel nástrojů. (Přepíše [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Volat rámci při tlačítko stane viditelné nebo neviditelné. (Přepíše [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Volat rámci při nadřazený panel nástrojů změní svou velikost nebo umístění a tato změna způsobí, že tlačítko změnit velikost. (Přepíše [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Volat rámci při nadřazený panel nástrojů aktualizuje text popisného popisu. (Přepíše [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Přečte tento objekt z archivu nebo jej zapíše do archivu (Přepíše [CMFCToolBarButton::Serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Nastaví styl tlačítka panelu nástrojů. (Přepíše [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Nastaví čas a datum v ovládacím prvku pro výběr času.|
|[CMFCToolBarDateTimeCtrl::SetTimeall](#settimeall)|Nastaví čas a datum ve všech instancích ovládacího prvku pro výběr času, které mají zadané ID příkazu.|

## <a name="remarks"></a>Poznámky

Příklad použití ovládacího prvku výběru data a času naleznete v ukázkovém projektu ToolbarDateTimePicker. Informace o přidání ovládacích tlačítek na panely nástrojů naleznete v [tématu Návod: Uvedení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

Určuje, zda může uživatel tlačítko během vlastního nastavení roztáhnout.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní neumožňuje uživateli roztáhnout tlačítko panelu nástrojů během vlastního nastavení. Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že umožňuje uživateli roztáhnout tlačítko panelu nástrojů data a času během vlastního nastavení.

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl:::CMFCToolBarDateTimeCtrl

Vytvoří a inicializuje objekt [CMFCToolBarDateTimeCtrl.](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] ID ovládacího prvku.

*iImage*<br/>
[v] Index obrazu v `CMFCToolBarImages` objektu panelu nástrojů.

*dwStyl*<br/>
[v] Styl okna, `CMFCToolBarDateTimeCtrlImpl` který je vytvořen, když uživatel klepne na tlačítko.

*iŠířka*<br/>
[v] Šířka ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

Tento objekt je inicializován na systémové datum a čas. Styl okna vnitřního `CMFCToolBarDateTimeCtrlImpl` objektu zahrnuje parametr *dwStyle* a styly WS_CHILD a WS_VISIBLE. Tyto styly nelze `CMFCToolBarDateTimeCtrl::SetStyle`změnit pomocí aplikace . Slouží `SetStyle` ke změně stylu `CMFCToolBarDateTimeCtrl` ovládacího prvku.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarDateTimeCtrl` třídy. Tento fragment kódu je součástí [ukázky výběru času panelu nástrojů](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom

Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Odkaz na zdrojové tlačítko, ze kterého chcete kopírovat.

### <a name="remarks"></a>Poznámky

Volánítéto metody zkopírovat jiné tlačítko panelu nástrojů na toto tlačítko panelu nástrojů. *src* musí být `CMFCToolBarDateTimeCtrl`typu .

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarDateTimectrl::ExportToMenuButton

Zkopíruje text z tlačítka panelu nástrojů do nabídky.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
[v] Odkaz na tlačítko cílové nabídky.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton::ExportToMenuButton)](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)načtením prostředku řetězce, který je přidružen k ID příkazu ovládacího prvku. Další informace o řetězcových prostředcích naleznete v tématu [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Načte první `CMFCToolBarDateTimeCtrl` objekt v aplikaci, který má zadané ID příkazu.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pro načtení.

### <a name="return-value"></a>Návratová hodnota

První `CMFCToolBarDateTimeCtrl` objekt v aplikaci, který má zadané ID `CMFCToolBarDateTimeCtrl` příkazu, nebo NULL, pokud žádné objekty nemají zadané ID příkazu.

### <a name="remarks"></a>Poznámky

Tato sdílená metoda nástroje je používána metodami, jako je [NAPŘÍKLAD CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) a [CMFCToolBarDateTimeTimeCtrl::GetTimeAll](#gettimeall) pro nastavení nebo získání času a data všech instancí ovládacího prvku pro výběr času, které mají zadané ID příkazu.

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Vrátí ukazatel ovládacího prvku pro výběr data a času.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek pro výběr data a času; nebo NULL, pokud ovládací prvek neexistuje.

### <a name="remarks"></a>Poznámky

Třída `CMFCToolBarDateTimeCtrl` inicializuje `m_pWndDateTime` datový člen při `CMFCToolBarDateTimeCtrl` vložení objektu do panelu nástrojů.

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

Načte popisovač okna, který je přidružen k tlačítku panelu nástrojů.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna, který je přidružen k tlačítku panelu nástrojů data a času.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše [metodu CMFCToolBarButton::GetHwnd.](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime

Získá vybraný čas z přidruženého ovládacího prvku výběru data a času a vloží jej do zadané struktury [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
[out] V první přetížení [COleDateTime class](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obdrží informace o systémovém čase. V druhé přetížení [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obdrží informace o systémovém čase.

*pTimeDest*<br/>
[out] Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu přijímat informace o systémovém čase. Nesmí být null.

### <a name="return-value"></a>Návratová hodnota

V první přetížení nenulová, pokud je čas úspěšně zapsán do [cOleDateTime class objektu;](../../atl-mfc-shared/reference/coledatetime-class.md) jinak 0. V druhé a třetí přetížení vrácená hodnota je DWORD, který se rovná dwFlag člen, který byl nastaven ve struktuře [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)

### <a name="remarks"></a>Poznámky

Metoda nastaví [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) člen struktury dwFlags k označení, zda je výběr data a času nastaven na datum a čas. Pokud se hodnota rovná GDT_NONE, ovládací `no date` prvek je nastaven na stav a používá styl DTS_SHOWNONE. Pokud se vrácená hodnota rovná GDT_VALID, systémový čas je úspěšně uložen v cílovém umístění.

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Vrátí čas vybraný uživatelem z ovládacího tlačítka pro výběr času, které má zadané ID příkazu.

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
[v] Určuje ID příkazu tlačítka panelu nástrojů.

*timeDest*<br/>
[out] V první přetížení [COleDateTime class](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obdrží informace o systémovém čase. V druhé přetížení [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obdrží informace o systémovém čase.

*pTimeDest*<br/>
[out] Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu přijímat informace o systémovém čase. Nesmí být null.

### <a name="return-value"></a>Návratová hodnota

Pokud rozhraní nelze najít tlačítko panelu nástrojů, který odpovídá ID příkazu *uiCmd*, vrácená hodnota je nula v první přetížení a GDT_NONE v ostatní přetížení. Pokud je nalezeno tlačítko panelu nástrojů, vrácená hodnota je stejná jako vrácená hodnota z volání [CMFCToolBarDateTimeCtrl::GetTime](#gettime) na tomto tlačítku. Vrácená hodnota nula nebo GDT_NONE může dojít při nalezení tlačítka, což znamená, že volání `GetTime` nevrátilplatné datum z nějakého jiného důvodu.

### <a name="remarks"></a>Poznámky

Tato metoda hledá tlačítko panelu nástrojů, které má zadané ID příkazu a volá [metodu CMFCToolBarDateTimeCtrl::GetTime](#gettime) na tomto tlačítku.

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Určuje, zda se po výběru tlačítka zobrazí ohraničení tlačítka.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zobrazí jeho ohraničení, když je vybráno; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí nenulovou hodnotu, pokud je ovládací prvek viditelný.

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Určuje, zda tlačítko zpracuje [zprávu WM_COMMAND.](/windows/win32/menurc/wm-command)

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
[v] Zpráva s oznámením, která je přidružena k příkazu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud tlačítko zpracuje WM_COMMAND zprávu nebo NEPRAVDA, což znamená, že zpráva by měla být zpracována nadřazeným panelem nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu, když se chystá odeslat [zprávu WM_COMMAND](/windows/win32/menurc/wm-command) do nadřazeného okna.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním [oznámení DTN_DATETIMECHANGE.](/windows/win32/Controls/dtn-datetimechange) Aktualizuje vnitřní stav času a aktualizuje vlastnost `CMFCToolBarDateTimeCtrl` time všech objektů se stejným ID příkazu.

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Volat rámci při přidání tlačítka do dialogového okna **Přizpůsobit.**

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::OnAddToCustomizePage,](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)zkopírováním vlastností od prvního data a časového ovládacího prvku v libovolném panelu nástrojů, který má stejné ID příkazu jako tento objekt. Tato metoda neprovede žádnou akci, pokud žádný panel nástrojů nemá ovládací prvek data a času, který má stejné ID příkazu jako tento objekt.

Další informace o dialogovém **okně Přizpůsobit** naleznete v tématu [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Volat rámci při vložení tlačítka do nového panelu nástrojů.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) opětovným vytvořením vnitřního `CMFCToolBarDateTimeCtrlImpl` objektu.

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick

Volat rámci při uživatel i klepne na ovládací prvek.

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

Tato metoda přepíše implementaci základní třídy [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), vrácením `CMFCToolBarDateTimeCtrlImpl` nenulové hodnoty, pokud je viditelný vnitřní objekt.

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

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

Úchyt globální štětce, který rámci používá k malování pozadí tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)nastavením barev textu a pozadí kontextu poskytnutého zařízení na globální text a barvy pozadí.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, naleznete [v tématu AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Volat rámci při změně globální písmo.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) změnou písma ovládacího prvku na písmo globálního písma.

Další informace o globálních možnostech, které jsou k dispozici pro vaši aplikaci, naleznete [v tématu AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

Volat rámci při přesune nadřazený panel nástrojů.

```
virtual void OnMove();
```

### <a name="remarks"></a>Poznámky

Tato metoda přepíše výchozí implementaci třídy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove) `CMFCToolBarDateTimeCtrlImpl` ) aktualizací polohy vnitřního objektu.

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

Volat rámci při tlačítko stane viditelné nebo neviditelné.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] Určuje, zda je tlačítko viditelné. Pokud je tento parametr TRUE, tlačítko je viditelné. V opačném případě tlačítko není viditelné.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) zobrazením tlačítka, pokud *je hodnota bShow* TRUE. V opačném případě tato metoda skryje tlačítko.

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize

Volat rámci při nadřazený panel nástrojů změní svou velikost nebo umístění a tato změna způsobí, že tlačítko změnit velikost.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iVelikost*<br/>
[v] Nová šířka tlačítka v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše výchozí implementaci třídy ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) `CMFCToolBarDateTimeCtrlImpl` aktualizací velikosti a umístění vnitřního objektu.

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
[v] Nadřazené okno.

*iButtonIndex*<br/>
[v] Index tlačítka na základě nuly v nadřazené kolekci tlačítek.

*soubor nástrojů wnd*<br/>
[v] Ovládací prvek, který zobrazuje text popisu.

*Str*<br/>
[out] Objekt, `CString` který obdrží aktualizovaný text popisu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud metoda aktualizuje text popisu; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) zobrazením textu popisku, který je přidružen k tlačítku. Pokud tlačítko není ukotveno vodorovně, tato metoda neprovede žádnou akci a vrátí hodnotu FALSE.

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime

Nastaví čas a datum v ovládacím prvku pro výběr času.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
[v] V první verzi odkaz na [COleDateTime class](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje čas, na který bude nastaven ovládací prvek. Ve druhé verzi ukazatel na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, na který bude nastaven ovládací prvek.

*pTimeNew*<br/>
[v] Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obsahuje čas, na který bude nastaven ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nastaví čas v ovládacím prvku pro výběr data a času voláním [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeall

Nastaví čas a datum ve všech instancích ovládacího prvku pro výběr času, které mají zadané ID příkazu.

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
[v] Určuje ID příkazu tlačítka panelu nástrojů.

*timeNew*<br/>
[v] V první verzi [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje čas, na který bude nastaven ovládací prvek. Ve druhé verzi ukazatel na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, na který bude nastaven ovládací prvek.

*pTimeNew*<br/>
[v] Ukazatel na [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) strukturu, která obsahuje čas, na který bude nastaven ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Vyhledá tlačítko panelu nástrojů se zadaným ID příkazu a nastaví čas v ovládacím prvku pro výběr data a času voláním [příkazu CMFCToolBarDateTimeCtrl::SetTime](#settime).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
