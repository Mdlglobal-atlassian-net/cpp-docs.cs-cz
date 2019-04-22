---
title: Cmfccolorbutton – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: c0c9ad79342f2013aa071240c684fce168e55c9e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779999"
---
# <a name="cmfccolorbutton-class"></a>Cmfccolorbutton – třída

`CMFCColorButton` a [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md) třídy se používají společně k implementaci ovládacího prvku pro výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Sestaví nový `CMFCColorButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí nebo zakáže "automatické" tlačítko, které je umístěn nad regulární barvy tlačítka. (Standardní systém automatické tlačítko má název **automatické**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže "other" tlačítko, který je umístěn pod regulární barvy tlačítka. (Standardní systém je označené jako "other" tlačítko **Další barvy**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální Automatická barva.|
|[CMFCColorButton::GetColor](#getcolor)|Načte barvy tlačítka.|
|[CMFCColorButton::SetColor](#setcolor)|Nastaví barvu tlačítka.|
|[CMFCColorButton::SetColorName](#setcolorname)|Nastaví název barvy.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců na dialogové okno Výběr barvy.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam barvy konkrétní dokumenty, které se zobrazují na dialogové okno Výběr barvy.|
|[CMFCColorButton::SetPalette](#setpalette)|Určuje paletu barev standardní zobrazení.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Změní velikost ovládacího prvku tlačítko, v závislosti na velikosti jeho textu a obrázků.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Určuje, zda aktuální barva – tlačítko se zobrazí v vizuálního stylu Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Volá se rozhraním pro zobrazení obrázku tlačítka.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Volá se rozhraním, chcete-li zobrazit ohraničení tlačítka.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Volá se rozhraním, když, zaměřuje se na tlačítko Zobrazit rámečku fokusu.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Volá se rozhraním, když dialogové okno Výběr barvy se má zobrazit.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializuje `m_pPalette` chráněný datový člen paletě zadaný nebo výchozí systémové palety.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Volá se rozhraním, když uživatel vybere barvu z palety dialogové okno Výběr barvy.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|`m_bAltColorDlg`|Logická hodnota. Při hodnotě TRUE se zobrazí rozhraní [cmfccolordialog –](../../mfc/reference/cmfccolordialog-class.md) Barva dialogové okno při *jiných* po kliknutí na tlačítko, nebo pokud je hodnota FALSE, systém barvy dialogové okno. Výchozí hodnota je TRUE. Další informace najdete v tématu [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Logická hodnota. Při hodnotě TRUE se rozhraní nastaví fokus v nabídce barvy v případě, že v nabídce se zobrazí, nebo pokud je hodnota FALSE, zaměřuje nezmění. Výchozí hodnota je TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Označuje, zda je povolen režim úprav pro bude tlačítko barev.|
|`m_Color`|A [COLORREF](/windows/desktop/gdi/colorref) hodnotu. Obsahuje aktuálně vybranou barvu.|
|`m_ColorAutomatic`|A [COLORREF](/windows/desktop/gdi/colorref) hodnotu. Obsahuje aktuálně vybraný výchozí barvy.|
|`m_Colors`|A [carray –](../../mfc/reference/carray-class.md) z [COLORREF](/windows/desktop/gdi/colorref) hodnoty. Obsahuje aktuálně dostupných barev.|
|`m_lstDocColors`|A [CList –](../../mfc/reference/clist-class.md) z [COLORREF](/windows/desktop/gdi/colorref) hodnoty. Obsahuje aktuální barvy dokumentu.|
|`m_nColumns`|Celé číslo. Obsahuje číslo sloupce, které chcete zobrazit v mřížce barvy v nabídce pro výběr barvy.|
|`m_pPalette`|Ukazatel [cpalette –](../../mfc/reference/cpalette-class.md). Obsahuje barvy, které jsou k dispozici v aktuální nabídce pro výběr barvy.|
|`m_pPopup`|Ukazatel [cmfccolorpopupmenu – třída](../../mfc/reference/cmfccolorpopupmenu-class.md) objektu. Nabídce pro výběr barev, které se zobrazí, když kliknete na tlačítko barvy.|
|`m_strAutoColorText`|Řetězec. Popisek tlačítka "automatické" v nabídce pro výběr barvy.|
|`m_strDocColorsText`|Řetězec. Popisek tlačítka v nabídce pro výběr barvy, který zobrazuje barvy dokumentu.|
|`m_strOtherText`|Řetězec. Popisek tlačítka "other" v nabídce pro výběr barvy.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CMFCColorButton` třídy se chová jako příkazové tlačítko, které se otevře dialogové okno Výběr barvy. Dialogové okno Výběr barvy obsahuje celou řadu malých barvy tlačítka a "other" tlačítka, která zobrazuje ovládacího prvku pro výběr vlastních barev. (Standardní systém je označené jako "other" tlačítko **Další barvy**.) Když uživatel vybere novou barvu `CMFCColorButton` objekt odráží změnu a zobrazí vybranou barvu.

Vytvoření ovládacího prvku tlačítko barvy přímo v kódu nebo s použitím **ClassWizard** nástroje a šablony dialogového okna. Pokud vytvoříte ovládací prvek tlačítko barvy přímo, přidejte `CMFCColorButton` proměnnou pro svoji aplikaci a pak volání konstruktoru a `Create` metody `CMFCColorButton` objektu. Pokud používáte **ClassWizard**, přidejte `CButton` proměnné pro vaši aplikaci a poté změňte typ proměnné z `CButton` k `CMFCColorButton`.

Dialogové okno Výběr barvy ( [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md)) se zobrazí [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metody při volání rozhraní `OnLButtonDown` obslužné rutiny události. [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metoda může být potlačena za účelem podporují výběr vlastní barvy.

`CMFCColorButton` Jeho nadřazený objekt, který se barva mění a odeslat ho wm_command – upozorní objekt | BN_CLICKED oznámení. Používá nadřazené [CMFCColorButton::GetColor](#getcolor) metody k získání aktuální barvu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat pomocí různých metod v barevné tlačítko `CMFCColorButton` třídy. Metody, nastavit barvu bude tlačítko barev a jeho počet sloupců a povolit automatické a další tlačítka. V tomto příkladu je součástí [stav panelu demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorbutton.h

##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton

Sestaví nový `CMFCColorButton` objektu.

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

Povolit nebo zakázat "automatické" tlačítko u ovládacího prvku pro výběr barev a nastavit barvu automaticky (výchozí).

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Určuje text, bude automatické tlačítka.

*colorAutomatic*<br/>
[in] Hodnota RGB, která určuje výchozí barvu automatického tlačítka.

*bEnable*<br/>
[in] Určuje, zda je povoleno automatické tlačítko.

### <a name="remarks"></a>Poznámky

##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton

Povolí nebo zakáže "other" tlačítko, které se zobrazí pod regulární barvy tlačítka.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Určuje text tlačítka.

*bAltColorDlg*<br/>
[in] Určuje, zda [cmfccolordialog –](../../mfc/reference/cmfccolordialog-class.md) dialogové okno nebo dialogové okno barev systému se otevře, když uživatel klikne na tlačítko.

*bEnable*<br/>
[in] Určuje, zda je povoleno tlačítko "other".

### <a name="remarks"></a>Poznámky

Klikněte na tlačítko "other" zobrazíte dialogové okno barvy. Pokud *bAltColorDlg* parametr má hodnotu TRUE, [cmfccolordialog – třída](../../mfc/reference/cmfccolordialog-class.md) se zobrazí; v opačném případě se zobrazí dialogové okno barev systému.

##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor

Načte aktuální barvu automaticky (výchozí).

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB představující aktuální Automatická barva.

### <a name="remarks"></a>Poznámky

Aktuální Automatická barva se nastavil [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) metody.

##  <a name="getcolor"></a>  CMFCColorButton::GetColor

Načte aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB.

### <a name="remarks"></a>Poznámky

##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme

Určuje, zda aktuální barva – tlačítko se zobrazí v vizuálního stylu Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou vizuální styly podporovány a aktuální barva – tlačítko se zobrazí v vizuálního stylu Windows XP. v opačném případě hodnota FALSE.

##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode

Nastaví barevné tlačítko pro režim úprav.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Poznámky

Pokud je potřeba přidat na stránku dialogové okno přizpůsobení barevné tlačítko (nebo povolte uživatele, aby jiný výběr barvy během přizpůsobování), povolit tlačítko tak, že nastavíte `m_bEnabledInCustomizeMode` člena na hodnotu TRUE. Ve výchozím nastavení je tento člen nastaven na hodnotu FALSE.

##  <a name="ondraw"></a>  CMFCColorButton::OnDraw

Volá se rozhraním, aby se vykreslil obraz tlačítka.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Odkazuje na kontext zařízení, která se použije k vykreslení obrázku tlačítku.

*Rect*<br/>
[in] Obdélník, který vazeb na tlačítko.

*uiState*<br/>
[in] Určuje vizuální stav tlačítka.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu za účelem přizpůsobení samotný proces vykreslování.

##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder

Volá se rozhraním, aby zobrazte ohraničení tlačítka.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Odkazuje na zařízení kontext použitý k vykreslení ohraničení.

*rectClient*<br/>
[in] Obdélník v kontextu zařízení, která je zadána *primárního řadiče domény* parametr, který definuje hranice tlačítko, které chcete kreslit.

*uiState*<br/>
[in] Určuje vizuální stav tlačítka.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci pro přizpůsobení vzhledu ohraničení bude tlačítko barev.

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

Volá se rozhraním, když je fokus na tlačítko Zobrazit rámečku fokusu.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Odkazuje na kontext zařízení pro kreslení obdélníku fokusu.

*rectClient*<br/>
[in] Obdélník v kontextu zařízení určeného *primárního řadiče domény* parametr, který definuje hranice tlačítka.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu za účelem přizpůsobení vzhledu rámečku fokusu.

##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup

Volá se před zobrazením automaticky otevíraný panel barev.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Poznámky

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

Inicializuje `m_pPalette` chráněný datový člen paletě zadaný nebo výchozí systémové palety.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pPal*|[in] Ukazatel na logickou paletu nebo hodnota NULL. Pokud má hodnotu NULL, použije se výchozí systémové palety.|

##  <a name="setcolor"></a>  CMFCColorButton::SetColor

Určuje barvu tlačítka.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Hodnota RGB.

### <a name="remarks"></a>Poznámky

##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName

Určuje název barvy.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Hodnota barvy RGB.

*strName*<br/>
[in] Název barvy.

### <a name="remarks"></a>Poznámky

Seznam s názvy barev je globální na aplikaci. V důsledku toho tato metoda převede její parametry [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber

Definuje počet sloupců, které jsou zobrazeny v tabulce barev, která se zobrazí uživateli při výběru barvy uživatele.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nColumns*<br/>
[in] Určuje počet sloupců.

### <a name="remarks"></a>Poznámky

Uživatel může vybrat barvu z nabídky panelu barev, které zobrazí tabulku předdefinované barvy. Tuto metodu použijte k definování počet sloupců v tabulce.

##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors

Určuje sadu barev a název v sadě. Sada barev se zobrazí pomocí [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md) objektu.

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Určuje popisek, který se má zobrazit sadu barvy dokumentu.

*lstColors*<br/>
[in] Odkaz na seznam hodnoty RGB.

### <a name="remarks"></a>Poznámky

A `CMFCColorButton` objektu udržuje seznam hodnoty RGB, které jsou předány [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md) objektu. Když se zobrazí na panelu barev, tyto barvy jsou uvedeny v speciální oddíl, jehož popisek je určená *lpszLabel* parametru.

##  <a name="setpalette"></a>  CMFCColorButton::SetPalette

Určuje standardní barvy se zobrazí na automaticky otevíraný panel barev.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette*<br/>
[in] Ukazatel na paletu barev.

### <a name="remarks"></a>Poznámky

##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent

Změní velikost ovládacího prvku tlačítka podle jeho textu a obrázků.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[in] Pokud nenulovou hodnotu, nová velikost ovládacího prvku tlačítka se počítá, ale skutečná velikost se nemění.

### <a name="return-value"></a>Návratová hodnota

A `CSize` objekt, který určuje novou velikost ovládacího prvku tlačítko.

### <a name="remarks"></a>Poznámky

##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor

Volá se rozhraním, když uživatel vybere barvu z barevného pruhu, který se zobrazí, když uživatel klikne na tlačítko barvy.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Barva vybraná uživatelem.

### <a name="remarks"></a>Poznámky

`UpdateColor` Funkce změní barvu vybraného tlačítka a odesláním wm_command – zprávy s oznámením standardní BN_CLICKED upozorní svého nadřazeného objektu. Použití [CMFCColorButton::GetColor](#getcolor) metodu pro načtení vybraných barev.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/desktop/gdi/colorref)<br/>
[CPalette – třída](../../mfc/reference/cpalette-class.md)<br/>
[CArray – třída](../../mfc/reference/carray-class.md)<br/>
[CList – třída](../../mfc/reference/clist-class.md)<br/>
[CString –](../../atl-mfc-shared/reference/cstringt-class.md)
