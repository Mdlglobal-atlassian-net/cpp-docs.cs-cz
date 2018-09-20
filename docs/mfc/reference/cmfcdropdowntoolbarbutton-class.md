---
title: Cmfcdropdowntoolbarbutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 157bcb8b1b8341e16d7dcb6c3a9d9fc9dc1a4d4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431736"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Cmfcdropdowntoolbarbutton – třída

Typ tlačítka panelu nástrojů, který se při kliknutí chová jako běžné tlačítko. Otevře však rozevírací seznam nástrojů ( [CMFCDropDownToolbar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md) Pokud uživatel stiskne a podrží tlačítko panelu nástrojů.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Vytvoří `CMFCDropDownToolbarButton` objektu.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Zkopíruje aktuální tlačítko Vlastnosti jiné tlačítko panelu nástrojů. (Přepíše [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otevře se panel nástrojů rozevíracího seznamu.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Zkopíruje text tlačítka na panelu nástrojů do nabídky. (Přepíše [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Načte rozevírací seznam nástrojů, který je přidružený k tlačítku.|
|`CMFCDropDownToolbarButton::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Určuje, zda je momentálně otevřený rozevírací seznam nástrojů.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Určuje, zda tlačítko lze zobrazit pomocí rozšířených ohraničení. (Přepíše [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Volá se rozhraním pro výpočet velikosti tlačítko pro zadané zařízení kontext a stav dokování. (Přepíše [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Volá se rozhraním pro zpracování [WM_CANCELMODE](/windows/desktop/winmsg/wm-cancelmode) zprávy. (Přepíše `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním při vložení do nového panelu nástrojů na tlačítko. (Přepíše [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Volá se rozhraním, když uživatel klikne na tlačítko myši. (Přepíše [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Volá se rozhraním, když uživatel uvolní tlačítko myši. (Přepíše [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Volá se rozhraním, když zpracovává zprávu WM_HELPHITTEST nadřazeného panelu nástrojů. (Přepíše [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Upraví zadaný nabídky při aplikace zobrazí místní nabídka na panelu nástrojů nadřazené. (Přepíše [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit tlačítko s použitím zadaného styly a možnosti. (Přepíše [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Volá se rozhraním, chcete-li nakreslit tlačítko **příkazy** podokně **vlastní** dialogové okno. (Přepíše [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Čte tento objekt z archivu nebo zapíše do archivu. (Přepíše [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Nastaví výchozí příkaz, který rozhraní používá, když uživatel klikne na tlačítko.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Určuje dobu, která uživatel musí podržte tlačítko myši předtím, než se zobrazí rozevírací seznam nástrojů.|

## <a name="remarks"></a>Poznámky

A `CMFCDropDownToolBarButton` se liší od běžné tlačítko v tom, že má malou šipku v pravém horním rohu na tlačítko. Když uživatele vybere tlačítko na panelu nástrojů v rozevíracím seznamu, zobrazí rozhraní jeho ikonu na panelu nástrojů nejvyšší úrovně (tlačítko s malou šipku v pravém dolním rohu).

Informace o tom, jak implementovat rozevírací seznam nástrojů, naleznete v tématu [CMFCDropDownToolbar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md).

`CMFCDropDownToolBarButton` Objekt je možné exportovat do [cmfctoolbarmenubutton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md) objektu a zobrazen jako tlačítko nabídky pomocí místní nabídky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton –](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfcdropdowntoolbarbutton –](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

Zkopíruje aktuální tlačítko Vlastnosti jiné tlačítko panelu nástrojů.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Odkaz na tlačítko zdroj ze kterého chcete kopírovat.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem kopírování jiné tlačítko panelu nástrojů do tohoto tlačítka panelu nástrojů. *src* musí být typu `CMFCDropDownToolbarButton`.

##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Vytvoří `CMFCDropDownToolbarButton` objektu.

```
CMFCDropDownToolbarButton();


CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Výchozí text na tlačítku.

*pToolBar*<br/>
[in] Ukazatel `CMFCDropDownToolBar` objekt, který se zobrazí, když uživatel stiskne tlačítko.

### <a name="remarks"></a>Poznámky

Druhé přetížení konstruktoru zkopíruje k tlačítku rozevíracího seznamu na první tlačítko na panelu nástrojů, které *pToolBar* určuje.

Obvykle tlačítka panelu nástrojů v rozevíracím seznamu použije text z naposledy použitých tlačítka na panelu nástrojů, které *pToolBar* určuje. Používá textem určeným parametrem *lpszName* když tlačítko je převedena na tlačítko nabídky nebo se zobrazí v **příkazy** karty **vlastní** dialogové okno. Další informace o **vlastní** dialogovém okně naleznete v tématu [cmfctoolbarscustomizedialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCDropDownToolbarButton` třídy. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

Otevře se panel nástrojů rozevíracího seznamu.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Nadřazené okno rámce rozevíracího seznamu nebo hodnota NULL pro použití nadřazené okno panelu nástrojů v rozevíracím seznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

[CMFCDropDownToolbarButton::OnClick](#onclick) metoda volá tuto metodu za účelem otevřete rozevírací seznam nástrojů, když uživatel stiskne a podrží tlačítko panelu nástrojů.

Tyto metody vytvoří rozevírací seznam nástrojů pomocí [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) metody. Pokud nadřazeného panelu nástrojů je ukotven svisle, tato metoda se umístí panelu rozevíracího seznamu buď na levém nebo pravém okraji nadřazeného panelu nástrojů v závislosti na přizpůsobit. Jinak tato metoda umístí panelu rozevíracího seznamu pod nadřazeného panelu nástrojů.

Tato metoda selže, pokud *pWnd* má hodnotu NULL a nadřazené okno nemá žádné tlačítko panelu nástrojů v rozevíracím seznamu.

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

Zkopíruje text tlačítka na panelu nástrojů do nabídky.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*Tlačítko nabídky*<br/>
[in] Odkaz na tlačítko nabídky Cíl.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud metoda uspěje; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda volá implementaci základní třídy ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) a potom připojí k cílové tlačítko nabídky rozbalovací nabídky, které obsahuje každou položku nabídky panelu nástrojů v toto tlačítko. Tato metoda nepřipojuje podnabídek rozbalovací nabídky.

Tato metoda selže, pokud nadřazeného panelu nástrojů `m_pToolBar`, má hodnotu NULL nebo implementaci základní třídy vrací hodnotu FALSE.

##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar

Načte rozevírací seznam nástrojů, který je přidružený k tlačítku.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Návratová hodnota

Rozevírací seznam nástrojů, který je přidružený k tlačítku.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí `m_pToolBar` datový člen.

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

Určuje, zda je momentálně otevřený rozevírací seznam nástrojů.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud rozevírací seznam nástrojů je aktuálně otevřená. jinak 0.

### <a name="remarks"></a>Poznámky

Rozhraní se otevře rozevírací seznam nástrojů pomocí [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metody. Rozhraní framework zavře rozevírací seznam nástrojů, když uživatel stiskne tlačítko vlevo myši v neklientské oblasti panelu rozevíracího seznamu.

##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize

Určuje, zda tlačítko lze zobrazit pomocí rozšířených ohraničení.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko panelu nástrojů můžete zobrazit pomocí rozšířených hranici. jinak 0.

### <a name="remarks"></a>Poznámky

Další informace o rozšířených ohraničení, naleznete v tématu [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay

Určuje dobu, která uživatel musí podržte tlačítko myši předtím, než se zobrazí rozevírací seznam nástrojů.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Poznámky

Doba zpoždění se měří v milisekundách. Výchozí hodnota je 500. Můžete změnit hodnotu tohoto člena sdílených dat můžete nastavit jinou zpoždění.

##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize

Volá se rozhraním pro výpočet velikosti tlačítko pro zadané zařízení kontext a stav dokování.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Kontext zařízení, která se zobrazí tlačítko.

*sizeDefault*<br/>
[in] Výchozí velikost tlačítka.

*bHorz*<br/>
[in] Ukotvit stav nadřazeného panelu nástrojů. Tento parametr je hodnotu TRUE, pokud je ukotven vodorovně panelu nástrojů nebo plovoucí nebo hodnotu NEPRAVDA, pokud se ukotví svisle.

### <a name="return-value"></a>Návratová hodnota

A `SIZE` strukturu, která obsahuje dimenze na tlačítko v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) tak, že přidáte šířku na šipku rozevíracího seznamu na vodorovný rozměr velikost tlačítka.

##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd

Volá se rozhraním při vložení do nového panelu nástrojů na tlačítko.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Nové nadřazené okno.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje implementaci základní třídy ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) tím, že zrušíte textový popisek ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) a nastavení [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) a [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) datové členy na hodnotu FALSE.

##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick

Volá se rozhraním, když uživatel klikne na tlačítko myši.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Nadřazené okno panelu nástrojů.

*bDelay*<br/>
[in] TRUE, pokud zpráva by měla zpracovává se zpožděním.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud na tlačítko zpracovává zprávy klikněte na tlačítko. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), stačí aktualizovat stav panelu nástrojů v rozevíracím seznamu.

Když uživatel klikne na tlačítko panelu nástrojů, tato metoda vytvoří časovač, který čeká délka časový limit určený parametrem [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) datový člen a pak se otevře rozevírací nabídky panelu nástrojů pomocí [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metody. Tato metoda zavře panel rozevíracího seznamu podruhé uživatel klikne na tlačítko panelu nástrojů.

##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp

Volá se rozhraním, když uživatel uvolní tlačítko myši.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud na tlačítko zpracovává zprávy klikněte na tlačítko. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), stačí aktualizovat stav panelu nástrojů v rozevíracím seznamu.

Tato metoda zastaví časovač rozevírací seznam nástrojů, pokud je aktivní. Uzavírá rozevírací seznam nástrojů, pokud je otevřený.

Další informace o panelu nástrojů rozevíracího seznamu a rozevírací seznam nástrojů časovače, naleznete v tématu [CMFCDropDownToolbarButton::OnClick](#onclick).

##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp

Volá se rozhraním, když zpracovává zprávu WM_HELPHITTEST nadřazeného panelu nástrojů.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Nadřazené okno panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zpracovává zprávy nápovědy. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) voláním [CMFCDropDownToolbarButton::OnClick](#onclick) metodu s *bDelay*nastavena na hodnotu FALSE. Tato metoda vrátí hodnotu, která je vrácena [CMFCDropDownToolbarButton::OnClick](#onclick).

Další informace o zprávě WM_HELPHITTEST najdete v tématu [TN028: podpora pomůže Context-Sensitive](../../mfc/tn028-context-sensitive-help-support.md).

##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu

Upraví zadaný nabídky při aplikace zobrazí místní nabídka na panelu nástrojů nadřazené.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[in] V nabídce Upravit.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) tím, že zakážete následující položky:

- **Kopírovat obrázek tlačítka**

- **Vzhled tlačítka**

- **Obrázek**

- **Text**

- **Obrázek a Text**

Přepsáním této metody můžete upravit nabídku, která zobrazí rozhraní v režimu úprav.

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

Volá se rozhraním, chcete-li nakreslit tlačítko s použitím zadaného styly a možnosti.

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

*primární řadič domény*<br/>
[in] Kontext zařízení, která se zobrazí tlačítko.

*Rect*<br/>
[in] Ohraničující obdélník na tlačítko.

*pImages*<br/>
[in] Kolekce obrázků panelu nástrojů, který je přidružený k tlačítku.

*bHorz*<br/>
[in] Ukotvit stav nadřazeného panelu nástrojů. Tento parametr je PRAVDA, pokud je ukotven tlačítka vodorovně a FALSE-li na tlačítko je ukotven svisle.

*bCustomizeMode*<br/>
[in] Určuje, zda je panel nástrojů v režimu úprav. Tento parametr má hodnotu TRUE, pokud panelu nástrojů je v režimu úprav a hodnotu FALSE, pokud panel nástrojů není v režimu úprav.

*bHighlight*<br/>
[in] Určuje, zda se zvýrazní tlačítko. Tento parametr je hodnotu PRAVDA, pokud se zvýrazní tlačítko a hodnotu FALSE, pokud není zvýrazní tlačítko.

*bDrawBorder*<br/>
[in] Určuje, zda tlačítko zobrazí jeho ohraničení. Tento parametr je hodnota TRUE, pokud tlačítko zobrazeno jeho okraj a hodnotu FALSE při tlačítko by neměl zobrazit jeho ohraničení.

*bGrayDisabledButtons*<br/>
[in] Určuje, jestli se má stín tlačítka Zakázané nebo použít kolekci zakázané imagí. Tento parametr je hodnota TRUE, pokud zakázané tlačítka by měl být označeno šedou barvou a hodnotu FALSE, když tato metoda by měla použít kolekci zakázané imagí.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu za účelem přizpůsobení panelu nástrojů tlačítko Kreslení.

##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Volá se rozhraním, chcete-li nakreslit tlačítko **příkazy** podokně **vlastní** dialogové okno.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Kontext zařízení, která se zobrazí tlačítko.

*Rect*<br/>
[in] Ohraničující obdélník na tlačítko.

*bSelected*<br/>
[in] Určuje, zda výběru tlačítka. Pokud tento parametr má hodnotu TRUE, výběru tlačítka. Pokud má parametr hodnotu FALSE, tlačítko není vybrané.

### <a name="return-value"></a>Návratová hodnota

Šířka v pixelech, tlačítka v kontextu zadané zařízení.

### <a name="remarks"></a>Poznámky

Tato metoda je volána v dialogovém okně přizpůsobení ( **příkazy** kartu) když tlačítko je vyžadována k zobrazení sám na pole se seznamem vykreslené vlastníkem.

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) tak, že změníte textový popisek tlačítka na název tlačítka (to znamená na hodnotu *lpszName* parametr, který je předán konstruktoru).

##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize

Čte tento objekt z archivu nebo zapíše do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[in] `CArchive` Objektu, ze které nebo která k serializaci.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje implementaci základní třídy ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) pomocí serializace ID prostředku nadřazeného panelu nástrojů. Při načítání archivu ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) vrací nenulovou hodnotu), tato metoda nastaví `m_pToolBar` datový člen na panelu nástrojů, který obsahuje ID serializovaných prostředku.

##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand

Nastaví výchozí příkaz, který rozhraní používá, když uživatel klikne na tlačítko.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] ID příkazu výchozí.

### <a name="remarks"></a>Poznámky

Voláním této metody lze zadat výchozí příkaz, který rozhraní provede, když uživatel klikne na tlačítko. Položku s Identifikátorem příkazu určené *uiCmd* se musí nacházet v rozevíracím seznamu nadřazeného panelu nástrojů.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



