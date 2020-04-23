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
ms.openlocfilehash: f09a2f3fe66abb86a8f220dbdf6744813ad9db0d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752402"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton – třída

Typ tlačítka panelu nástrojů, který se při klepnutí chová jako běžné tlačítko. Otevře však rozevírací panel nástrojů ( [CMFCDropDownToolBar Class,](../../mfc/reference/cmfcdropdowntoolbar-class.md) pokud uživatel stiskne a podrží tlačítko panelu nástrojů dolů.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Vytvoří `CMFCDropDownToolbarButton` objekt.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko. (Přepíše [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otevře rozevírací panel nástrojů.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Zkopíruje text z tlačítka panelu nástrojů do nabídky. (Přepíše [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Načte rozevírací panel nástrojů, který je přidružen k tlačítku.|
|`CMFCDropDownToolbarButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Určuje, zda je rozbalovací panel nástrojů aktuálně otevřený.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Určuje, zda lze tlačítko zobrazit s rozšířeným ohraničením. (Přepíše [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Volat rámci vypočítat velikost tlačítka pro zadaný kontext zařízení a dokovací stav. (Přepíše [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Volat rámci pro zpracování [WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) zprávy. (Přepíše `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Volat rámci při vložení tlačítka do nového panelu nástrojů. (Přepíše [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::Při klepnutí](#onclick)|Volat rámci po kliknutí uživatele na tlačítko myši. (Přepíše [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Volat rámci při uživatel uvolní tlačítko myši. (Přepíše [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Volat rámci při nadřazený panel nástrojů zpracovává WM_HELPHITTEST zprávu. (Přepíše [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::Nabídka OnCustomizeMenu](#oncustomizemenu)|Změní zadaný menu, když aplikace zobrazí místní nabídku na nadřazeném panelu nástrojů. (Přepíše [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Volat rámci nakreslit tlačítko pomocí zadaných stylů a možností. (Přepíše [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Volat rámci nakreslit tlačítko v podokně **příkazy** dialogového okna **Přizpůsobit.** (Přepíše [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serializovat](#serialize)|Přečte tento objekt z archivu nebo jej zapíše do archivu. (Přepíše [CMFCToolBarButton::Serializovat](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Nastaví výchozí příkaz, který rozhraní používá, když uživatel klepne na tlačítko.|

### <a name="data-members"></a>Členové dat

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Určuje dobu, po kterou musí uživatel podržet tlačítko myši, než se zobrazí rozevírací panel nástrojů.|

## <a name="remarks"></a>Poznámky

A `CMFCDropDownToolBarButton` se liší od běžného tlačítka v tom, že má malou šipku v pravém dolním rohu tlačítka. Poté, co uživatel vybere tlačítko z rozevíracího panelu nástrojů, zobrazí rozhraní svou ikonu na tlačítku panelu nástrojů nejvyšší úrovně (tlačítko s malou šipkou v pravém dolním rohu).

Informace o implementaci rozevíracího panelu nástrojů naleznete v [tématu CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md).

Objekt `CMFCDropDownToolBarButton` lze exportovat do objektu [třídy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) a zobrazit jako tlačítko nabídky s rozbalovací nabídkou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CmFCDropDownTlačítko panelu nástrojů](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom

Zkopíruje vlastnosti jiného tlačítka panelu nástrojů na aktuální tlačítko.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Odkaz na zdrojové tlačítko, ze kterého chcete kopírovat.

### <a name="remarks"></a>Poznámky

Volánítéto metody zkopírovat jiné tlačítko panelu nástrojů na toto tlačítko panelu nástrojů. *src* musí být `CMFCDropDownToolbarButton`typu .

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Vytvoří `CMFCDropDownToolbarButton` objekt.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
[v] Výchozí text tlačítka.

*panel nástrojů pToolBar*<br/>
[v] Ukazatel na `CMFCDropDownToolBar` objekt, který se zobrazí, když uživatel stiskne tlačítko.

### <a name="remarks"></a>Poznámky

Druhé přetížení konstruktoru zkopíruje na rozevírací tlačítko první tlačítko z panelu nástrojů, který určuje *pToolBar.*

Tlačítko rozevíracího panelu nástrojů obvykle používá text z naposledy použitého tlačítka na panelu nástrojů, který určuje *panel nástrojů.* Používá text určený *lpszName,* když je tlačítko převedeno na tlačítko nabídky nebo se zobrazí na kartě **Příkazy** dialogového okna **Přizpůsobit.** Další informace o dialogovém **okně Přizpůsobit** naleznete v tématu [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCDropDownToolbarButton` třídy. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar

Otevře rozevírací panel nástrojů.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Nadřazené okno rozevíracího rámečku nebo NULL pro použití nadřazeného okna rozevíracího panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Metoda [CMFCDropDownToolbarButton::OnClick](#onclick) volá tuto metodu k otevření rozevíracího panelu nástrojů, když uživatel stiskne a podrží tlačítko panelu nástrojů.

Tato metoda vytvoří rozevírací panel nástrojů pomocí metody [CMFCDropDownFrame::Create.](../../mfc/reference/cmfcdropdownframe-class.md#create) Pokud je nadřazený panel nástrojů ukotven svisle, umístí tato metoda rozevírací panel nástrojů na levou nebo pravou stranu nadřazeného panelu nástrojů v závislosti na přizpůsobení. V opačném případě tato metoda umístí rozevírací panel nástrojů pod nadřazený panel nástrojů.

Tato metoda se nezdaří, pokud *pWnd* je NULL a rozbalovací panel nástrojů tlačítko nemá nadřazené okno.

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Zkopíruje text z tlačítka panelu nástrojů do nabídky.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
[v] Odkaz na tlačítko cílové nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda volá implementaci základní třídy ( [CMFCToolBarButton::ExportToMenuButton)](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)a potom připojí k tlačítku cílové nabídky rozbalovací nabídku, která obsahuje každou položku nabídky panelu nástrojů v tomto tlačítku. Tato metoda nepřipojí dílčí nabídky do rozbalovací nabídky.

Tato metoda se nezdaří, `m_pToolBar`pokud nadřazený panel nástrojů , je NULL nebo implementace základní třídy vrátí hodnotu NEPRAVDA.

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Načte rozevírací panel nástrojů, který je přidružen k tlačítku.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Návratová hodnota

Rozevírací panel nástrojů přidružený k tlačítku.

### <a name="remarks"></a>Poznámky

Tato metoda `m_pToolBar` vrátí datový člen.

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

Určuje, zda je rozbalovací panel nástrojů aktuálně otevřený.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je rozbalovací panel nástrojů aktuálně otevřený; jinak 0.

### <a name="remarks"></a>Poznámky

Rozhraní Framework otevře rozevírací panel nástrojů pomocí metody [CMFCDropDownToolbarButton::DropDownToolbar.](#dropdowntoolbar) Rozhraní framework zavře rozevírací panel nástrojů, když uživatel stiskne levé tlačítko myši v oblasti nástrojů, které nejsou klientem.

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

Určuje, zda lze tlačítko zobrazit s rozšířeným ohraničením.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze tlačítko panelu nástrojů zobrazit s prodlouženým ohraničením; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace o rozšířených ohraničeních naleznete v tématu [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Určuje dobu, po kterou musí uživatel podržet tlačítko myši, než se zobrazí rozevírací panel nástrojů.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Poznámky

Doba zpoždění se měří v milisekundách. Výchozí hodnota je 500. Další zpoždění můžete nastavit změnou hodnoty tohoto sdíleného datového člena.

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Volat rámci vypočítat velikost tlačítka pro zadaný kontext zařízení a dokovací stav.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který zobrazí tlačítko.

*sizeDefault*<br/>
[v] Výchozí velikost tlačítka.

*bHorz*<br/>
[v] Stav ukotvení nadřazeného panelu nástrojů. Tento parametr je TRUE, pokud je panel nástrojů ukotven vodorovně nebo plovoucí, nebo NEPRAVDA, pokud je panel nástrojů ukotven svisle.

### <a name="return-value"></a>Návratová hodnota

Struktura, `SIZE` která obsahuje rozměry tlačítka v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) přidáním šířky šipky rozevíracího seznamu do vodorovné dimenze velikosti tlačítka.

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Volat rámci při vložení tlačítka do nového panelu nástrojů.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše implementaci základní třídy ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) vymazáním textového popisku ( [CMFCToolBarButton::m_strText)](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)a nastavením [CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) a [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) datových členů na FALSE.

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFCDropDownToolbarButton::Při klepnutí

Volat rámci po kliknutí uživatele na tlačítko myši.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Nadřazené okno tlačítka panelu nástrojů.

*bZpoždění*<br/>
[v] TRUE, pokud by zpráva měla být zpracována se zpožděním.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zpracuje zprávu o kliknutí; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), aktualizací stavu rozevíracího panelu nástrojů.

Když uživatel klepne na tlačítko panelu nástrojů, tato metoda vytvoří časovač, který čeká na dobu určenou datovým členem [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) a potom otevře rozevírací panel nástrojů pomocí metody [CMFCDropDownToolbarButton::DropDownToolbar.](#dropdowntoolbar) Tato metoda zavře rozevírací panel nástrojů podruhé, kdy uživatel klepne na tlačítko panelu nástrojů.

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Volat rámci při uživatel uvolní tlačítko myši.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zpracuje zprávu o kliknutí; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), aktualizací stavu rozevíracího panelu nástrojů.

Tato metoda zastaví časovač rozevíracího panelu nástrojů, pokud je aktivní. Zavře rozevírací panel nástrojů, pokud je otevřený.

Další informace o rozevíracím panelu nástrojů a časovači rozevíracího panelu nástrojů naleznete v tématu [CMFCDropDownToolbarButton::OnClick](#onclick).

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Volat rámci při nadřazený panel nástrojů zpracovává WM_HELPHITTEST zprávu.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Nadřazené okno tlačítka panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zpracuje zprávu nápovědy; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) voláním metody [CMFCDropDownToolbarButton::OnClick](#onclick) s *parametrem bDelay* nastaveným na hodnotu FALSE. Tato metoda vrátí hodnotu, která je vrácena [CMFCDropDownToolbarButton::OnClick](#onclick).

Další informace o zprávě WM_HELPHITTEST naleznete v [tématu TN028: Kontextová podpora nápovědy](../../mfc/tn028-context-sensitive-help-support.md).

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::Nabídka OnCustomizeMenu

Změní zadaný menu, když aplikace zobrazí místní nabídku na nadřazeném panelu nástrojů.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

*pNabídka*<br/>
[v] Nabídka přizpůsobit.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) zakázáním následujících položek nabídky:

- **Obrázek tlačítka Kopírovat**

- **Vzhled tlačítka**

- **Image**

- **Text**

- **Obrázek a text**

Přepište tuto metodu a upravte místní nabídku, která se zobrazí v režimu přizpůsobení.

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw

Volat rámci nakreslit tlačítko pomocí zadaných stylů a možností.

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

*Pdc*<br/>
[v] Kontext zařízení, který zobrazí tlačítko.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka.

*pObrázky*<br/>
[v] Kolekce obrázků panelu nástrojů, která je přidružena k tlačítku.

*bHorz*<br/>
[v] Stav ukotvení nadřazeného panelu nástrojů. Tento parametr je true, pokud je tlačítko ukotveno vodorovně a NEPRAVDA, když je tlačítko ukotveno svisle.

*bPřizpůsobitrežim*<br/>
[v] Určuje, zda je panel nástrojů v režimu přizpůsobení. Tento parametr je true, pokud je panel nástrojů v režimu přizpůsobení a NEPRAVDA, pokud panel nástrojů není v režimu přizpůsobení.

*bZvýraznění*<br/>
[v] Určuje, zda je tlačítko zvýrazněno. Tento parametr je true, pokud je tlačítko zvýrazněno, a NEPRAVDA, pokud tlačítko není zvýrazněno.

*bDrawBorder*<br/>
[v] Určuje, zda má tlačítko zobrazovat jeho ohraničení. Tento parametr je true, když tlačítko by mělo zobrazit jeho ohraničení a FALSE, když tlačítko by nemělo zobrazit jeho ohraničení.

*bGrayDisabledTlačítka*<br/>
[v] Určuje, zda mají být zastíněna zakázaná tlačítka nebo zda se má použít kolekce zakázaných obrazů. Tento parametr je true, pokud by měla být zakázána tlačítka stínovaná a NEPRAVDA, pokud by tato metoda měla používat kolekci zakázaných obrázků.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a přizpůsobte výkres tlačítka panelu nástrojů.

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Volat rámci nakreslit tlačítko v podokně **příkazy** dialogového okna **Přizpůsobit.**

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který zobrazí tlačítko.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka.

*bVybrané*<br/>
[v] Určuje, zda je tlačítko vybráno. Pokud je tento parametr TRUE, je vybráno tlačítko. Pokud je tento parametr FALSE, tlačítko není vybráno.

### <a name="return-value"></a>Návratová hodnota

Šířka tlačítka v obrazových bodech v zadaném kontextu zařízení.

### <a name="remarks"></a>Poznámky

Tato metoda je volána dialogovém oknem přizpůsobení (karta **Příkazy),** když je nutné tlačítko, aby se zobrazilo v seznamu vlastník-draw.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) změnou popisku textu tlačítka na název tlačítka (to znamená na hodnotu parametru *lpszName,* který jste předali konstruktoru).

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFCDropDownToolbarButton::Serializovat

Přečte tento objekt z archivu nebo jej zapíše do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[v] Objekt, `CArchive` ze kterého nebo do kterého serializovat.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) serializováním ID prostředku nadřazeného panelu nástrojů. Když se archiv načítá ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) vrátí nenulovou hodnotu), tato metoda nastaví `m_pToolBar` datový člen na panel nástrojů, který obsahuje Serializované ID prostředku.

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Nastaví výchozí příkaz, který rozhraní používá, když uživatel klepne na tlačítko.

```cpp
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID výchozího příkazu.

### <a name="remarks"></a>Poznámky

Volání této metody k určení výchozí ho příkazu, který provede rozhraní, když uživatel klepne na tlačítko. Položka s ID příkazu určené *uiCmd* musí být umístěna v nadřazeném panelu nástrojů rozevíracího souboru.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Třída CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
