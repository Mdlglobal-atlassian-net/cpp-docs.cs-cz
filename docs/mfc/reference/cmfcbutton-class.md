---
title: "Třída CMFCButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d496cf079cd56d8260c5fd8072809bc05559ef2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcbutton-class"></a>CMFCButton – třída
`CMFCButton` Třída přidává funkce [CButton](../../mfc/reference/cbutton-class.md) třída například zarovnání text tlačítka, kombinace text tlačítka a bitovou kopii, vyberete kurzoru a zadat popis tlačítka.  
  
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
|[CMFCButton::CleanUp](#cleanup)|Obnoví interní proměnné a uvolní přidělené prostředky, např. obrázky, rastrové obrázky a ikony.|  
|`CMFCButton::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCButton::DrawItem`|Voláno rámcem, pokud došlo ke změně visual aspekt tlačítka vykreslované uživatelem. (Přepisuje [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Určuje, jestli chcete zobrazit úplný text popisu tlačítka v okně velké popisu nebo zkrácený verzi text v okně malé popisu.|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|Určuje, jestli písmo pro text tlačítka je stejný jako písmo nabídce aplikace.|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Určuje, zda styl ohraničení tlačítko odpovídá aktuální motiv systému Windows.|  
|`CMFCButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Vrátí odkaz na základní ovládacího prvku popisek.|  
|[CMFCButton::IsAutoCheck](#isautocheck)|Určuje, zda zaškrtávací políčko nebo přepínač Automatické tlačítko.|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Označuje, zda je tlačítko nastavit do režimu automatické opakování.|  
|[CMFCButton::IsCheckBox](#ischeckbox)|Určuje, zda je tlačítko tlačítka zaškrtávací políčko.|  
|[CMFCButton::IsChecked](#ischecked)|Určuje, zda je aktuální tlačítko zaškrtnuto.|  
|[CMFCButton::IsHighlighted](#ishighlighted)|Určuje, zda je označený tlačítko.|  
|[CMFCButton::IsPressed](#ispressed)|Určuje, jestli je tlačítko Poslat a zvýrazní.|  
|[CMFCButton::IsPushed](#ispushed)|Určuje, zda je tlačítko Poslat.|  
|[CMFCButton::IsRadioButton](#isradiobutton)|Označuje, zda je tlačítko přepínače.|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Určuje, zda styl ohraničení tlačítko odpovídá aktuální motiv systému Windows.|  
|`CMFCButton::OnDrawParentBackground`|Kreslení na pozadí tlačítko nadřazené v určené oblasti. (Přepisuje [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Nastaví tlačítka režimu automatické opakování.|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Nastaví obrázek pro tlačítko zaškrtnuté.|  
|[CMFCButton::SetFaceColor](#setfacecolor)|Nastaví barvu pozadí pro text tlačítka.|  
|[CMFCButton::SetImage](#setimage)|Nastaví obrázek pro tlačítko.|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|Nastavuje obrázek, kurzoru.|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Nastaví kurzor na bitovou kopii dlaně.|  
|[CMFCButton::SetStdImage](#setstdimage)|Používá `CMenuImages` objekt, který chcete nastavit obrázek tlačítka.|  
|[CMFCButton::SetTextColor](#settextcolor)|Nastaví barvu textu tlačítka pro tlačítko, které není vybraná.|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Nastaví barvu textu tlačítka pro tlačítko, který je vybraný.|  
|[CMFCButton::SetTooltip](#settooltip)|Přidruží popisek tlačítka.|  
|[CMFCButton::SizeToContent](#sizetocontent)|Změní velikost tlačítko obsahovat jeho text tlačítka a bitové kopie.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|Voláno rámcem k vykreslení tlačítko.|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|Voláno rámcem k vykreslení ohraničení tlačítko.|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Voláno rámcem k vykreslení rámečku fokusu pro tlačítko.|  
|[CMFCButton::OnDrawText](#ondrawtext)|Voláno rámcem k vykreslení text tlačítka.|  
|[CMFCButton::OnFillBackground](#onfillbackground)|Voláno rámcem k vykreslení pozadí textu tlačítka.|  
|[CMFCButton::SelectFont](#selectfont)|Načte písma, který je přidružený kontext zadané zařízení.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Označuje, zda se k vykreslení rámečku fokusu kolem tlačítko.|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Označuje, zda chcete zvýraznit stylu bs_checkbox – tlačítko při ukazatel myši nad ním.|  
|[CMFCButton::m_bRightImage](#m_brightimage)|Označuje, zda zobrazíte bitovou kopii na pravé straně tlačítko.|  
|[CMFCButton::m_bTransparent](#m_btransparent)|Určuje, zda je tlačítko transparentní.|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Určuje zarovnání textu tlačítka.|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Určuje styl tlačítka, jako je například bez okrajů, ploché, oddělte dvojrozměrném nebo 3D.|  
  
## <a name="remarks"></a>Poznámky  
 Jiné typy tlačítka jsou odvozeny od `CMFCButton` třídy, jako [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) třídy, která podporuje hypertextové odkazy, a `CMFCColorButton` třídy, která podporuje dialogové okno pro výběr barev.  
  
 Styl `CMFCButton` objekt může být *3D*, *ploché*, *zadáte dvojrozměrném* nebo *žádné ohraničení*. Text tlačítka lze zarovnávat na levé straně, top a uprostřed tlačítko. V době běhu můžete řídit, jestli na tlačítko zobrazí text, obrázky, nebo text a bitovou kopii. Můžete také určit, že obrázek konkrétní kurzoru zobrazit při ukazatel myši nad tlačítko.  
  
 Vytvoření ovládacího prvku tlačítko přímo v kódu nebo pomocí **Průvodce třídou MFC** nástroje a šablony pole dialogového okna. Pokud vytvoříte ovládacího prvku tlačítko přímo, přidejte `CMFCButton` proměnnou vaší aplikace a pak volání konstruktoru a `Create` metody `CMFCButton` objektu. Pokud použijete **Průvodce třídou MFC**, přidejte `CButton` proměnné k vaší aplikaci a poté změňte typ proměnné z `CButton` k `CMFCButton`.  
  
 Zpracování zpráv s oznámením v dialogovém okně aplikaci pole, přidejte položku mapování zpráv a obslužné rutiny události pro jednotlivá oznámení. Oznámení zaslaná z `CMFCButton` objekt jsou stejné jako poslal `CButton` objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak konfigurovat vlastnosti tlačítko pomocí různých metod v `CMFCButton` třídy. V příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbutton.h  
  
##  <a name="cleanup"></a>CMFCButton::CleanUp  
 Obnoví interní proměnné a uvolní přidělené prostředky, např. obrázky, rastrové obrázky a ikony.  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip  
 Určuje, jestli chcete zobrazit úplný text popisu tlačítka v okně velké popisu nebo zkrácený verzi text v okně malé popisu.  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bOn`  
 `TRUE`Chcete-li zobrazit celý text; `FALSE` na text zobrazení zkrácen.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont  
 Určuje, jestli písmo pro text tlačítka je stejný jako písmo nabídce aplikace.  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bOn`  
 `TRUE`Písmo nabídky aplikace používat jako písmo textu tlačítka; `FALSE` používat systém písmo. Výchozí hodnota je `TRUE`.  
  
 [v]`bRedraw`  
 `TRUE`okamžitě ho překreslit obrazovce; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud použijete tuto metodu určit písmo textu tlačítka, můžete zadat písma s [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) metoda. Pokud jste písmo nezadávejte vůbec, rozhraní nastaví výchozí písmo.  
  
##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming  
 Určuje, zda styl ohraničení tlačítko odpovídá aktuální motiv systému Windows.  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`aktuální motiv systému Windows použít k vykreslení ohraničení tlačítko; `FALSE` nechcete použít motiv systému Windows. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ovlivňuje všechny tlačítka v aplikaci, které jsou odvozeny od `CMFCButton` třídy.  
  
##  <a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl  
 Vrátí odkaz na základní ovládacího prvku popisek.  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na základní ovládacího prvku popisek.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck  
 Určuje, zda zaškrtávací políčko nebo přepínač Automatické tlačítko.  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud má tlačítko Styl bs_autocheckbox – nebo bs_autoradiobutton –; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode  
 Označuje, zda je tlačítko nastavit do režimu automatické opakování.  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tlačítko je nastavena na automatické opakování režim; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCButton::SetAutorepeatMode](#setautorepeatmode) metodu a nastavit tlačítko do režimu automatické opakování.  
  
##  <a name="ischeckbox"></a>CMFCButton::IsCheckBox  
 Určuje, zda je tlačítko tlačítka zaškrtávací políčko.  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je tlačítko bs_checkbox – nebo bs_autocheckbox – styl; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ischecked"></a>CMFCButton::IsChecked  
 Určuje, zda je aktuální tlačítko zaškrtnuto.  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je aktuální tlačítko označeno; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá různé způsoby, jak určit, zda jsou zrušena zaškrtnutí různé druhy tlačítka. Například je kontrolován přepínače, když obsahuje tečku; zaškrtávací políčko je zaškrtnuto, pokud obsahuje **X**.  
  
##  <a name="ishighlighted"></a>CMFCButton::IsHighlighted  
 Určuje, zda je označený tlačítko.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je tlačítko označený; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tlačítko se změní na zvýrazněné, když ukazatel myši nachází na tlačítko.  
  
##  <a name="ispressed"></a>CMFCButton::IsPressed  
 Určuje, jestli je tlačítko Poslat a zvýrazní.  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud stisknutí tlačítka; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ispushed"></a>CMFCButton::IsPushed  
 Určuje, zda je tlačítko Poslat.  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je tlačítko Poslat; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isradiobutton"></a>CMFCButton::IsRadioButton  
 Označuje, zda je tlačítko přepínače.  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je styl tlačítko bs_radiobutton – nebo bs_autoradiobutton –; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled  
 Určuje, zda styl ohraničení tlačítko odpovídá aktuální motiv systému Windows.  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud styl ohraničení tlačítko odpovídá aktuální motiv systému Windows. v opačném `FALSE`.  
  
##  <a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus  
 Označuje, zda se k vykreslení rámečku fokusu kolem tlačítko.  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bDrawFocus` člena `TRUE` k určení, že rozhraní bude kreslení rámečku fokusu kolem textu tlačítka a bitové kopie, pokud se tlačítko aktivuje.  
  
 `CMFCButton` Konstruktor inicializuje tohoto člena `TRUE`.  
  
##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked  
 Označuje, zda chcete zvýraznit stylu bs_checkbox – tlačítko při ukazatel myši nad ním.  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bHighlightChecked` člena `TRUE` k určení, zda bude rozhraní při ponechán ukazatel myši nad ním zvýrazněte stylu bs_checkbox – tlačítko.  
  
##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage  
 Označuje, zda zobrazíte bitovou kopii na pravé straně tlačítko.  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bRightImage` člena `TRUE` k určení, že rozhraní zobrazí obrázek na tlačítko vpravo od textu popisku tlačítka.  
  
##  <a name="m_btransparent"></a>CMFCButton::m_bTransparent  
 Určuje, zda je tlačítko transparentní.  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte `m_bTransparent` člena `TRUE` k určení, které rozhraní provede tlačítko transparentní. `CMFCButton` Konstruktor inicializuje tohoto člena `FALSE`.  
  
##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle  
 Určuje zarovnání textu tlačítka.  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 Použijte jednu z následujících `CMFCButton::AlignStyle` hodnot výčtu k určení zarovnání textu tlačítka:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|ALIGN_CENTER|(Výchozí) Zarovná text tlačítka k centru tlačítko.|  
|ALIGN_LEFT|Zarovná text tlačítka na levé straně na tlačítko.|  
|ALIGN_RIGHT|Zarovná text tlačítka na pravé straně tlačítko.|  
  
 `CMFCButton` Konstruktor inicializuje ALIGN_CENTER tohoto člena.  
  
##  <a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle  
 Určuje styl tlačítka, jako je například bez okrajů, ploché, oddělte dvojrozměrném nebo 3D.  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí `CMFCButton::m_nFlatStyle` hodnot výčtu, které určují vzhled tlačítka.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|(Výchozí) Tlačítko zřejmě vysoké, trojrozměrné stranách. Při kliknutí na tlačítko tlačítko je pravděpodobně být stisknutí do hloubkové odsazení.|  
|BUTTONSTYLE_FLAT|Když myši není přes tlačítko Pozastavit, na tlačítko se zdá být dvourozměrná a nemá vyvolané stranách. Při přesunutí myši pozastavení přes tlačítko, se zobrazí tlačítko do mají nízké, trojrozměrné stran. Při kliknutí na tlačítko se zobrazí tlačítko na stisknout do bez podstruktury odsazení.|  
|BUTTONSTYLE_SEMIFLAT|Tlačítko zřejmě nízkou, trojrozměrné stranách. Při kliknutí na tlačítko tlačítko je pravděpodobně být stisknutí do hloubkové odsazení.|  
|BUTTONSTYLE_NOBORDERS|Tlačítko mít není vyvolána stranách a vždy se zobrazí dvourozměrná. Tlačítko se nezobrazí na stisknutí do odsazení, po klepnutí.|  
  
 `CMFCButton` Konstruktor inicializuje tohoto člena `BUTTONSTYLE_3D`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit hodnoty `m_nFlatStyle` členské proměnné v `CMFCButton` třídy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>CMFCButton::OnDraw  
 Voláno rámcem k vykreslení tlačítko.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rect`  
 Odkaz na obdélníku bounds tlačítko.  
  
 [v]`uiState`  
 Aktuální stav tlačítko. Další informace najdete v tématu `itemState` členem [drawitemstruct – struktura](../../mfc/reference/drawitemstruct-structure.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro kreslení tlačítko pomocí vlastní kód.  
  
##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder  
 Voláno rámcem k vykreslení ohraničení tlačítko.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectClient`  
 Odkaz na obdélníku bounds tlačítko.  
  
 [v]`uiState`  
 Aktuální stav tlačítko. Další informace najdete v tématu `itemState` členem [drawitemstruct – struktura](../../mfc/reference/drawitemstruct-structure.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu použít vlastní kód k vykreslení ohraničení.  
  
##  <a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect  
 Voláno rámcem k vykreslení rámečku fokusu pro tlačítko.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectClient`  
 Odkaz na obdélníku bounds tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro kreslení rámečku fokusu pomocí vlastní kód.  
  
##  <a name="ondrawtext"></a>CMFCButton::OnDrawText  
 Voláno rámcem k vykreslení text tlačítka.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rect`  
 Odkaz na obdélníku bounds tlačítko.  
  
 [v]`strText`  
 Text k vykreslení.  
  
 [v]`uiDTFlags`  
 Příznaky, které určují způsob formátování textu. Další informace najdete v tématu `nFormat` parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metoda.  
  
 [v]`uiState`  
 (Vyhrazené).  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro kreslení text tlačítka pomocí vlastní kód.  
  
##  <a name="onfillbackground"></a>CMFCButton::OnFillBackground  
 Voláno rámcem k vykreslení pozadí textu tlačítka.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectClient`  
 Odkaz na obdélníku bounds tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro kreslení na pozadí tlačítko pomocí vlastní kód.  
  
##  <a name="selectfont"></a>CMFCButton::SelectFont  
 Načte písma, který je přidružený kontext zadané zařízení.  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Potlačí tuto metodu použít vlastní kód pro načtení písmo.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode  
 Nastaví tlačítka režimu automatické opakování.  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTimeDelay`  
 Nezáporné číslo, které udává interval mezi zprávy odeslané do nadřazeného okna. Interval se měří v milisekundách a jeho výchozí hodnota je 500 milisekund. Zadejte nula. Chcete-li zakázat režim automatické opakování zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda způsobí, že tlačítko neustále odesílání wm_command – zprávy do nadřazeného okna, dokud tlačítko vydání, nebo `nTimeDelay` parametr je nastaven na hodnotu nula.  
  
##  <a name="setcheckedimage"></a>CMFCButton::SetCheckedImage  
 Nastaví obrázek pro tlačítko zaškrtnuté.  
  
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
 [v]`hIcon`  
 Zpracování na ikonu, který obsahuje bitovou mapu a maska pro novou bitovou kopii.  
  
 [v]`bAutoDestroy`  
 `TRUE`Chcete-li určit, že rastrový obrázek prostředky ukončit automaticky; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
 [v]`hIconHot`  
 Zpracování na ikonu, která obsahuje bitovou kopii pro vybraný stav.  
  
 [v]`hBitmap`  
 Popisovač rastrového obrázku, který obsahuje bitovou kopii pro jiný vybraný stav.  
  
 [v]`hBitmapHot`  
 Popisovač rastrového obrázku, který obsahuje bitovou kopii pro vybraný stav.  
  
 [v]`bMap3dColors`  
 Určuje průhlednou barvu pozadí tlačítko; To znamená, vzhled tlačítka. `TRUE`Chcete použít hodnotu barva RGB (192, 192, 192); `FALSE` použít hodnoty barvy definované `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [v]`uiBmpResId`  
 ID prostředku bitové kopie není vybraná.  
  
 [v]`uiBmpHotResId`  
 ID prostředku pro vybranou image.  
  
 [v]`hIconDisabled`  
 Zpracování na ikonu pro bitovou kopii zakázané.  
  
 [v]`hBitmapDisabled`  
 Popisovač rastrového obrázku, který obsahuje bitovou kopii zakázané.  
  
 [v]`uiBmpDsblResID`  
 ID prostředku zakázané rastrového obrázku.  
  
 [v]`bAlphaBlend`  
 `TRUE`Chcete-li používat pouze 32-bit Image, které používají alfa kanálu; `FALSE`, nechcete použít pouze obrázky alfa kanálu. Výchozí hodnota je `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setfacecolor"></a>CMFCButton::SetFaceColor  
 Nastaví barvu pozadí pro text tlačítka.  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`crFace`  
 Hodnotu barva RGB.  
  
 [v]`bRedraw`  
 `TRUE`na obrazovce ho překreslit okamžitě; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li definovat nové barvu výplně pozadí tlačítko (vzhled). Všimněte si, že na pozadí není vyplněno, kdy [CMFCButton::m_bTransparent](#m_btransparent) členské proměnné je `TRUE`.  
  
##  <a name="setimage"></a>CMFCButton::SetImage  
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
 [v]`hIcon`  
 Zpracování na ikonu, který obsahuje bitovou mapu a maska pro novou bitovou kopii.  
  
 [v]`bAutoDestroy`  
 `TRUE`Chcete-li určit, že rastrový obrázek prostředky ukončit automaticky; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
 [v]`hIconHot`  
 Zpracování na ikonu, která obsahuje bitovou kopii pro vybraný stav.  
  
 [v]`hBitmap`  
 Popisovač rastrového obrázku, který obsahuje bitovou kopii pro jiný vybraný stav.  
  
 [v]`hBitmapHot`  
 Popisovač rastrového obrázku, který obsahuje bitovou kopii pro vybraný stav.  
  
 [v]`uiBmpResId`  
 ID prostředku bitové kopie není vybraná.  
  
 [v]`uiBmpHotResId`  
 ID prostředku pro vybranou image.  
  
 [v]`bMap3dColors`  
 Určuje průhlednou barvu pozadí tlačítko; To znamená, vzhled tlačítka. `TRUE`Chcete použít hodnotu barva RGB (192, 192, 192); `FALSE` použít hodnoty barvy definované `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [v]`hIconDisabled`  
 Zpracování na ikonu pro bitovou kopii zakázané.  
  
 [v]`hBitmapDisabled`  
 Popisovač rastrového obrázku, který obsahuje bitovou kopii zakázané.  
  
 [v]`uiBmpDsblResID`  
 ID prostředku zakázané rastrového obrázku.  
  
 [v]`bAlphaBlend`  
 `TRUE`Chcete-li používat pouze 32-bit Image, které používají alfa kanálu; `FALSE`, nechcete použít pouze obrázky alfa kanálu. Výchozí hodnota je `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat různé verze `SetImage` metoda v `CMFCButton` třídy. V příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor  
 Nastavuje obrázek, kurzoru.  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hcursor`  
 Popisovač kurzoru.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k přidružení bitovou kopii kurzoru, jako je například ruční kurzor, pomocí tlačítka. Kurzor je načten z prostředků aplikace.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `SetMouseCursor` metoda v `CMFCButton` třídy. V příkladu je součástí kód [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand  
 Nastaví kurzor na bitovou kopii dlaně.  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte pro přidružení kurzoru bitové kopie ruční tlačítko. Kurzor je načten z prostředků aplikace.  
  
##  <a name="setstdimage"></a>CMFCButton::SetStdImage  
 Používá `CMenuImages` objekt, který chcete nastavit obrázek tlačítka.  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`id`  
 Jeden z identifikátorů tlačítko bitové kopie, které je definováno v `CMenuImage::IMAGES_IDS` výčtu. Hodnoty bitové kopie specifikujte bitové kopie, jako je například šipky, kódy PIN a přepínače.  
  
 [v]`state`  
 Jeden z identifikátorů stavu tlačítko bitové kopie, které je definováno v `CMenuImages::IMAGE_STATE` výčtu. Stavy image zadat tlačítko barvy například černé, šedé, světla šedá bílé a tmavým šedá. Výchozí hodnota je `CMenuImages::ImageBlack`.  
  
 [v]`idDisabled`  
 Jeden z identifikátorů tlačítko bitové kopie, které je definováno v `CMenuImage::IMAGES_IDS` výčtu. Obrázek označuje, že tlačítko zakázána. Výchozí hodnota je první obrázek tlačítka ( `CMenuImages::IdArrowDown`).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settextcolor"></a>CMFCButton::SetTextColor  
 Nastaví barvu textu tlačítka pro tlačítko, které není vybraná.  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`clrText`  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor  
 Nastaví barvu textu tlačítka pro tlačítko, který je vybraný.  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`clrTextHot`  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settooltip"></a>CMFCButton::SetTooltip  
 Přidruží popisek tlačítka.  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszToolTipText`  
 Ukazatel na hodnotu text pro popis tlačítka. Zadejte hodnotu NULL zakázat popisek.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizetocontent"></a>CMFCButton::SizeToContent  
 Změní velikost tlačítko obsahovat jeho text tlačítka a bitové kopie.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bCalcOnly`  
 `TRUE`vypočítat, ale nemění velikost nového tlačítka; `FALSE` ke změně velikosti tlačítka. Výchozí hodnota je `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt, který obsahuje novou velikost tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vypočítá nové velikosti, která zahrnuje vodorovné okraj 10 pixelů a svislé okraj 5 pixelů.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl – třída](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton – třída](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton – třída](../../mfc/reference/cmfcmenubutton-class.md)
