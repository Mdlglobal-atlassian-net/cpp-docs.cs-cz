---
title: CMFCColorButton – třída
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
ms.openlocfilehash: ac49957f075f8798607535286d6c4518c0eeeeae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505365"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton – třída

Třídy `CMFCColorButton` [třídy a CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) slouží společně k implementaci ovládacího prvku pro výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Vytvoří nový `CMFCColorButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí nebo zakáže tlačítko "automatické", které je umístěno nad běžnými barevnými tlačítky. (Standardní automatické tlačítko systému je označeno **automaticky**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Povoluje nebo zakazuje tlačítko "jiné", které je umístěno pod běžnými barevnými tlačítky. (Standardní systémové tlačítko "jiné" má označení **Další barvy**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální automatickou barvu.|
|[CMFCColorButton:: GetColor](#getcolor)|Načte barvu tlačítka.|
|[CMFCColorButton::SetColor](#setcolor)|Nastaví barvu tlačítka.|
|[CMFCColorButton::SetColorName](#setcolorname)|Nastaví název barvy.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců v dialogovém okně Výběr barvy.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam barev specifických pro dokument, které se zobrazí v dialogovém okně Výběr barvy.|
|[CMFCColorButton::SetPalette](#setpalette)|Určuje paletu standardních barev displeje.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Změní velikost ovládacího prvku tlačítko v závislosti na velikosti textu a obrázku.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Označuje, zda je aktuální tlačítko barvy zobrazeno ve stylu vizuálu systému Windows XP.|
|[CMFCColorButton:: Draw](#ondraw)|Volá se rozhraním, aby se zobrazila obrázek tlačítka.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Volá se rozhraním, aby se zobrazilo ohraničení tlačítka.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Volá se rozhraním, aby se zobrazil obdélník pro fokus, když má tlačítko fokus.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Volá se rozhraním, když se chystá zobrazení dialogového okna pro výběr barvy.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|`m_pPalette` Inicializuje chráněný datový člen na určenou paletě nebo výchozí systémovou paletu.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Volá se rozhraním, když uživatel vybere barvu z palety dialogového okna pro výběr barvy.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|`m_bAltColorDlg`|Logická hodnota. Pokud je nastaveno na TRUE, rozhraní zobrazí dialogové okno Barva [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) při kliknutí na *jiné* tlačítko, nebo v případě false, v dialogovém okně systémová barva. Výchozí hodnota je TRUE (pravda). Další informace najdete v tématu [CMFCColorButton:: EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Logická hodnota. Pokud je nastaveno na TRUE, rozhraní nastaví fokus v nabídce barva při zobrazení nabídky, nebo pokud má hodnotu FALSE, nezmění fokus. Výchozí hodnota je TRUE (pravda).|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Určuje, zda je pro tlačítko Barva povolen režim přizpůsobení.|
|`m_Color`|Hodnota [COLORREF](/windows/win32/gdi/colorref) Obsahuje aktuálně vybranou barvu.|
|`m_ColorAutomatic`|Hodnota [COLORREF](/windows/win32/gdi/colorref) Obsahuje aktuálně vybranou výchozí barvu.|
|`m_Colors`|[CArray –](../../mfc/reference/carray-class.md) hodnot [COLORREF](/windows/win32/gdi/colorref) . Obsahuje aktuálně dostupné barvy.|
|`m_lstDocColors`|[CList –](../../mfc/reference/clist-class.md) hodnot [COLORREF](/windows/win32/gdi/colorref) . Obsahuje aktuální barvy dokumentu.|
|`m_nColumns`|Celé číslo. Obsahuje počet sloupců, které se mají zobrazit v mřížce barev v nabídce výběru barvy.|
|`m_pPalette`|Ukazatel na [CPalette –](../../mfc/reference/cpalette-class.md). Obsahuje barvy, které jsou k dispozici v nabídce Výběr aktuální barvy.|
|`m_pPopup`|Ukazatel na objekt [třídy CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) . Nabídka výběru barvy, která se zobrazí po kliknutí na tlačítko barvy.|
|`m_strAutoColorText`|Řetězec. Popisek tlačítka pro automatické navýšení v nabídce výběru barvy.|
|`m_strDocColorsText`|Řetězec. Popisek tlačítka v nabídce výběru barvy, ve kterém se zobrazují barvy dokumentu|
|`m_strOtherText`|Řetězec. Popisek tlačítka jiné v nabídce výběru barvy.|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CMFCColorButton` se třída chová jako tlačítko push, které otevře dialogové okno Výběr barvy. Dialogové okno pro výběr barvy obsahuje pole malých barevných tlačítek a tlačítko "jiné", které zobrazuje vlastní výběr barvy. (Standardní systémové tlačítko "jiné" má označení **Další barvy**.) Když uživatel vybere novou barvu, `CMFCColorButton` objekt se projeví ve změně a zobrazí se vybraná barva.

Vytvořte ovládací prvek tlačítko barvy přímo v kódu nebo pomocí nástroje **ClassWizard** a šablony dialogového okna. Pokud vytvoříte ovládací prvek tlačítko barvy přímo, přidejte `CMFCColorButton` do aplikace proměnnou a potom zavolejte konstruktor a `Create` metody `CMFCColorButton` objektu. Použijete-li **ClassWizard**, přidejte `CButton` do aplikace proměnnou a poté změňte typ proměnné z `CButton` na `CMFCColorButton`.

Dialogové okno pro výběr barvy ( [Třída CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) se zobrazuje metodou [CMFCColorButton:: OnShowColorPopup](#onshowcolorpopup) , když `OnLButtonDown` rozhraní volá obslužnou rutinu události. Metoda [CMFCColorButton:: OnShowColorPopup](#onshowcolorpopup) může být přepsána tak, aby podporovala vlastní výběr barvy.

`CMFCColorButton` Objekt upozorní svůj nadřazený prvek o změnu barvy odesláním WM_COMMAND | Oznámení BN_CLICKED. Nadřazený objekt používá metodu [CMFCColorButton:: GetColor](#getcolor) k načtení aktuální barvy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak konfigurovat tlačítko barvy pomocí různých metod ve `CMFCColorButton` třídě. Metody nastaví barvu tlačítka barvy a jeho počtu sloupců a povolí automatické a další tlačítka. Tento příklad je součástí [ukázkové ukázky stavového řádku](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorbutton. h

##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

Vytvoří nový `CMFCColorButton` objekt.

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton

Povolí nebo zakáže tlačítko "automatické" v ovládacím prvku pro výběr barvy a nastaví automatickou (výchozí) barvu.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
pro Určuje text automatického tlačítka.

*colorAutomatic*<br/>
pro Hodnota RGB, která určuje výchozí barvu automatického tlačítka.

*bEnable*<br/>
pro Určuje, jestli je automatické tlačítko povolené nebo zakázané.

### <a name="remarks"></a>Poznámky

##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

Povolí nebo zakáže tlačítko jiné, které se zobrazí pod běžnými barevnými tlačítky.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
pro Určuje text tlačítka.

*bAltColorDlg*<br/>
pro Určuje, zda je dialogové okno [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) nebo dialogové okno systémová barva otevřeno, když uživatel klikne na tlačítko.

*bEnable*<br/>
pro Určuje, jestli je tlačítko jiné povolené nebo zakázané.

### <a name="remarks"></a>Poznámky

Kliknutím na tlačítko Další zobrazíte dialogové okno barvy. Pokud má parametr *bAltColorDlg* hodnotu true, zobrazí se [Třída CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ; v opačném případě se zobrazí dialogové okno systémová barva.

##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

Načte aktuální automatickou (výchozí) barvu.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB představující aktuální automatickou barvu.

### <a name="remarks"></a>Poznámky

Aktuální Automatická barva je nastavena metodou [CMFCColorButton:: EnableAutomaticButton](#enableautomaticbutton) .

##  <a name="getcolor"></a>CMFCColorButton:: GetColor

Načte aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB.

### <a name="remarks"></a>Poznámky

##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

Označuje, zda je aktuální tlačítko barvy zobrazeno ve stylu vizuálu systému Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou podporovány vizuální styly a že se aktuální tlačítko barvy zobrazuje ve stylu vizuálu systému Windows XP; v opačném případě FALSE.

##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

Nastaví tlačítko barvy na režim přizpůsobení.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Poznámky

Pokud potřebujete přidat tlačítko barev do stránky dialogového okna pro přizpůsobení (nebo povolit uživateli, aby během přizpůsobení provedl jiný výběr barvy), povolte tlačítko nastavením `m_bEnabledInCustomizeMode` člena na hodnotu true. Ve výchozím nastavení je tento člen nastaven na hodnotu FALSE.

##  <a name="ondraw"></a>CMFCColorButton:: Draw

Volá se rozhraním, aby se vykreslila image tlačítka.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Odkazuje na kontext zařízení, který se používá k vykreslení obrázku tlačítka.

*OBD*<br/>
pro Obdélník, který je ohraničený tlačítkem.

*uiState*<br/>
pro Určuje vizuální stav tlačítka.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu pro přizpůsobení procesu vykreslování.

##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

Volá se rozhraním, aby se zobrazilo ohraničení tlačítka.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Odkazuje na kontext zařízení použitý k vykreslení ohraničení.

*rectClient*<br/>
pro Rámeček v kontextu zařízení, který je určen parametrem *primárního řadiče domény* definující hranice tlačítka, které se má vykreslit.

*uiState*<br/>
pro Určuje vizuální stav tlačítka.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce upravíte vzhled ohraničení tlačítka barvy.

##  <a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect

Volá se rozhraním, aby se zobrazil obdélník pro fokus, když má tlačítko fokus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Odkazuje na kontext zařízení, který se používá k vykreslení obdélníku fokusu.

*rectClient*<br/>
pro Obdélník v kontextu zařízení určený parametrem *primárního řadiče domény* , který definuje hranice tlačítka.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete přizpůsobit vzhled obdélníku fokusu.

##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

Volá se před tím, než se zobrazí místní panel barev.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Poznámky

##  <a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette

`m_pPalette` Inicializuje chráněný datový člen na určenou paletě nebo výchozí systémovou paletu.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pPal*|pro Ukazatel na logickou paletu nebo hodnotu NULL. Pokud má hodnotu NULL, použije se výchozí Systémová paleta.|

##  <a name="setcolor"></a>CMFCColorButton::SetColor

Určuje barvu tlačítka.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
pro Hodnota RGB.

### <a name="remarks"></a>Poznámky

##  <a name="setcolorname"></a>CMFCColorButton::SetColorName

Určuje název barvy.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
pro Hodnota barvy RGB

*strName*<br/>
pro Název barvy

### <a name="remarks"></a>Poznámky

Seznam názvů barev je globální pro každou aplikaci. V důsledku toho tato metoda převede své parametry do [CMFCColorBar:: SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

Definuje počet sloupců, které jsou zobrazeny v tabulce barev, která je prezentována uživateli během procesu výběru barvy uživatele.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nColumns*<br/>
pro Určuje počet sloupců.

### <a name="remarks"></a>Poznámky

Uživatel může vybrat barvu z překryvného panelu barev, který zobrazuje tabulku předdefinovaných barev. Tuto metodu použijte k definování počtu sloupců v tabulce.

##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

Určuje sadu barev a název sady. Sada barev se zobrazí pomocí objektu [třídy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) .

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
pro Určuje popisek, který má být zobrazen se sadou barev dokumentu.

*lstColors*<br/>
pro Odkaz na seznam hodnot RGB.

### <a name="remarks"></a>Poznámky

Objekt udržuje seznam hodnot RGB, které jsou předány do objektu [třídy CMFCColorBar.](../../mfc/reference/cmfccolorbar-class.md) `CMFCColorButton` Po zobrazení pruhu barev se tyto barvy zobrazí ve speciálním oddílu, jehož jmenovka je určena parametrem *lpszLabel* .

##  <a name="setpalette"></a>CMFCColorButton::SetPalette

Určuje standardní barvy, které se mají zobrazit na panelu barev automaticky otevíraných oken.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette*<br/>
pro Ukazatel na paletu barev.

### <a name="remarks"></a>Poznámky

##  <a name="sizetocontent"></a>CMFCColorButton::SizeToContent

Změní velikost ovládacího prvku tlačítko tak, aby odpovídala jeho textu a obrázku.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
pro Pokud je hodnota nenulová, je vypočítána nová velikost ovládacího prvku tlačítko, ale skutečná velikost se nemění.

### <a name="return-value"></a>Návratová hodnota

`CSize` Objekt, který určuje novou velikost ovládacího prvku tlačítka.

### <a name="remarks"></a>Poznámky

##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor

Volá se rozhraním, když uživatel vybere barvu z pruhu barev, který se zobrazí, když uživatel klikne na tlačítko Barva.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
pro Barva vybraná uživatelem

### <a name="remarks"></a>Poznámky

`UpdateColor` Funkce změní barvu aktuálně vybraného tlačítka a upozorní své nadřazené položky odesláním zprávy WM_COMMAND pomocí oznámení BN_CLICKED Standard. Pro načtení vybrané barvy použijte metodu [CMFCColorButton:: GetColor](#getcolor) .

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette – třída](../../mfc/reference/cpalette-class.md)<br/>
[CArray – třída](../../mfc/reference/carray-class.md)<br/>
[CList – třída](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
