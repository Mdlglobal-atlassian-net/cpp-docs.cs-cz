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
ms.openlocfilehash: 5434801969a55387a5b5555c9a4ade22f1969e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367781"
---
# <a name="cmfcbutton-class"></a>CMFCButton – třída

Třída `CMFCButton` přidává do třídy [CButton](../../mfc/reference/cbutton-class.md) funkce, jako je například zarovnání textu tlačítka, kombinování textu tlačítka a obrazu, výběr kurzoru a určení tipu nástroje.

## <a name="syntax"></a>Syntaxe

```
class CMFCButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Výchozí konstruktor.|
|`CMFCButton::~CMFCButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCButton::Vyčištění](#cleanup)|Obnoví vnitřní proměnné a uvolní přidělené prostředky, jako jsou obrázky, bitmapy a ikony.|
|`CMFCButton::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCButton::DrawItem`|Volat rámci při vizuální aspekt nakreslené ho vlastníka tlačítko se změnilo. (Přepíše [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Určuje, zda se má zobrazit úplný text popisku ve velkém okně popisku nebo zkrácenou verzi textu v malém okně popisku.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Určuje, zda je písmo textu tlačítka stejné jako písmo nabídky aplikace.|
|[CMFCButton::Povolit nastavení windowsthemingu](#enablewindowstheming)|Určuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.|
|`CMFCButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Vrátí odkaz na základní ovládací prvek popisku.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Označuje, zda je zaškrtávací políčko nebo přepínací tlačítko automatické tlačítko.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Označuje, zda je tlačítko nastaveno na režim automatického opakování.|
|[CMFCButton::Zaškrtávací políčko IsCheckBox](#ischeckbox)|Označuje, zda je tlačítko zaškrtávací políčko.|
|[CMFCButton::Jezaškrtnuto](#ischecked)|Označuje, zda je zaškrtnuto aktuální tlačítko.|
|[CMFCButton::Zvýrazněno](#ishighlighted)|Označuje, zda je tlačítko zvýrazněno.|
|[CMFCButton::Je stisknuto](#ispressed)|Označuje, zda je stisknuto a zvýrazněno tlačítko.|
|[CMFCButton::IsPushed](#ispushed)|Označuje, zda je stisknuto tlačítko.|
|[CMFCButton::isradiobutton](#isradiobutton)|Označuje, zda je tlačítko přepínací.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Označuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.|
|`CMFCButton::OnDrawParentBackground`|Nakreslí pozadí nadřazeného tlačítka v zadané oblasti. (Přepíše [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::Nastavit automatický režim opakování](#setautorepeatmode)|Nastaví tlačítko do režimu automatického opakování.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Nastaví obrázek pro zaškrtnuté tlačítko.|
|[CMFCButton::SetfaceColor](#setfacecolor)|Nastaví barvu pozadí textu tlačítka.|
|[CMFCButton::SetImage](#setimage)|Nastaví obrázek tlačítka.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Nastaví obraz kurzoru.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Nastaví kurzor na obraz ruky.|
|[CMFCButton::SetStdImage](#setstdimage)|Používá `CMenuImages` objekt k nastavení obrazu tlačítka.|
|[CMFCButton::SetTextColor](#settextcolor)|Nastaví barvu textu tlačítka pro tlačítko, které není vybráno.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Nastaví barvu textu tlačítka pro vybrané tlačítko.|
|[CMFCButton::SetTooltip](#settooltip)|Přidruží popis ekponovacího tlačítka.|
|[CMFCButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby obsahovalo text a obrázek tlačítka.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCButton::Ondraw](#ondraw)|Volat rámci nakreslit tlačítko.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Volat rámci k nakreslení hranice tlačítka.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Volat rámci nakreslit obdélník fokusu pro tlačítko.|
|[CMFCButton::OnDrawText](#ondrawtext)|Volat rámci nakreslit text tlačítka.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Volat rámci nakreslit pozadí textu tlačítka.|
|[CMFCButton::SelectFont](#selectfont)|Načte písmo, které je přidruženo k zadanému kontextu zařízení.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Určuje zarovnání textu tlačítka.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Určuje, zda se mají používat motivy systému Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Označuje, zda chcete kolem tlačítka nakreslit obdélník fokusu.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Určuje styl tlačítka, například bez okrajů, plochý, poloplochý nebo 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Pokud true, umožňuje zakázané tlačítko, které mají být vypracovány jako šedě-out.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Označuje, zda se má zvýraznit tlačítko ve stylu BS_CHECKBOX, když na něj kurzor najedete myší.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Označuje, zda má reagovat na události tlačítka dolů.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Označuje, zda se má zobrazit obrázek na pravé straně tlačítka.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Označuje, zda je obrázek nad tlačítkem.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Označuje, zda je tlačítko průhledné.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Označuje, zda poslední událost kliknutí byla poklepáním.|

## <a name="remarks"></a>Poznámky

Jiné typy tlačítek jsou odvozeny z `CMFCButton` třídy, jako je například třída [CMFCURLLinkButton,](../../mfc/reference/cmfclinkctrl-class.md) která podporuje hypertextové odkazy, a `CMFCColorButton` třída, která podporuje dialogové okno pro výběr barev.

Styl objektu `CMFCButton` může být *3D*, *plochý*, *poloplochý* nebo *bez ohraničení*. Text tlačítka lze zarovnat vlevo, nahoře nebo uprostřed tlačítka. Za běhu můžete určit, zda se na tlačítku zobrazí text, obrázek nebo text a obrázek. Můžete také určit, že se určitý obrázek kurzoru zobrazí, když kurzor najeví nad tlačítkem.

Vytvořte ovládací prvek tlačítka buď přímo v kódu, nebo pomocí nástroje **Průvodce třídami knihovny MFC** a šablony dialogového okna. Pokud vytvoříte ovládací prvek tlačítka `CMFCButton` přímo, přidejte proměnnou do `Create` aplikace a `CMFCButton` pak volání konstruktoru a metody objektu. Pokud používáte **Průvodce třídou knihovny MFC**, přidejte do aplikace proměnnou `CButton` a změňte typ proměnné z na `CButton` . `CMFCButton`

Chcete-li zpracovat oznámení v aplikaci dialogového okna, přidejte položku mapy zprávy a obslužnou rutinu události pro každé oznámení. Oznámení odeslaná objektem `CMFCButton` jsou stejná jako `CButton` oznámení odeslaná objektem.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat vlastnosti tlačítka pomocí `CMFCButton` různých metod ve třídě. Příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CmFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbutton.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFCButton::Vyčištění

Obnoví vnitřní proměnné a uvolní přidělené prostředky, jako jsou obrázky, bitmapy a ikony.

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Určuje, zda se má zobrazit úplný text popisku ve velkém okně popisku nebo zkrácenou verzi textu v malém okně popisku.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
[v] TRUE pro zobrazení celého textu; NEPRAVDA pro zobrazení zkráceného textu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Určuje, zda je písmo textu tlačítka stejné jako písmo nabídky aplikace.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
[v] TRUE pro použití písma nabídky aplikace jako písma textu tlačítka; False použít systémové písmo. Výchozí hodnota je TRUE.

*bPřekreslit*<br/>
[v] TRUE okamžitě překreslit obrazovku; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Pokud tuto metodu nepoužijete k určení písma textu tlačítka, můžete určit písmo pomocí metody [CWnd::SetFont.](../../mfc/reference/cwnd-class.md#setfont) Pokud písmo vůbec nezadáte, rozhraní framework nastaví výchozí písmo.

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFCButton::Povolit nastavení windowsthemingu

Určuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE chcete-li použít aktuální motiv systému Windows k nakreslení ohraničení tlačítek; Nepoužívejte motiv systému Windows. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda ovlivňuje všechna tlačítka v aplikaci, které jsou odvozeny z třídy. `CMFCButton`

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Vrátí odkaz na základní ovládací prvek popisku.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na základní ovládací prvek popisku.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFCButton::IsAutoCheck

Označuje, zda je zaškrtávací políčko nebo přepínací tlačítko automatické tlačítko.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud má tlačítko styl BS_AUTOCHECKBOX nebo BS_AUTORADIOBUTTON; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Označuje, zda je tlačítko nastaveno na režim automatického opakování.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko nastaveno na režim automatického opakování; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pomocí metody [CMFCButton::SetAutorepeatMode](#setautorepeatmode) nastavte tlačítko do režimu automatického opakování.

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFCButton::Zaškrtávací políčko IsCheckBox

Označuje, zda je tlačítko zaškrtávací políčko.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud má tlačítko BS_CHECKBOX nebo BS_AUTOCHECKBOX styl; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFCButton::Jezaškrtnuto

Označuje, zda je zaškrtnuto aktuální tlačítko.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zaškrtnuto aktuální tlačítko; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Rozhraní framework používá různé způsoby, jak označit, že jsou kontrolovány různé druhy tlačítek. Například přepínací tlačítko je zaškrtnuto, pokud obsahuje tečku; pokud obsahuje **x**, zaškrtázací políčko .

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFCButton::Zvýrazněno

Označuje, zda je tlačítko zvýrazněno.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko zvýrazněno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Když na něj najeze myší najedete myší, tlačítko se zvýrazní.

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFCButton::Je stisknuto

Označuje, zda je stisknuto a zvýrazněno tlačítko.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je stisknuto tlačítko; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFCButton::IsPushed

Označuje, zda je stisknuto tlačítko.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko stisknuto; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFCButton::isradiobutton

Označuje, zda je tlačítko přepínací.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je styl tlačítka BS_RADIOBUTTON nebo BS_AUTORADIOBUTTON; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Označuje, zda styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud styl ohraničení tlačítka odpovídá aktuálnímu motivu systému Windows; jinak NEPRAVDA.

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Určuje, zda se mají při kreslení tlačítka používat motivy systému Windows XP.

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Označuje, zda chcete kolem tlačítka nakreslit obdélník fokusu.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Poznámky

Nastavte `m_bDrawFocus` člen na TRUE, abyste určili, že rozhraní nakreslí obdélník fokusu kolem textu a obrazu tlačítka, pokud se na tlačítko zaměří.

Konstruktor `CMFCButton` inicializuje tento člen na HODNOTU PRAVDA.

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

Pokud true, umožňuje zakázané tlačítko, které mají být vypracovány jako šedě-out.

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Označuje, zda se má zvýraznit tlačítko ve stylu BS_CHECKBOX, když na něj kurzor najedete myší.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Poznámky

Nastavte `m_bHighlightChecked` člen na HODNOTU TRUE, abyste určili, že rozhraní framework uvede tlačítko ve stylu BS_CHECKBOX, když na něj najedete myší.

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Označuje, zda má reagovat na události tlačítka dolů.

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFCButton::m_bRightImage

Označuje, zda se má zobrazit obrázek na pravé straně tlačítka.

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFCButton::m_bTopImage](#m_bTopImage)

Označuje, zda je obrázek nad tlačítkem.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Poznámky

Nastavte `m_bRightImage` člen na HODNOTU TRUE, abyste určili, že rozhraní zobrazí obrázek tlačítka napravo od textového popisku tlačítka.

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFCButton::m_bTransparent

Označuje, zda je tlačítko průhledné.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Poznámky

Nastavte `m_bTransparent` člen na TRUE, abyste určili, že rozhraní provede tlačítko průhledné. Konstruktor `CMFCButton` inicializuje tento člen na HODNOTU FALSE.

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Určuje zarovnání textu tlačítka.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Poznámky

K určení zarovnání textu tlačítka použijte jednu z následujících `CMFCButton::AlignStyle` hodnot výčtu:

|Hodnota|Popis|
|-----------|-----------------|
|ALIGN_CENTER|(Výchozí) Zarovná text tlačítka ke středu tlačítka.|
|ALIGN_LEFT|Zarovná text tlačítka na levou stranu tlačítka.|
|ALIGN_RIGHT|Zarovná text tlačítka na pravou stranu tlačítka.|

Konstruktor `CMFCButton` inicializuje tento člen ALIGN_CENTER.

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

Označuje, zda poslední událost kliknutí byla poklepáním.|

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Určuje styl tlačítka, například bez okrajů, plochý, poloplochý nebo 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Poznámky

V následující tabulce `CMFCButton::m_nFlatStyle` jsou uvedeny hodnoty výčtu, které určují vzhled tlačítka.

|Hodnota|Popis|
|-----------|-----------------|
|BUTTONSTYLE_3D|(Výchozí) Zdá se, že tlačítko má vysoké, trojrozměrné strany. Po klepnutí na tlačítko se zdá, že je stisknuto do hlubokého odsazení.|
|BUTTONSTYLE_FLAT|Pokud se myš nepozastaví nad tlačítkem, tlačítko se zdá být dvojrozměrné a nemá vystouplou stranu. Když se myš pozastaví nad tlačítkem, zdá se, že má nízké trojrozměrné strany. Po klepnutí na tlačítko se zdá, že je stisknuto do mělkého odsazení.|
|BUTTONSTYLE_SEMIFLAT|Zdá se, že tlačítko má nízké trojrozměrné strany. Po klepnutí na tlačítko se zdá, že je stisknuto do hlubokého odsazení.|
|BUTTONSTYLE_NOBORDERS|Tlačítko nemá vystouplou stranu a vždy se zobrazí dvojrozměrné. Tlačítko se při klepnutí nezobrazí stisknutí do odsazení.|

Konstruktor `CMFCButton` inicializuje tento člen BUTTONSTYLE_3D.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit hodnoty `m_nFlatStyle` členské proměnné `CMFCButton` ve třídě. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFCButton::Ondraw

Volat rámci nakreslit tlačítko.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Odkaz na obdélník, který ohraničuje tlačítko.

*uiState*<br/>
[v] Aktuální stav tlačítka. Další informace naleznete `itemState` v tématu člen [struktury DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu použít vlastní kód k nakreslení tlačítka.

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Volat rámci k nakreslení hranice tlačítka.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectClient*<br/>
[v] Odkaz na obdélník, který ohraničuje tlačítko.

*uiState*<br/>
[v] Aktuální stav tlačítka. Další informace naleznete `itemState` v tématu člen [struktury DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu použít vlastní kód k nakreslení ohraničení.

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Volat rámci nakreslit obdélník fokusu pro tlačítko.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectClient*<br/>
[v] Odkaz na obdélník, který ohraničuje tlačítko.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu použít vlastní kód k nakreslení obdélníkfobené.

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFCButton::OnDrawText

Volat rámci nakreslit text tlačítka.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Odkaz na obdélník, který ohraničuje tlačítko.

*strText*<br/>
[v] Text k tomu.

*uiDTFlags*<br/>
[v] Příznaky, které určují, jak formátovat text. Další informace naleznete v parametru *nFormat* metody [CDC::DrawText.](../../mfc/reference/cdc-class.md#drawtext)

*uiState*<br/>
[v] Vyhrazena.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu použít vlastní kód k nakreslení textu tlačítka.

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFCButton::OnFillBackground

Volat rámci nakreslit pozadí textu tlačítka.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectClient*<br/>
[v] Odkaz na obdélník, který ohraničuje tlačítko.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu použít vlastní kód k nakreslení pozadí tlačítka.

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFCButton::SelectFont

Načte písmo, které je přidruženo k zadanému kontextu zařízení.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

### <a name="return-value"></a>Návratová hodnota

Přepsat tuto metodu použít vlastní kód k načtení písma.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFCButton::Nastavit automatický režim opakování

Nastaví tlačítko do režimu automatického opakování.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parametry

*nZpoždění času*<br/>
[v] Nezáporné číslo, které určuje interval mezi zprávami, které jsou odesílány do nadřazeného okna. Interval se měří v milisekundách a jeho výchozí hodnota je 500 milisekund. Zadejte nulu, chcete-li zakázat režim automatického opakování zpráv.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že tlačítko neustále odesílat WM_COMMAND zprávy do nadřazeného okna, dokud je tlačítko uvolněno, nebo *parametr nTimeDelay* je nastavenna na nulu.

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

Nastaví obrázek pro zaškrtnuté tlačítko.

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

*hIkona*<br/>
[v] Zpracovat ikonu, která obsahuje bitmapu a masku pro nový obraz.

*bAutoDestroy*<br/>
[v] TRUE, chcete-li určit, že bitmapové prostředky budou zničeny automaticky; jinak NEPRAVDA. Výchozí hodnota je TRUE.

*hIconHot*<br/>
[v] Zpracovat ikonu, která obsahuje obrázek pro vybraný stav.

*hBitmap*<br/>
[v] Zpracovat bitmapu, která obsahuje obraz pro nevybraný stav.

*hBitmapHot*<br/>
[v] Zpracovat bitmapu, která obsahuje obraz pro vybraný stav.

*bMap3dBarvy*<br/>
[v] Určuje průhlednou barvu pozadí tlačítka; to znamená, že tvář tlačítka. TRUE použít hodnotu barvy RGB(192, 192, 192); NEPRAVDA pro použití hodnoty `AFX_GLOBAL_DATA::clrBtnFace`barvy definované uživatelem .

*uiBmpResId*<br/>
[v] ID prostředku pro nevybraný obrázek.

*uiBmpHotResId*<br/>
[v] ID prostředku pro vybraný obrázek.

*hIconDisabled*<br/>
[v] Zpracovat ikonu pro zakázaný obrázek.

*hBitmapZakázáno*<br/>
[v] Zpracovat bitmapu, která obsahuje zakázaný obraz.

*uiBmpDsblResID*<br/>
[v] ID prostředku zakázané bitmapy.

*bAlphaBlend*<br/>
[v] TRUE použít pouze 32bitové obrazy, které používají alfa kanál; FALSE, nepoužívat pouze alfa kanál obrazy. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFCButton::SetfaceColor

Nastaví barvu pozadí textu tlačítka.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*crFace*<br/>
[v] Hodnota barvy RGB.

*bPřekreslit*<br/>
[v] TRUE okamžitě překreslit obrazovku; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k definování nové barvy výplně pro pozadí tlačítka (plochu). Všimněte si, že pozadí není vyplněno, pokud je proměnná [člena CMFCButton::m_bTransparent](#m_btransparent) TRUE.

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFCButton::SetImage

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

*hIkona*<br/>
[v] Zpracovat ikonu, která obsahuje bitmapu a masku pro nový obraz.

*bAutoDestroy*<br/>
[v] TRUE, chcete-li určit, že bitmapové prostředky budou zničeny automaticky; jinak NEPRAVDA. Výchozí hodnota je TRUE.

*hIconHot*<br/>
[v] Zpracovat ikonu, která obsahuje obrázek pro vybraný stav.

*hBitmap*<br/>
[v] Zpracovat bitmapu, která obsahuje obraz pro nevybraný stav.

*hBitmapHot*<br/>
[v] Zpracovat bitmapu, která obsahuje obraz pro vybraný stav.

*uiBmpResId*<br/>
[v] ID prostředku pro nevybraný obrázek.

*uiBmpHotResId*<br/>
[v] ID prostředku pro vybraný obrázek.

*bMap3dBarvy*<br/>
[v] Určuje průhlednou barvu pozadí tlačítka; to znamená, že tvář tlačítka. TRUE použít hodnotu barvy RGB(192, 192, 192); NEPRAVDA pro použití hodnoty `AFX_GLOBAL_DATA::clrBtnFace`barvy definované uživatelem .

*hIconDisabled*<br/>
[v] Zpracovat ikonu pro zakázaný obrázek.

*hBitmapZakázáno*<br/>
[v] Zpracovat bitmapu, která obsahuje zakázaný obraz.

*uiBmpDsblResID*<br/>
[v] ID prostředku zakázané bitmapy.

*bAlphaBlend*<br/>
[v] TRUE použít pouze 32bitové obrazy, které používají alfa kanál; FALSE, nepoužívat pouze alfa kanál obrazy. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `SetImage` verze metody `CMFCButton` ve třídě. Příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Nastaví obraz kurzoru.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parametry

*hkurzor*<br/>
[v] Úchyt kurzoru.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete k tlačítku přidružit obrázek kurzoru, například kurzor ruky. Kurzor je načten z prostředků aplikace.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `SetMouseCursor` používat metodu ve `CMFCButton` třídě. Příklad je součástí kódu v [nové ovládací prvky ukázky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Nastaví kurzor na obraz ruky.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete přidružit obrázek kurzoru ruky k tlačítku. Kurzor je načten z prostředků aplikace.

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFCButton::SetStdImage

Používá `CMenuImages` objekt k nastavení obrazu tlačítka.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Jeden z identifikátorů obrázku tlačítka, `CMenuImage::IMAGES_IDS` který je definován ve výčtu. Hodnoty obrazu určují obrazy, jako jsou šipky, špendlíky a přepínací tlačítka.

*Státu*<br/>
[v] Jeden z identifikátorů stavu obrázku tlačítka, který je definován ve výčtu. `CMenuImages::IMAGE_STATE` Stavy obrazu určují barvy tlačítek, jako je černá, šedá, světle šedá, bílá a tmavě šedá. Výchozí hodnota je `CMenuImages::ImageBlack`.

*idZakázáno*<br/>
[v] Jeden z identifikátorů obrázku tlačítka, `CMenuImage::IMAGES_IDS` který je definován ve výčtu. Obrázek označuje, že tlačítko je zakázáno. Výchozí hodnota je první obrázek tlačítka ( `CMenuImages::IdArrowDown`).

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFCButton::SetTextColor

Nastaví barvu textu tlačítka pro tlačítko, které není vybráno.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parametry

*clrText*<br/>
[v] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Nastaví barvu textu tlačítka pro vybrané tlačítko.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parametry

*clrTextHot*<br/>
[v] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFCButton::SetTooltip

Přidruží popis ekponovacího tlačítka.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parametry

*lpszToolTipText*<br/>
[v] Ukazatel na text popisku. Zadejte hodnotu NULL, chcete-li zakázat popis.

### <a name="remarks"></a>Poznámky

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCButton::SizeToContent

Změní velikost tlačítka tak, aby obsahovalo text a obrázek tlačítka.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[v] TRUE pro výpočet, ale ne změnit, novou velikost tlačítka; NEPRAVDA pro změnu velikosti tlačítka. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CSize` který obsahuje novou velikost tlačítka.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vypočítá novou velikost, která zahrnuje vodorovný okraj 10 pixelů a svislý okraj 5 pixelů.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl – třída](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton – třída](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton – třída](../../mfc/reference/cmfcmenubutton-class.md)
