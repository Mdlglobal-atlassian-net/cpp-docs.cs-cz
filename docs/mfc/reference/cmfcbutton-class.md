---
title: CMFCButton – třída
ms.date: 08/28/2018
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
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505863"
---
# <a name="cmfcbutton-class"></a>CMFCButton – třída

Třída přidává funkce do třídy CButton, jako je například zarovnání textu tlačítka, kombinování textu tlačítka a obrázku, výběr kurzoru a určení popisu tlačítka. [](../../mfc/reference/cbutton-class.md) `CMFCButton`

## <a name="syntax"></a>Syntaxe

```
class CMFCButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Výchozí konstruktor|
|`CMFCButton::~CMFCButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCButton:: CleanUp](#cleanup)|Obnoví interní proměnné a uvolní přidělené prostředky, jako jsou obrázky, rastry a ikony.|
|`CMFCButton::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCButton::DrawItem`|Volá se rozhraním, když se změní vizuální aspekt tlačítka, které bylo vykresleno vlastníkem. (Overrides [CButton::D rawitem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Určuje, zda se má zobrazovat úplný text popisku v rámci velkého okna s popisem tlačítka nebo zkrácená verze textu v malém okně s popisem tlačítka.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Určuje, zda je písmo textu tlačítka stejné jako písmo nabídky aplikace.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Určuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.|
|`CMFCButton::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Vrátí odkaz na podkladový ovládací prvek ToolTip.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Označuje, zda je zaškrtávací políčko nebo přepínač automatickým tlačítkem.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Určuje, zda je tlačítko nastaveno na režim automatického opakování.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Označuje, zda se jedná o tlačítko zaškrtávacího políčka.|
|[CMFCButton::IsChecked](#ischecked)|Označuje, zda je vybráno aktuální tlačítko.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Označuje, zda je zvýrazněno tlačítko.|
|[CMFCButton::IsPressed](#ispressed)|Označuje, zda je tlačítko vloženo a zvýrazněno.|
|[CMFCButton::-pushd](#ispushed)|Označuje, zda je tlačítko vloženo.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Označuje, zda se jedná o přepínač.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Určuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.|
|`CMFCButton::OnDrawParentBackground`|Vykreslí pozadí nadřazeného tlačítka v zadané oblasti. (Overrides [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Potlačení [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Nastaví tlačítko na režim automatického opakování.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Nastaví obrázek pro kontrolované tlačítko.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Nastaví barvu pozadí pro text tlačítka.|
|[CMFCButton::SetImage](#setimage)|Nastaví obrázek tlačítka.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Nastaví obrázek kurzoru.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Nastaví ukazatel na obrázek ruky.|
|[CMFCButton::SetStdImage](#setstdimage)|`CMenuImages` Použije objekt k nastavení obrázku tlačítka.|
|[CMFCButton::SetTextColor](#settextcolor)|Nastaví barvu textu tlačítka pro tlačítko, které není vybráno.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Nastaví barvu textu tlačítka pro vybrané tlačítko.|
|[CMFCButton::SetTooltip](#settooltip)|Přidruží popisek k tlačítku.|
|[CMFCButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby obsahovalo text a obrázek tlačítka.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCButton:: Draw](#ondraw)|Volá se rozhraním, aby se nakreslilo tlačítko.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Volá se rozhraním, aby se nakreslilo ohraničení tlačítka.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Volá se rozhraním, aby se vykreslil rámeček fokusu pro tlačítko.|
|[CMFCButton::OnDrawText](#ondrawtext)|Volá se rozhraním, aby se nakreslil text tlačítka.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Volá se rozhraním, aby se nakreslilo pozadí textu tlačítka.|
|[CMFCButton::SelectFont](#selectfont)|Načte písmo přidružené k zadanému kontextu zařízení.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Určuje zarovnání textu tlačítka.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Určuje, jestli se mají používat motivy Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Označuje, zda se má kolem tlačítka nakreslit obdélník s fokusem.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Určuje styl tlačítka, například bez okrajového, plochého, částečně plochého nebo trojrozměrného.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|V případě hodnoty TRUE umožňuje, aby bylo zakázané tlačítko vykresleno jako šedě.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Označuje, zda má být zvýrazněno tlačítko BS_CHECKBOX, když se ukazatel myši nachází na pozadí.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Označuje, zda reagovat na události tlačítek dolů.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Označuje, zda se má na pravé straně tlačítka Zobrazit obrázek.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Určuje, zda je obrázek nad tlačítkem.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Určuje, zda je tlačítko transparentní.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Označuje, zda byla událost posledního kliknutí poklikáním.|

## <a name="remarks"></a>Poznámky

Jiné typy tlačítek jsou odvozeny z `CMFCButton` třídy, jako je například třída [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) , která podporuje `CMFCColorButton` hypertextové odkazy a třída, která podporuje dialogové okno Výběr barvy.

Stylem `CMFCButton` objektu může být prostorová, *plochá*, *částečně plochá* nebo *žádná ohraničení*. Text tlačítka lze Zarovnat vlevo, nahoře nebo uprostřed tlačítka. V době běhu můžete určit, zda tlačítko zobrazuje text, obrázek nebo text a obrázek. Můžete také určit, že se má při přesunutí ukazatele myši na tlačítko zobrazit konkrétní obrázek kurzoru.

Vytvořte ovládací prvek tlačítko buď přímo v kódu, nebo pomocí nástroje **Průvodce třídou MFC** a šablony dialogového okna. Pokud vytvoříte ovládací prvek tlačítko přímo, přidejte `CMFCButton` do aplikace proměnnou a potom zavolejte konstruktor a `Create` metody `CMFCButton` objektu. Použijete-li **Průvodce třídou knihovny MFC**, `CButton` přidejte do aplikace proměnnou a poté změňte typ proměnné z `CButton` na `CMFCButton`.

Pro zpracování zpráv s oznámením v aplikaci dialogového okna přidejte položku mapování zpráv a obslužnou rutinu události pro každé oznámení. Oznámení odesílaná `CMFCButton` objektem jsou shodná s tím, jak jsou odesílány `CButton` objektem.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak konfigurovat vlastnosti tlačítka pomocí různých metod ve `CMFCButton` třídě. Příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

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

**Záhlaví:** afxbutton. h

##  <a name="cleanup"></a>CMFCButton:: CleanUp

Obnoví interní proměnné a uvolní přidělené prostředky, jako jsou obrázky, rastry a ikony.

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Určuje, zda se má zobrazovat úplný text popisku v rámci velkého okna s popisem tlačítka nebo zkrácená verze textu v malém okně s popisem tlačítka.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parametry

*Přání*<br/>
pro TRUE pro zobrazení celého textu; Hodnota FALSE pro zobrazení zkráceného textu

### <a name="remarks"></a>Poznámky

##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Určuje, zda je písmo textu tlačítka stejné jako písmo nabídky aplikace.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*Přání*<br/>
pro TRUE pro použití písma nabídky aplikace jako písma textu tlačítka; FALSE pro použití systémového písma Výchozí hodnota je TRUE.

*bRedraw*<br/>
pro TRUE pro okamžité překreslování obrazovky; v opačném případě FALSE. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Pokud nepoužijete tuto metodu k zadání písma textu tlačítka, můžete zadat písmo pomocí metody [CWnd:: SetFont](../../mfc/reference/cwnd-class.md#setfont) . Pokud nezadáte vůbec písmo, rozhraní nastaví výchozí písmo.

##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Určuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE, pokud chcete použít aktuální motiv Windows k vykreslování ohraničení tlačítek; FALSE, pokud nechcete použít motiv Windows Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda ovlivňuje všechna tlačítka v aplikaci, která jsou odvozena z `CMFCButton` třídy.

##  <a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Vrátí odkaz na podkladový ovládací prvek ToolTip.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na podkladový ovládací prvek ToolTip.

### <a name="remarks"></a>Poznámky

##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck

Označuje, zda je zaškrtávací políčko nebo přepínač automatickým tlačítkem.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud má tlačítko Style BS_AUTOCHECKBOX nebo BS_AUTORADIOBUTTON; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Určuje, zda je tlačítko nastaveno na režim automatického opakování.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko nastaveno na režim automatického opakování; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pomocí metody [CMFCButton:: SetAutorepeatMode](#setautorepeatmode) nastavte tlačítko na režim automatického opakování.

##  <a name="ischeckbox"></a>CMFCButton:: zaškrtávací políčko

Označuje, zda se jedná o tlačítko zaškrtávacího políčka.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud má tlačítko buď styl BS_CHECKBOX nebo BS_AUTOCHECKBOX; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="ischecked"></a>CMFCButton::-Checked

Označuje, zda je vybráno aktuální tlačítko.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zaškrtnuto aktuální tlačítko; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Rozhraní používá různé způsoby, jak označit, že jsou zaškrtnuty různé druhy tlačítek. Například přepínač je zkontrolován, když obsahuje tečku; zaškrtávací políčko je zaškrtnuto, pokud obsahuje **X**.

##  <a name="ishighlighted"></a>CMFCButton::-zvýrazňovat

Označuje, zda je zvýrazněno tlačítko.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko zvýrazněno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tlačítko se zvýrazní, když ukazatel myši setrvá na tlačítku.

##  <a name="ispressed"></a>CMFCButton:: nastisknuté

Označuje, zda je tlačítko vloženo a zvýrazněno.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je stisknuto tlačítko; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="ispushed"></a>CMFCButton::-pushd

Označuje, zda je tlačítko vloženo.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko vloženo; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="isradiobutton"></a>CMFCButton::-RadioButton

Označuje, zda se jedná o přepínač.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je styl tlačítka BS_RADIOBUTTON nebo BS_AUTORADIOBUTTON; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Určuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows; v opačném případě FALSE.

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Určuje, zda se při vykreslování tlačítka použijí motivy systému Windows XP.

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Označuje, zda se má kolem tlačítka nakreslit obdélník s fokusem.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Poznámky

`m_bDrawFocus` Nastavte člena na hodnotu true, chcete-li určit, že rozhraní bude nakreslit obdélník výběru kolem textu tlačítka a obrázku, pokud tlačítko dostane fokus.

`CMFCButton` Konstruktor inicializuje tohoto člena na hodnotu true.

##  <a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

V případě hodnoty TRUE umožňuje, aby bylo zakázané tlačítko vykresleno jako šedě.

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Označuje, zda má být zvýrazněno tlačítko BS_CHECKBOX, když se ukazatel myši nachází na pozadí.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Poznámky

`m_bHighlightChecked` Nastavte člena na hodnotu true, chcete-li určit, že rozhraní bude zvýrazňovat BS_CHECKBOX tlačítko stylu, když ukazatel myši na něj najede myší.

##  <a name="m_bResponseOnButtonDown"></a> CMFCButton::m_bResponseOnButtonDown

Označuje, zda reagovat na události tlačítek dolů.

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage

Označuje, zda se má na pravé straně tlačítka Zobrazit obrázek.

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)

Určuje, zda je obrázek nad tlačítkem.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Poznámky

`m_bRightImage` Nastavte člena na hodnotu true, chcete-li určit, že rozhraní zobrazí obrázek tlačítka napravo od popisku textu tlačítka.

##  <a name="m_btransparent"></a>CMFCButton::m_bTransparent

Určuje, zda je tlačítko transparentní.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Poznámky

`m_bTransparent` Nastavte člena na hodnotu true, chcete-li určit, že rozhraní bude mít tlačítko transparentní. `CMFCButton` Konstruktor inicializuje tohoto člena na hodnotu false.

##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Určuje zarovnání textu tlačítka.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Poznámky

K určení zarovnání textu tlačítka `CMFCButton::AlignStyle` použijte jednu z následujících hodnot výčtu:

|Value|Popis|
|-----------|-----------------|
|ALIGN_CENTER|Výchozí Zarovná text tlačítka do středu tlačítka.|
|ALIGN_LEFT|Zarovná text tlačítka na levou stranu tlačítka.|
|ALIGN_RIGHT|Zarovná text tlačítka na pravou stranu tlačítka.|

`CMFCButton` Konstruktor inicializuje tohoto člena na ALIGN_CENTER.

##  <a name="m_bWasDblClk"></a>CMFCButton:: m_bWasDblClk] (#m_bWasDblClk) |

Označuje, zda byla událost posledního kliknutí poklikáním. |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Určuje styl tlačítka, například bez okrajového, plochého, částečně plochého nebo trojrozměrného.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny `CMFCButton::m_nFlatStyle` hodnoty výčtu, které určují vzhled tlačítka.

|Value|Popis|
|-----------|-----------------|
|BUTTONSTYLE_3D|Výchozí Zdá se, že tlačítko má vysokou trojrozměrné stranu. Po kliknutí na tlačítko se zobrazí tlačítko, které se stiskne do hloubkového odsazení.|
|BUTTONSTYLE_FLAT|Když se myš na tlačítko nezastaví, tlačítko se zdá být dvourozměrné a nevyvolává se strany. Když se ukazatel myši zastaví na tlačítku, zdá se, že tlačítko má nízké trojrozměrné strany. Po kliknutí na tlačítko se zobrazí tlačítko, které se stiskne do omezeného odsazení.|
|BUTTONSTYLE_SEMIFLAT|Zdá se, že tlačítko má malé, trojrozměrné strany. Po kliknutí na tlačítko se zobrazí tlačítko, které se stiskne do hloubkového odsazení.|
|BUTTONSTYLE_NOBORDERS|Tlačítko nemá vystouplé strany a vždy se zobrazuje dvourozměrně. Po kliknutí na tlačítko se při kliknutí na tlačítko nezobrazují jeho stisknutí.|

`CMFCButton` Konstruktor inicializuje tohoto člena na BUTTONSTYLE_3D.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit hodnoty `m_nFlatStyle` členské proměnné `CMFCButton` ve třídě. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

##  <a name="ondraw"></a>CMFCButton:: Draw

Volá se rozhraním, aby se nakreslilo tlačítko.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*OBD*<br/>
pro Odkaz na obdélník, který je ohraničený tlačítkem.

*uiState*<br/>
pro Stav aktuálního tlačítka Další informace najdete `itemState` v tématu věnovaném členu [struktury DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete použít vlastní kód k nakreslení tlačítka.

##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Volá se rozhraním, aby se nakreslilo ohraničení tlačítka.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*rectClient*<br/>
pro Odkaz na obdélník, který je ohraničený tlačítkem.

*uiState*<br/>
pro Stav aktuálního tlačítka Další informace najdete `itemState` v tématu věnovaném členu [struktury DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete použít vlastní kód k vykreslení ohraničení.

##  <a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Volá se rozhraním, aby se vykreslil rámeček fokusu pro tlačítko.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*rectClient*<br/>
pro Odkaz na obdélník, který je ohraničený tlačítkem.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete použít vlastní kód k vykreslení obdélníku fokusu.

##  <a name="ondrawtext"></a>CMFCButton::OnDrawText

Volá se rozhraním, aby se nakreslil text tlačítka.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*OBD*<br/>
pro Odkaz na obdélník, který je ohraničený tlačítkem.

*strText*<br/>
pro Text, který má být nakreslen.

*uiDTFlags*<br/>
pro Příznaky, které určují, jak se má text formátovat Další informace naleznete v parametru *nFormat* metody [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) .

*uiState*<br/>
pro Rezervovaný.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete použít vlastní kód k vykreslení textu tlačítka.

##  <a name="onfillbackground"></a>CMFCButton::OnFillBackground

Volá se rozhraním, aby se nakreslilo pozadí textu tlačítka.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*rectClient*<br/>
pro Odkaz na obdélník, který je ohraničený tlačítkem.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete použít vlastní kód k vykreslení pozadí tlačítka.

##  <a name="selectfont"></a>CMFCButton::SelectFont

Načte písmo přidružené k zadanému kontextu zařízení.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

### <a name="return-value"></a>Návratová hodnota

Tuto metodu přepište, pokud chcete použít vlastní kód pro načtení písma.

### <a name="remarks"></a>Poznámky

##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

Nastaví tlačítko na režim automatického opakování.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parametry

*nTimeDelay*<br/>
pro Nezáporné číslo, které určuje interval mezi zprávami, které jsou odeslány do nadřazeného okna. Interval se měří v milisekundách a jeho výchozí hodnota je 500 milisekund. Pokud chcete zakázat režim automatického opakování zprávy, zadejte nula.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že tlačítko bude trvale odesílat WM_COMMAND zprávy do nadřazeného okna, dokud se tlačítko neuvolní, nebo parametr *nTimeDelay* je nastaven na hodnotu nula.

##  <a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

Nastaví obrázek pro kontrolované tlačítko.

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

*hIcon*<br/>
pro Zajistěte, aby se natáhla ikona obsahující rastrový obrázek a maska pro nový obrázek.

*bAutoDestroy*<br/>
pro TRUE pro určení, že se prostředky bitmapy mají automaticky zničit; v opačném případě FALSE. Výchozí hodnota je TRUE.

*hIconHot*<br/>
pro Zpracování ikony, která obsahuje obrázek pro vybraný stav.

*hBitmap*<br/>
pro Zpracování rastrového obrázku, který obsahuje obrázek pro nevybraný stav

*hBitmapHot*<br/>
pro Zpracování rastrového obrázku, který obsahuje obrázek pro vybraný stav.

*bMap3dColors*<br/>
pro Určuje průhlednou barvu pozadí tlačítka; To znamená, že se jedná o obličej tlačítka. TRUE pro použití hodnoty Color RGB (192, 192, 192); FALSE pro použití hodnoty barvy definované `AFX_GLOBAL_DATA::clrBtnFace`.

*uiBmpResId*<br/>
pro ID prostředku pro nevybraný obrázek.

*uiBmpHotResId*<br/>
pro ID prostředku pro vybraný obrázek

*hIconDisabled*<br/>
pro Zpracování ikony pro zakázaný obrázek

*hBitmapDisabled*<br/>
pro Zpracování rastrového obrázku, který obsahuje zakázanou bitovou kopii.

*uiBmpDsblResID*<br/>
pro ID prostředku zakázaného rastrového obrázku

*bAlphaBlend*<br/>
pro TRUE pro použití pouze 32 bitových kopií, které používají alfa kanál; FALSE, pokud nechcete používat jenom obrázky alfa kanálu. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="setfacecolor"></a>CMFCButton::SetFaceColor

Nastaví barvu pozadí pro text tlačítka.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*crFace*<br/>
pro Hodnota barvy RGB.

*bRedraw*<br/>
pro TRUE pro okamžité překreslování obrazovky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k definování nové barvy výplně tlačítka na pozadí (Face). Všimněte si, že pozadí není vyplněno, pokud je proměnná členské proměnné [CMFCButton:: M_BTRANSPARENT](#m_btransparent) true.

##  <a name="setimage"></a>CMFCButton::SetImage

Nastaví obrázek tlačítka.

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

*hIcon*<br/>
pro Zajistěte, aby se natáhla ikona obsahující rastrový obrázek a maska pro nový obrázek.

*bAutoDestroy*<br/>
pro TRUE pro určení, že se prostředky bitmapy mají automaticky zničit; v opačném případě FALSE. Výchozí hodnota je TRUE.

*hIconHot*<br/>
pro Zpracování ikony, která obsahuje obrázek pro vybraný stav.

*hBitmap*<br/>
pro Zpracování rastrového obrázku, který obsahuje obrázek pro nevybraný stav

*hBitmapHot*<br/>
pro Zpracování rastrového obrázku, který obsahuje obrázek pro vybraný stav.

*uiBmpResId*<br/>
pro ID prostředku pro nevybraný obrázek.

*uiBmpHotResId*<br/>
pro ID prostředku pro vybraný obrázek

*bMap3dColors*<br/>
pro Určuje průhlednou barvu pozadí tlačítka; To znamená, že se jedná o obličej tlačítka. TRUE pro použití hodnoty Color RGB (192, 192, 192); FALSE pro použití hodnoty barvy definované `AFX_GLOBAL_DATA::clrBtnFace`.

*hIconDisabled*<br/>
pro Zpracování ikony pro zakázaný obrázek

*hBitmapDisabled*<br/>
pro Zpracování rastrového obrázku, který obsahuje zakázanou bitovou kopii.

*uiBmpDsblResID*<br/>
pro ID prostředku zakázaného rastrového obrázku

*bAlphaBlend*<br/>
pro TRUE pro použití pouze 32 bitových kopií, které používají alfa kanál; FALSE, pokud nechcete používat jenom obrázky alfa kanálu. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé verze `SetImage` metody `CMFCButton` ve třídě. Příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Nastaví obrázek kurzoru.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parametry

*hcursor*<br/>
pro Popisovač kurzoru.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li přidružit obrázek kurzoru, jako je například ukazatel, pomocí tlačítka. Kurzor je načten z prostředků aplikace.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `SetMouseCursor` metodu `CMFCButton` ve třídě. Příklad je částí kódu v [ukázce nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Nastaví ukazatel na obrázek ruky.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li přidružit obrázek kurzoru ruky k tlačítku. Kurzor je načten z prostředků aplikace.

##  <a name="setstdimage"></a>CMFCButton::SetStdImage

`CMenuImages` Použije objekt k nastavení obrázku tlačítka.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Jeden z identifikátorů obrázků tlačítek, který je definován ve `CMenuImage::IMAGES_IDS` výčtu. Hodnoty obrázků určují obrázky, například šipky, kolíky a přepínače.

*státech*<br/>
pro Jeden z identifikátorů stavu obrázku tlačítka, který je definován ve `CMenuImages::IMAGE_STATE` výčtu. Stavy obrázků určují barvy tlačítek, jako jsou černá, šedá, světlá šedá, bílá a tmavě šedá. Výchozí hodnota je `CMenuImages::ImageBlack`.

*idDisabled*<br/>
pro Jeden z identifikátorů obrázků tlačítek, který je definován ve `CMenuImage::IMAGES_IDS` výčtu. Obrázek označuje, že tlačítko je zakázané. Výchozí hodnota je první obrázek tlačítka ( `CMenuImages::IdArrowDown`).

### <a name="remarks"></a>Poznámky

##  <a name="settextcolor"></a>CMFCButton::SetTextColor

Nastaví barvu textu tlačítka pro tlačítko, které není vybráno.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parametry

*clrText*<br/>
pro Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Nastaví barvu textu tlačítka pro vybrané tlačítko.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parametry

*clrTextHot*<br/>
pro Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

##  <a name="settooltip"></a>CMFCButton::SetTooltip

Přidruží popisek k tlačítku.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parametry

*lpszToolTipText*<br/>
pro Ukazatel na text popisku. Chcete-li popis zakázat, zadejte hodnotu NULL.

### <a name="remarks"></a>Poznámky

##  <a name="sizetocontent"></a>CMFCButton::SizeToContent

Změní velikost tlačítka tak, aby obsahovalo text a obrázek tlačítka.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
pro TRUE pro výpočet, ale ne změnu, nová velikost tlačítka; Hodnota FALSE pro změnu velikosti tlačítka Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

`CSize` Objekt, který obsahuje novou velikost tlačítka.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vypočítá novou velikost, která zahrnuje vodorovný okraj 10 pixelů a svislý okraj 5 pixelů.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl – třída](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton – třída](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton – třída](../../mfc/reference/cmfcmenubutton-class.md)
