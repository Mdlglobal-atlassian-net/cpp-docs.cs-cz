---
title: Cmfcbutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/28/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
dev_langs:
- C++
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23b830ca8a7fb7f2e799cae17209a9fa089d1881
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690872"
---
# <a name="cmfcbutton-class"></a>Cmfcbutton – třída
`CMFCButton` Třídy přidá funkce, které [CButton](../../mfc/reference/cbutton-class.md) třídy, jako je například zarovnání textu tlačítka, kombinaci textu a obrázku, výběr kurzoru a zadání popisku tlačítka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCButton : public CButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|Výchozí konstruktor.|  
|`CMFCButton::~CMFCButton`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCButton::CleanUp](#cleanup)|Obnoví vnitřních proměnných a uvolní přidělené prostředky, jako jsou obrázky, rastrové obrázky a ikony.|  
|`CMFCButton::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|  
|`CMFCButton::DrawItem`|Volá se rozhraním, při úpravě vizuálního aspektu tlačítka nakresleného vlastníkem. (Přepíše [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Určuje, jestli se mají zobrazovat úplné znění popisek v okně velké popisu tlačítka nebo zkrácená verze textu v okně malé popisu.|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|Určuje, zda písmo textu tlačítka je stejný jako písma nabídky aplikace.|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Určuje, zda styl ohraničení tlačítka odpovídá aktuální motiv Windows.|  
|`CMFCButton::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Vrátí odkaz na základní ovládací prvek tooltip.|  
|[CMFCButton::IsAutoCheck](#isautocheck)|Označuje, zda zaškrtávací políčko nebo přepínací tlačítka automatického tlačítka.|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Určuje, zda tlačítko je nastavena na automatické opakování režim.|  
|[CMFCButton::IsCheckBox](#ischeckbox)|Určuje, zda tlačítko je tlačítko zaškrtávacího políčka.|  
|[CMFCButton::IsChecked](#ischecked)|Označuje, zda je zaškrtnuto tlačítko aktuální.|  
|[CMFCButton::IsHighlighted](#ishighlighted)|Určuje, zda se zvýrazní tlačítko.|  
|[CMFCButton::IsPressed](#ispressed)|Určuje, zda je posunuta a zvýrazní tlačítko.|  
|[CMFCButton::IsPushed](#ispushed)|Určuje, zda tlačítko je vloženo.|  
|[CMFCButton::IsRadioButton](#isradiobutton)|Určuje, zda tlačítko je tlačítko přepínače.|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Určuje, zda styl ohraničení tlačítka odpovídá aktuální motiv Windows.|  
|`CMFCButton::OnDrawParentBackground`|Nakreslí pozadí nadřazeného objektu tlačítka v určené oblasti. (Přepíše [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Nastaví tlačítko pro režim automatické opakování.|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Nastaví obrázek pro tlačítko zaškrtnuto.|  
|[CMFCButton::SetFaceColor](#setfacecolor)|Nastaví barvu pozadí textu tlačítka.|  
|[CMFCButton::SetImage](#setimage)|Nastaví obrázek pro tlačítko.|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|Nastaví obrázek kurzoru.|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Nastaví kurzor do bitové kopie na tvar ruky.|  
|[CMFCButton::SetStdImage](#setstdimage)|Používá `CMenuImages` objekt nastavení obrázku tlačítka.|  
|[CMFCButton::SetTextColor](#settextcolor)|Nastaví barvu textu tlačítka pro tlačítko, které není vybraná.|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Nastaví barvu textu tlačítka pro tlačítko, který je vybrán.|  
|[CMFCButton::SetTooltip](#settooltip)|Přidruží popisek tlačítka.|  
|[CMFCButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby obsahovala jeho textu a obrázků.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit tlačítko.|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|Volá se rozhraním, chcete-li nakreslit ohraničení tlačítka.|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Volá se rozhraním, chcete-li nakreslit obdélník pro tlačítko.|  
|[CMFCButton::OnDrawText](#ondrawtext)|Volá se rozhraním, chcete-li nakreslit text tlačítka.|  
|[CMFCButton::OnFillBackground](#onfillbackground)|Volá se rozhraním, chcete-li nakreslit na pozadí text tlačítka.|  
|[CMFCButton::SelectFont](#selectfont)|Načte písma, která souvisí s kontextem zadané zařízení.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Určuje zarovnání textu tlačítka.|  
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Určuje, jestli se má použít motivy Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Označuje, zda chcete-li nakreslit obdélník kolem tlačítka.| 
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Určuje styl tlačítka, jako je například bez okrajů, bez stromové struktury, středníkem ploché nebo 3D.|  
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|V případě hodnoty TRUE umožňuje zakázané tlačítko vykreslit jako šedě.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Označuje, zda zvýraznění BS_CHECKBOX – vizuální styl tlačítka, když se ukazatelem přejde nad ním.|  
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Označuje, zda reagovat na události tlačítka.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Určuje, jestli se má zobrazit obrázek na pravé straně tlačítka.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Označuje, zda bitová kopie je nad tlačítko.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Označuje, zda tlačítko je transparentní.|  
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Určuje, zda klikněte na poslední událost byla poklepání.|
  
## <a name="remarks"></a>Poznámky  
 Jiné typy tlačítek jsou odvozeny z `CMFCButton` třídy, jako [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) třídy, která podporuje hypertextové odkazy, a `CMFCColorButton` třídy, která podporuje dialogové okno Výběr barvy.  
  
 Styl `CMFCButton` objekt může být *3D*, *plochý*, *středníkem paušální* nebo *bez ohraničení*. Text tlačítka lze zarovnávat na levé straně, top nebo center tlačítka. V době běhu můžete určit, zda na tomto tlačítku zobrazí text, image, nebo textu a obrázku. Můžete také určit, že obrázek konkrétní kurzoru zobrazí, když se ukazatelem přejde na tlačítko.  
  
 Vytvoření ovládacího prvku tlačítko přímo v kódu nebo s použitím **Průvodce třídami MFC** nástroje a šablony dialogového okna. Pokud vytvoříte ovládací prvek tlačítko přímo, přidejte `CMFCButton` proměnnou pro svoji aplikaci a pak volání konstruktoru a `Create` metody `CMFCButton` objektu. Pokud používáte **Průvodce třídami MFC**, přidat `CButton` proměnné pro vaši aplikaci a poté změňte typ proměnné z `CButton` k `CMFCButton`.  
  
 Pro zpracování zpráv s oznámením v aplikaci pole dialogového okna přidáte položku mapování zpráv a obslužnou rutinu události pro každé upozornění. Oznámení zaslaná z `CMFCButton` se shodují s nastaveními odesílaných `CButton` objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup konfigurace vlastností tlačítka pomocí různých metod v `CMFCButton` třídy. V příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [Cmfcbutton –](../../mfc/reference/cmfcbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbutton.h  
  
##  <a name="cleanup"></a>  CMFCButton::CleanUp  
 Obnoví vnitřních proměnných a uvolní přidělené prostředky, jako jsou obrázky, rastrové obrázky a ikony.  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip  
 Určuje, jestli se mají zobrazovat úplné znění popisek v okně velké popisu tlačítka nebo zkrácená verze textu v okně malé popisu.  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Šťastnou*  
 TRUE, pokud chcete zobrazit všechny textu. FALSE pro zobrazení zkrácen textu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont  
 Určuje, zda písmo textu tlačítka je stejný jako písma nabídky aplikace.  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Šťastnou*  
 TRUE, pokud chcete použít písmo nabídky aplikace jako písmo textu tlačítka; FALSE, pokud chcete použít systémové písmo. Výchozí hodnota je TRUE.  
  
 [in] *bRedraw*  
 TRUE, pokud chcete okamžitě ho překreslit obrazovce. v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Pokud použijete tuto metodu k určení písmo textu tlačítka, můžete zadat písma s [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) metody. Pokud nezadáte písmo vůbec, rozhraní nastaví výchozí písmo.  
  
##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming  
 Určuje, zda styl ohraničení tlačítka odpovídá aktuální motiv Windows.  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bEnable*  
 TRUE, pokud chcete použít aktuální motiv Windows k vykreslení ohraničení tlačítka; FALSE, pokud chcete používat motiv Windows. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ovlivní všechna tlačítka ve vaší aplikaci, která jsou odvozena z `CMFCButton` třídy.  
  
##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl  
 Vrátí odkaz na základní ovládací prvek tooltip.  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na základní ovládací prvek tooltip.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck  
 Označuje, zda zaškrtávací políčko nebo přepínací tlačítka automatického tlačítka.  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je styl tlačítka BS_AUTOCHECKBOX nebo BS_AUTORADIOBUTTON; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode  
 Určuje, zda tlačítko je nastavena na automatické opakování režim.  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tlačítko je nastavena na automatické opakování režimu. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCButton::SetAutorepeatMode](#setautorepeatmode) metody nastavte tlačítko pro režim automatické opakování.  
  
##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox  
 Určuje, zda tlačítko je tlačítko zaškrtávacího políčka.  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud má tlačítko BS_CHECKBOX nebo BS_AUTOCHECKBOX styl; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ischecked"></a>  CMFCButton::IsChecked  
 Označuje, zda je zaškrtnuto tlačítko aktuální.  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je zaškrtnuto tlačítko aktuální; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá k označení, že jsou zaškrtnuté různé druhy tlačítka různými způsoby. Například přepínač proběhne, pokud obsahuje tečku; zaškrtávací políčko je zaškrtnuté políčko, pokud obsahuje **X**.  
  
##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted  
 Určuje, zda se zvýrazní tlačítko.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je zvýrazněný na tlačítko. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Zvýrazní tlačítko po umístění ukazatele myši nad tlačítkem.  
  
##  <a name="ispressed"></a>  CMFCButton::IsPressed  
 Určuje, zda je posunuta a zvýrazní tlačítko.  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud se stiskne tlačítko; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ispushed"></a>  CMFCButton::IsPushed  
 Určuje, zda tlačítko je vloženo.  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je vloženo tlačítka; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton  
 Určuje, zda tlačítko je tlačítko přepínače.  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je styl tlačítka BS_RADIOBUTTON nebo BS_AUTORADIOBUTTON; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled  
 Určuje, zda styl ohraničení tlačítka odpovídá aktuální motiv Windows.  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud odpovídá aktuální motiv Windows; styl ohraničení tlačítka v opačném případě hodnota FALSE.  



## <a name="a-namembdontusewinxptheme-cmfcbuttonmbdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton::m_bDontUseWinXPTheme
Určuje, jestli se má při vykreslování na tlačítko použít motivy Windows XP.

```  
BOOL m_bDontUseWinXPTheme;  
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus  
 Označuje, zda chcete-li nakreslit obdélník kolem tlačítka.  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bDrawFocus` členský určíte, že bude rozhraní nakreslit obdélník kolem textu tlačítka a obrázků, je-li na tlačítko získá fokus na hodnotu TRUE.  
  
 `CMFCButton` Konstruktor inicializuje tohoto člena na hodnotu TRUE.  

##  <a name="m_bGrayDisabled"></a>  CMFCButton::m_bGrayDisabled
V případě hodnoty TRUE umožňuje zakázané tlačítko vykreslit jako šedě.


```  
BOOL m_bGrayDisabled;  
```

##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked  
 Označuje, zda zvýraznění BS_CHECKBOX – vizuální styl tlačítka, když se ukazatelem přejde nad ním.  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bHighlightChecked` člena na hodnotu TRUE, chcete-li určit, že rozhraní framework vyzdvihne BS_CHECKBOX – vizuální styl tlačítka po umístění ukazatele myši nad ním.  

##  <a name="m_bResponseOnButtonDown"></a> CMFCButton::m_bResponseOnButtonDown
Označuje, zda reagovat na události tlačítka.

```  
BOOL m_bResponseOnButtonDown;  
```  

##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage  
 Určuje, jestli se má zobrazit obrázek na pravé straně tlačítka.  
  
```  
BOOL m_bRightImage;  
```  


##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)
Označuje, zda bitová kopie je nad tlačítko.

```  
BOOL m_bTopImage;  
```

### <a name="remarks"></a>Poznámky  
 Nastavte `m_bRightImage` člena na hodnotu TRUE, chcete-li určit, že rozhraní se zobrazí obrázek na tlačítko napravo od popisku tlačítka.  
  
##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent  
 Označuje, zda tlačítko je transparentní.  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bTransparent` člena na hodnotu TRUE, chcete-li určit, že rozhraní budou tlačítko transparentní. `CMFCButton` Konstruktor inicializuje tohoto člena na hodnotu FALSE.  
  
##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle  
 Určuje zarovnání textu tlačítka.  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 Použijte jednu z následujících `CMFCButton::AlignStyle` hodnot výčtu k určení zarovnání textu tlačítka:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|ALIGN_CENTER|(Výchozí) Zarovná text tlačítka na střed tlačítka.|  
|ALIGN_LEFT|Zarovná text tlačítka na levé straně tlačítka.|  
|ALIGN_RIGHT|Zarovná text tlačítka na pravé straně tlačítka.|  
  
 `CMFCButton` Konstruktor inicializuje tento člen pro ALIGN_CENTER.  

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk) | 
Určuje, zda klikněte na poslední událost byla poklepání. |

```  
BOOL m_bWasDblClk;  
```  

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle  
 Určuje styl tlačítka, jako je například bez okrajů, bez stromové struktury, středníkem ploché nebo 3D.  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulce jsou uvedeny `CMFCButton::m_nFlatStyle` hodnot výčtu, které určují vzhled tlačítka.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|(Výchozí) Zdá se, že tlačítko má vysokou, trojrozměrného strany. Při kliknutí na tlačítko na tlačítko se zobrazí na zavedeny do hloubkové odsazení.|  
|BUTTONSTYLE_FLAT|Při pozastavení nad tlačítko myši, na tlačítko se zdá být dvourozměrné a není nutné vyvolanou strany. Při pozastavení ukazatele myši nad tlačítkem, tlačítko mít nízká, trojrozměrného strany. Při kliknutí na tlačítko na tlačítko se zobrazí na zavedeny do bez podstruktury odsazení.|  
|BUTTONSTYLE_SEMIFLAT|Zdá se, že tlačítko má nízká, trojrozměrného strany. Při kliknutí na tlačítko na tlačítko se zobrazí na zavedeny do hloubkové odsazení.|  
|BUTTONSTYLE_NOBORDERS|Tlačítko není vyvolal strany a vždy zobrazuje dvojrozměrné. Tlačítko zřejmě není zavedeny do odsazení, když dojde ke kliknutí na.|  
  
 `CMFCButton` Konstruktor inicializuje tento člen pro BUTTONSTYLE_3D.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit hodnoty `m_nFlatStyle` členské proměnné v `CMFCButton` třídy. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>  CMFCButton::OnDraw  
 Volá se rozhraním, chcete-li nakreslit tlačítko.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *rect*  
 Odkaz na obdélník, který za rozsahem tlačítka.  
  
 [in] *uiState*  
 Aktuální stav tlačítka. Další informace najdete v tématu `itemState` člena [drawitemstruct – struktura](../../mfc/reference/drawitemstruct-structure.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Přepsáním této metody můžete použít vlastní kód chcete-li nakreslit tlačítko.  
  
##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder  
 Volá se rozhraním, chcete-li nakreslit ohraničení tlačítka.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *rectClient*  
 Odkaz na obdélník, který za rozsahem tlačítka.  
  
 [in] *uiState*  
 Aktuální stav tlačítka. Další informace najdete v tématu `itemState` člena [drawitemstruct – struktura](../../mfc/reference/drawitemstruct-structure.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem použití vlastního kódu k vykreslení ohraničení.  
  
##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect  
 Volá se rozhraním, chcete-li nakreslit obdélník pro tlačítko.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *rectClient*  
 Odkaz na obdélník, který za rozsahem tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Přepsáním této metody můžete použít vlastní kód chcete-li nakreslit obdélník.  
  
##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText  
 Volá se rozhraním, chcete-li nakreslit text tlačítka.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *rect*  
 Odkaz na obdélník, který za rozsahem tlačítka.  
  
 [in] *strText*  
 Text, chcete-li nakreslit.  
  
 [in] *uiDTFlags*  
 Příznaky, které určují, jak formátovat text. Další informace najdete v tématu *nFormat* parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metody.  
  
 [in] *uiState*  
 (Vyhrazeno).  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem vykreslení textu tlačítka pomocí vlastního kódu.  
  
##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground  
 Volá se rozhraním, chcete-li nakreslit na pozadí text tlačítka.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *rectClient*  
 Odkaz na obdélník, který za rozsahem tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem vykreslení na pozadí tlačítka pomocí vlastního kódu.  
  
##  <a name="selectfont"></a>  CMFCButton::SelectFont  
 Načte písma, která souvisí s kontextem zadané zařízení.  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Přepsáním této metody můžete použít vlastní kód k načtení písmo.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode  
 Nastaví tlačítko pro režim automatické opakování.  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nTimeDelay*  
 Nezáporné číslo, které udává interval mezi zprávy odeslané do nadřazeného okna. Interval se měří v milisekundách a jeho výchozí hodnota je 500 milisekund. Určete nula zakázat režim automatické opakování zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda způsobí, že tlačítko neustále odeslat wm_command – zprávy do nadřazeného okna, dokud se neuvolní tlačítko, nebo *nTimeDelay* parametr je nastaven na hodnotu nula.  
  
##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage  
 Nastaví obrázek pro tlačítko zaškrtnuto.  
  
```  
void SetCheckedImage(
    HICON hIcon,  
    BOOL bAutoDestroy=TRUE,  
    HICON hIconHot=NULL,  
    HICON hIconDisabled=NULL,  
    BOOL bAlphaBlend=FALSE);

 
void SetCheckedImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy=TRUE,  
    HBITMAP hBitmapHot=NULL,  
    BOOL bMap3dColors=TRUE,  
    HBITMAP hBitmapDisabled=NULL);

 
void SetCheckedImage(
    UINT uiBmpResId,  
    UINT uiBmpHotResId=0,  
    UINT uiBmpDsblResID=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hIcon*  
 Zpracování na ikonu, která obsahuje rastrového obrázku a maska pro nové image.  
  
 [in] *bAutoDestroy*  
 TRUE, pokud chcete určit, že prostředky rastrový obrázek zničí automaticky. v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.  
  
 [in] *hIconHot*  
 Zpracování na ikonu, která obsahuje bitovou kopii pro vybraný stav.  
  
 [in] *hBitmap*  
 Popisovač rastrový obrázek, který obsahuje bitovou kopii pro – vybraný stav.  
  
 [in] *hBitmapHot*  
 Popisovač rastrový obrázek, který obsahuje bitovou kopii pro vybraný stav.  
  
 [in] *bMap3dColors*  
 Určuje průhlednou barvu pozadí tlačítka; To znamená, rozpoznávání tváře tlačítka. TRUE, pokud chcete použít hodnota barvy RGB (192, 192, 192); FALSE, pokud chcete použít hodnota barvy určené `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] *uiBmpResId*  
 ID prostředku bitové kopie není vybraná.  
  
 [in] *uiBmpHotResId*  
 ID prostředku pro vybrané bitové kopie.  
  
 [in] *hIconDisabled*  
 Zpracování na ikonu pro zakázané bitovou kopii.  
  
 [in] *hBitmapDisabled*  
 Popisovač rastrový obrázek, který obsahuje bitovou kopii zakázané.  
  
 [in] *uiBmpDsblResID*  
 ID prostředku rastrového obrázku zakázané.  
  
 [in] *bAlphaBlend*  
 True použijte pouze 32bitové obrázky, které používají alfa kanál; FALSE, nechcete použít obrázky pouze alfa kanálu. Výchozí hodnota je FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor  
 Nastaví barvu pozadí textu tlačítka.  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *crFace*  
 Hodnota barvy RGB.  
  
 [in] *bRedraw*  
 TRUE, pokud chcete okamžitě; překreslení obrazovky v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete definovat novou barvu výplně pozadí tlačítka (pro rozpoznávání tváře). Všimněte si, že na pozadí není vyplněné, kdy [CMFCButton::m_bTransparent](#m_btransparent) členské proměnné je hodnota TRUE.  
  
##  <a name="setimage"></a>  CMFCButton::SetImage  
 Nastaví obrázek pro tlačítko.  
  
```  
void SetImage(
    HICON hIcon,  
    BOOL bAutoDestroy=TRUE,  
    HICON hIconHot=NULL,  
    HICON hIconDisabled=NULL,  
    BOOL bAlphaBlend=FALSE);

 
void SetImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy=TRUE,  
    HBITMAP hBitmapHot=NULL,  
    BOOL bMap3dColors=TRUE,  
    HBITMAP hBitmapDisabled=NULL);

 
void SetImage(
    UINT uiBmpResId,  
    UINT uiBmpHotResId=0,  
    UINT uiBmpDsblResID=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hIcon*  
 Zpracování na ikonu, která obsahuje rastrového obrázku a maska pro nové image.  
  
 [in] *bAutoDestroy*  
 TRUE, pokud chcete určit, že prostředky rastrový obrázek zničí automaticky. v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.  
  
 [in] *hIconHot*  
 Zpracování na ikonu, která obsahuje bitovou kopii pro vybraný stav.  
  
 [in] *hBitmap*  
 Popisovač rastrový obrázek, který obsahuje bitovou kopii pro – vybraný stav.  
  
 [in] *hBitmapHot*  
 Popisovač rastrový obrázek, který obsahuje bitovou kopii pro vybraný stav.  
  
 [in] *uiBmpResId*  
 ID prostředku bitové kopie není vybraná.  
  
 [in] *uiBmpHotResId*  
 ID prostředku pro vybrané bitové kopie.  
  
 [in] *bMap3dColors*  
 Určuje průhlednou barvu pozadí tlačítka; To znamená, rozpoznávání tváře tlačítka. TRUE, pokud chcete použít hodnota barvy RGB (192, 192, 192); FALSE, pokud chcete použít hodnota barvy určené `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] *hIconDisabled*  
 Zpracování na ikonu pro zakázané bitovou kopii.  
  
 [in] *hBitmapDisabled*  
 Popisovač rastrový obrázek, který obsahuje bitovou kopii zakázané.  
  
 [in] *uiBmpDsblResID*  
 ID prostředku rastrového obrázku zakázané.  
  
 [in] *bAlphaBlend*  
 True použijte pouze 32bitové obrázky, které používají alfa kanál; FALSE, nechcete použít obrázky pouze alfa kanálu. Výchozí hodnota je FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat různé verze `SetImage` metodu `CMFCButton` třídy. V příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor  
 Nastaví obrázek kurzoru.  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hcursor*  
 Popisovač kurzoru.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete přidružit obrázek kurzoru, jako je například kurzor ručně pomocí tlačítka. Kurzor je načtené z prostředků aplikace.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `SetMouseCursor` metodu `CMFCButton` třídy. V příkladu je část kódu v [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand  
 Nastaví kurzor do bitové kopie na tvar ruky.  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete přidružit obrázek kurzoru na tvar ruky tlačítka. Kurzor je načtené z prostředků aplikace.  
  
##  <a name="setstdimage"></a>  CMFCButton::SetStdImage  
 Používá `CMenuImages` objekt nastavení obrázku tlačítka.  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *id*  
 Jeden z identifikátorů image tlačítko, které jsou definovány v `CMenuImage::IMAGES_IDS` výčtu. Obrázek hodnoty určují, Image, jako je například šipky, kódy PIN a přepínače.  
  
 [in] *stavu*  
 Jeden z identifikátorů stav obrázku tlačítka, definovaných v `CMenuImages::IMAGE_STATE` výčtu. Stavy image zadejte barvy tlačítka, jako je například bílé a tmavě šedé Černá, gray, světle šedá. Výchozí hodnota je `CMenuImages::ImageBlack`.  
  
 [in] *idDisabled*  
 Jeden z identifikátorů image tlačítko, které jsou definovány v `CMenuImage::IMAGES_IDS` výčtu. Na obrázku označuje, že je tlačítko neaktivní. Výchozí hodnota je první obrázek tlačítka ( `CMenuImages::IdArrowDown`).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settextcolor"></a>  CMFCButton::SetTextColor  
 Nastaví barvu textu tlačítka pro tlačítko, které není vybraná.  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *clrText*  
 Hodnota barvy RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor  
 Nastaví barvu textu tlačítka pro tlačítko, který je vybrán.  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *clrTextHot*  
 Hodnota barvy RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settooltip"></a>  CMFCButton::SetTooltip  
 Přidruží popisek tlačítka.  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszToolTipText*  
 Ukazatel na text pro popis. Zadejte hodnotu NULL, chcete-li zakázat popisek.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent  
 Změní velikost tlačítka tak, aby obsahovala jeho textu a obrázků.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bCalcOnly*  
 TRUE, pokud chcete vypočítat, ale nikoli změnit, nová velikost tlačítka; FALSE, pokud chcete změnit velikost tlačítka. Výchozí hodnota je FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt, který obsahuje novou velikost tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vypočítá novou velikost, která obsahuje vodorovný okraj 10 pixelů a vertikální okraji 5 pixelů.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfclinkctrl – třída](../../mfc/reference/cmfclinkctrl-class.md)   
 [Cmfccolorbutton – třída](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton – třída](../../mfc/reference/cmfcmenubutton-class.md)
