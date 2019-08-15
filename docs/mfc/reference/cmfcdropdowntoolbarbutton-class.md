---
title: CMFCDropDownToolbarButton – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505319"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton – třída

Typ tlačítka panelu nástrojů, které se chová jako běžné tlačítko při kliknutí. Pokud se ale uživatel stiskne a drží tlačítko na panelu nástrojů, otevře panel nástrojů rozevíracího seznamu ( [Třída CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) ).

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|`CMFCDropDownToolbarButton` Vytvoří objekt.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko. (Overrides [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otevře rozevírací panel nástrojů.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Kopíruje text z tlačítka panelu nástrojů do nabídky. (Overrides [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Načte rozevírací panel nástrojů, který je přidružený k tlačítku.|
|`CMFCDropDownToolbarButton::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Určuje, zda je rozevírací panel nástrojů aktuálně otevřen.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Určuje, zda lze tlačítko Zobrazit s rozšířeným ohraničením. (Overrides [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Volá se rozhraním, aby se počítala velikost tlačítka pro zadaný kontext zařízení a stav docking. (Overrides [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Volá se rozhraním, aby se zpracovala zpráva [WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) . (Overrides `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko. (Overrides [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Volá se rozhraním, když uživatel klikne na tlačítko myši. (Potlačení [CMFCToolBarButton:: Click](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Volá se rozhraním, když uživatel uvolní tlačítko myši. (Overrides [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Volá se rozhraním, když nadřazený panel nástrojů zpracovává zprávu WM_HELPHITTEST. (Overrides [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Upraví zadanou nabídku, když aplikace zobrazí místní nabídku na nadřazeném panelu nástrojů. (Overrides [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Volá se rozhraním, aby se vykreslilo tlačítko pomocí zadaných stylů a možností. (Overrides [CMFCToolBarButton:: nakreslit](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Volá se rozhraním, aby se nakreslilo tlačítko v podokně **příkazy** dialogového okna **přizpůsobit** . (Overrides [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton:: serializovat](#serialize)|Přečte tento objekt z archivu nebo ho zapíše do archivu. (Overrides [CMFCToolBarButton:: serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Nastaví výchozí příkaz, který rozhraní používá, když uživatel klikne na tlačítko.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Určuje dobu, po kterou musí uživatel držet tlačítko myši před tím, než se zobrazí rozevírací panel nástrojů.|

## <a name="remarks"></a>Poznámky

Se `CMFCDropDownToolBarButton` liší od obyčejného tlačítka v tom, že má malou šipku v pravém dolním rohu tlačítka. Jakmile uživatel vybere tlačítko z rozevíracího seznamu, rozhraní zobrazí jeho ikonu na tlačítku panelu nástrojů nejvyšší úrovně (tlačítko s malou šipkou v pravém dolním rohu).

Informace o implementaci rozevíracího panelu nástrojů naleznete v tématu [Třída CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md).

Objekt lze exportovat do objektu [třídy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) a zobrazit jako tlačítko nabídky s místní nabídkou. `CMFCDropDownToolBarButton`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar. h

##  <a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom

Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
pro Odkaz na zdrojové tlačítko, ze kterého se má kopírovat.

### <a name="remarks"></a>Poznámky

Voláním této metody zkopírujte další tlačítko panelu nástrojů na toto tlačítko panelu nástrojů. *Src* musí být typu `CMFCDropDownToolbarButton`.

##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

`CMFCDropDownToolbarButton` Vytvoří objekt.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
pro Výchozí text tlačítka

*pToolBar*<br/>
pro Ukazatel na `CMFCDropDownToolBar` objekt, který se zobrazí, když uživatel stiskne tlačítko.

### <a name="remarks"></a>Poznámky

Druhé přetížení konstruktoru zkopíruje na tlačítko rozevírací nabídky první tlačítko z panelu nástrojů, který *pToolBar* určuje.

Rozevírací tlačítko na panelu nástrojů obvykle používá text z tlačítka naposledy použité na panelu nástrojů, který *pToolBar* určuje. Používá text určený parametrem *lpszName* , pokud je tlačítko převedeno na tlačítko nabídky nebo se zobrazuje na kartě **příkazy** dialogového okna **přizpůsobit** . Další informace o dialogovém okně **přizpůsobit** naleznete v tématu [Třída CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCDropDownToolbarButton` třídy. Tento fragment kódu je součástí ukázkového [vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::D ropDownToolbar

Otevře rozevírací panel nástrojů.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Nadřazené okno rozevíracího seznamu nebo hodnota NULL pro použití nadřazeného okna rozevíracího seznamu tlačítka na panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Metoda [CMFCDropDownToolbarButton:: Click](#onclick) volá tuto metodu pro otevření rozevíracího seznamu nástrojů, když uživatel stiskne a drží tlačítko panelu nástrojů.

Tyto metody vytvoří rozevírací seznam nástrojů pomocí metody [CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create) . Pokud je nadřazený panel nástrojů ukotvený svisle, tato metoda umístí rozevírací seznam nástrojů na levou nebo pravou stranu panelu nástrojů nadřazených panelů, v závislosti na tom, jak se hodí. V opačném případě tato metoda umístí rozevírací nabídku pod nadřazený panel nástrojů.

Tato metoda se nezdařila, pokud má *pWnd* hodnotu null a rozevírací tlačítko na panelu nástrojů nemá nadřazené okno.

##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Kopíruje text z tlačítka panelu nástrojů do nabídky.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
pro Odkaz na tlačítko cílové nabídky

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda volá implementaci základní třídy ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) a potom připojí k tlačítku cílové nabídky místní nabídku, která obsahuje každou položku nabídky panelu nástrojů na tomto tlačítku. Tato metoda nepřipojí podnabídky do místní nabídky.

Tato metoda se nezdařila, pokud `m_pToolBar`je nadřazený panel nástrojů,, je null nebo implementace základní třídy vrátí hodnotu false.

##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Načte rozevírací panel nástrojů, který je přidružený k tlačítku.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Návratová hodnota

Rozevírací panel nástrojů, který je spojen s tlačítkem.

### <a name="remarks"></a>Poznámky

Tato metoda vrací `m_pToolBar` datový člen.

##  <a name="isdropdown"></a>CMFCDropDownToolbarButton:: DropDown – rozevírací seznam

Určuje, zda je rozevírací panel nástrojů aktuálně otevřen.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je rozevírací panel nástrojů momentálně otevřený; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rozhraní otevře rozevírací panel nástrojů pomocí metody [CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar) . Rozhraní zavře rozevírací panel nástrojů, když uživatel stiskne tlačítko myši v oblasti mimo klienta rozevíracího seznamu nástrojů.

##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

Určuje, zda lze tlačítko Zobrazit s rozšířeným ohraničením.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud lze tlačítko panelu nástrojů zobrazit s rozšířeným ohraničením; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace o rozšířených ohraničeních naleznete v tématu [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Určuje dobu, po kterou musí uživatel držet tlačítko myši před tím, než se zobrazí rozevírací panel nástrojů.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Poznámky

Doba zpoždění se měří v milisekundách. Výchozí hodnota je 500. Další zpoždění můžete nastavit změnou hodnoty tohoto sdíleného datového člena.

##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Volá se rozhraním, aby se počítala velikost tlačítka pro zadaný kontext zařízení a stav docking.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazí tlačítko.

*sizeDefault*<br/>
pro Výchozí velikost tlačítka

*bHorz*<br/>
pro Stav Dock ovládacího prvku ToolBar Tento parametr má hodnotu TRUE, pokud je panel nástrojů ukotven vodorovně nebo je plovoucí, nebo FALSE, pokud je panel nástrojů ukotvený svisle.

### <a name="return-value"></a>Návratová hodnota

`SIZE` Struktura obsahující rozměry tlačítka v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) přidáním šířky šipky rozevíracího seznamu na vodorovnou dimenzi velikosti tlačítka.

##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) smazáním textového popisku ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) a nastavením [CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) a [CMFCToolBarButton :: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) datových členů na hodnotu false.

##  <a name="onclick"></a>CMFCDropDownToolbarButton:: Click

Volá se rozhraním, když uživatel klikne na tlačítko myši.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Nadřazené okno tlačítka panelu nástrojů

*bDelay*<br/>
pro Hodnota TRUE, pokud má být zpráva zpracována zpožděním

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zpracovává zprávu kliknutí; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, [CMFCToolBarButton:: Click](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), aktualizací stavu rozevíracího seznamu nástrojů.

Když uživatel klikne na tlačítko panelu nástrojů, tato metoda vytvoří časovač, který počká na dobu určenou datovým členem [CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay) a pak otevře rozevírací seznam pomocí [CMFCDropDownToolbarButton. ::D metoda ropDownToolbar](#dropdowntoolbar) . Tato metoda zavře rozevírací panel nástrojů podruhé, když uživatel klikne na tlačítko panelu nástrojů.

##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Volá se rozhraním, když uživatel uvolní tlačítko myši.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zpracovává zprávu kliknutí; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy, [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), aktualizací stavu rozevíracího seznamu nástrojů.

Tato metoda zastaví časovač rozevíracího seznamu, pokud je aktivní. Zavře rozevírací panel nástrojů, pokud je otevřený.

Další informace o rozevíracím panelu nástrojů a o časovači panelu nástrojů naleznete v tématu [CMFCDropDownToolbarButton:: Click](#onclick).

##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Volá se rozhraním, když nadřazený panel nástrojů zpracovává zprávu WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Nadřazené okno tlačítka panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zpracovává zprávu o nápovědě; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) voláním metody [CMFCDropDownToolbarButton:: Click](#onclick) s *BDELAY* nastavenou na hodnotu false. Tato metoda vrací hodnotu vrácenou funkcí [CMFCDropDownToolbarButton:: Click](#onclick).

Další informace o zprávě WM_HELPHITTEST naleznete v tématu [TN028: Podpora](../../mfc/tn028-context-sensitive-help-support.md)kontextové pomoci.

##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

Upraví zadanou nabídku, když aplikace zobrazí místní nabídku na nadřazeném panelu nástrojů.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
pro Nabídka, která se má přizpůsobit

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) tím, že zakáže následující položky nabídky:

- **Kopírovat obrázek tlačítka**

- **Vzhled tlačítka**

- **Obrázek**

- **Text**

- **Obrázek a text**

Tuto metodu přepište pro úpravu místní nabídky, kterou rozhraní zobrazuje v režimu přizpůsobení.

##  <a name="ondraw"></a>CMFCDropDownToolbarButton:: Draw

Volá se rozhraním, aby se vykreslilo tlačítko pomocí zadaných stylů a možností.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazí tlačítko.

*OBD*<br/>
pro Ohraničující obdélník tlačítka

*pImages*<br/>
pro Kolekce obrázků panelů nástrojů, které jsou přidruženy k tlačítku.

*bHorz*<br/>
pro Stav Dock ovládacího prvku ToolBar Tento parametr má hodnotu TRUE, pokud je tlačítko ukotveno vodorovně a hodnotu FALSE, pokud je tlačítko ukotveno svisle.

*bCustomizeMode*<br/>
pro Určuje, zda je panel nástrojů v režimu přizpůsobení. Tento parametr má hodnotu TRUE, pokud je panel nástrojů v režimu přizpůsobení a hodnota FALSE v případě, že panel nástrojů není v režimu přizpůsobení.

*bHighlight*<br/>
pro Určuje, zda je tlačítko zvýrazněno. Tento parametr má hodnotu TRUE, pokud je tlačítko zvýrazněno a FALSE, pokud tlačítko není zvýrazněno.

*bDrawBorder*<br/>
pro Určuje, zda má tlačítko zobrazit jeho ohraničení. Tento parametr má hodnotu TRUE, pokud má tlačítko zobrazit jeho ohraničení a hodnotu FALSE, pokud by tlačítko neměl zobrazit jeho ohraničení.

*bGrayDisabledButtons*<br/>
pro Určuje, zda se mají zakázaná tlačítka odstínovat nebo použít kolekci zakázaných imagí. Tento parametr má hodnotu TRUE, pokud mají být zakázaná tlačítka šedá a FALSE, pokud by tato metoda měla používat kolekci zakázaných imagí.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete přizpůsobit vykreslování tlačítek panelu nástrojů.

##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Volá se rozhraním, aby se nakreslilo tlačítko v podokně **příkazy** dialogového okna **přizpůsobit** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazí tlačítko.

*OBD*<br/>
pro Ohraničující obdélník tlačítka

*bSelected*<br/>
pro Určuje, zda je toto tlačítko vybráno. Je-li tento parametr nastaven na hodnotu TRUE, je tlačítko vybráno. Pokud je tento parametr FALSE, tlačítko není vybráno.

### <a name="return-value"></a>Návratová hodnota

Šířka tlačítka na zadaném kontextu zařízení (v pixelech).

### <a name="remarks"></a>Poznámky

Tato metoda je volána dialogem přizpůsobení (karta **příkazy** ), pokud je tlačítko požadováno k zobrazení sebe v seznamu vykresleného vlastníkem.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) tak, že se změní textový popisek tlačítka na název tlačítka (tj. na hodnotu parametru *lpszName* , který jste předali do konstruktoru. ).

##  <a name="serialize"></a>CMFCDropDownToolbarButton:: serializovat

Přečte tento objekt z archivu nebo ho zapíše do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*snížen*<br/>
pro `CArchive` Objekt, ze kterého se má serializovat.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton:: serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) pomocí serializace ID prostředku nadřazeného panelu nástrojů. Při načítání archivu ( [CArchive:: Overloads](../../mfc/reference/carchive-class.md#isloading) vrátí nenulovou hodnotu) Tato metoda nastaví `m_pToolBar` datový člen na panel nástrojů, který obsahuje ID serializovaného prostředku.

##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Nastaví výchozí příkaz, který rozhraní používá, když uživatel klikne na tlačítko.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID výchozího příkazu

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro určení výchozího příkazu, který se spustí, když uživatel klikne na tlačítko. Položka s ID příkazu, která je určená parametrem *uiCmd* , musí být umístěná v rozevíracím seznamu nadřazených panelů.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
