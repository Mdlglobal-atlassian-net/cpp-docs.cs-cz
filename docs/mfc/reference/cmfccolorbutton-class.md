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
ms.openlocfilehash: cf24c162d0eda272f73c69c434589ae6ef3332a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752558"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton – třída

Třídy `CMFCColorButton` tříd [y CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) se používají společně k implementaci ovládacího prvku pro výběr barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Vytvoří nový `CMFCColorButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí a zakáže "automatické" tlačítko, které je umístěno nad běžnými barevnými tlačítky. (Standardní automatické tlačítko systému je označeno **automaticky**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Povolí a zakáže tlačítko "ostatní", které je umístěno pod běžnými barevnými tlačítky. (Standardní systémové tlačítko "ostatní" je označeno **více barev**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální automatickou barvu.|
|[CMFCColorButton::GetColor](#getcolor)|Načte barvu tlačítka.|
|[CMFCColorButton::SetColor](#setcolor)|Nastaví barvu tlačítka.|
|[CMFCColorButton::SetColorName](#setcolorname)|Nastaví název barvy.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců v dialogovém okně výběru barev.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam barev specifických pro dokument, které jsou zobrazeny v dialogovém okně pro výběr barvy.|
|[CMFCColorButton::SetPalette](#setpalette)|Určuje paletu standardních barev zobrazení.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Změní velikost ovládacího prvku tlačítka v závislosti na jeho textu a velikosti obrázku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Označuje, zda je aktuální tlačítko barvy zobrazeno ve vizuálním stylu systému Windows XP.|
|[CMFCColorButton::Ondraw](#ondraw)|Volat rámci zobrazit obrázek tlačítka.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Volat rámci pro zobrazení ohraničení tlačítka.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Volat rámci zobrazit obdélník fokus, když má fokus.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Volat rámci při dialogovém okně výběru barev se chystá zobrazit.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializuje `m_pPalette` chráněný datový člen na zadanou paletu nebo výchozí systémovou paletu.|
|[CMFCColorButton::Aktualizovat barvu](#updatecolor)|Volat rámci, když uživatel vybere barvu z palety dialogového okna výběr u barev.|

### <a name="data-members"></a>Členové dat

|Název|Popis|
|----------|-----------------|
|`m_bAltColorDlg`|Logická hodnota. Pokud true, rozhraní zobrazí dialogové okno barva [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) při klepnutí na *druhé* tlačítko, nebo pokud FALSE, dialogové okno barva systému. Výchozí hodnota je TRUE. Další informace naleznete v tématu [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Logická hodnota. Pokud TRUE, rozhraní nastaví fokus na nabídku barev při zobrazení nabídky, nebo pokud FALSE, nezmění fokus. Výchozí hodnota je TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Označuje, zda je pro tlačítko barva povolen režim přizpůsobení.|
|`m_Color`|[Colorref](/windows/win32/gdi/colorref) hodnota. Obsahuje aktuálně vybranou barvu.|
|`m_ColorAutomatic`|[Colorref](/windows/win32/gdi/colorref) hodnota. Obsahuje aktuálně vybranou výchozí barvu.|
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md) [colorref](/windows/win32/gdi/colorref) hodnoty. Obsahuje aktuálně dostupné barvy.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) [colorref](/windows/win32/gdi/colorref) hodnoty. Obsahuje aktuální barvy dokumentu.|
|`m_nColumns`|Celé číslo Obsahuje počet sloupců, které se mají zobrazit v mřížce barev v nabídce výběru barev.|
|`m_pPalette`|Ukazatel na [CPalette](../../mfc/reference/cpalette-class.md). Obsahuje barvy, které jsou k dispozici v aktuální nabídce výběru barev.|
|`m_pPopup`|Ukazatel na objekt [třídy CMFCColorPopupMenu.](../../mfc/reference/cmfccolorpopupmenu-class.md) Nabídka výběru barev, která se zobrazí po klepnutí na tlačítko Barva.|
|`m_strAutoColorText`|Řetězec. Popisek tlačítka "automatický" v nabídce výběru barev.|
|`m_strDocColorsText`|Řetězec. Popisek tlačítka v nabídce výběru barev, která zobrazuje barvy dokumentu.|
|`m_strOtherText`|Řetězec. Popisek tlačítka "ostatní" v nabídce výběru barev.|

## <a name="remarks"></a>Poznámky

Ve výchozím `CMFCColorButton` nastavení se třída chová jako tlačítko, které otevře dialogové okno pro výběr barvy. Dialogové okno pro výběr barvy obsahuje pole malých barevných tlačítek a tlačítko "jiné", které zobrazuje vlastní výběr barvy. (Standardní systémové tlačítko "ostatní" je označeno **více barev**.) Když uživatel vybere novou barvu, `CMFCColorButton` objekt odráží změnu a zobrazí vybranou barvu.

Vytvořte ovládací prvek tlačítka barvy buď přímo v kódu, nebo pomocí nástroje **ClassWizard** a šablony dialogového okna. Pokud vytvoříte ovládací prvek tlačítka `CMFCColorButton` barva přímo, přidejte proměnnou do `Create` aplikace `CMFCColorButton` a pak volání konstruktoru a metody objektu. Pokud používáte **ClassWizard**, `CButton` přidejte proměnnou do aplikace a změňte `CMFCColorButton`typ proměnné z na `CButton` .

Dialogové okno pro výběr barvy ( [TŘÍDA CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) je zobrazeno metodou [CMFCColorButton::OnShowColorPopup,](#onshowcolorpopup) když rozhraní nazývá obslužnou rutinu `OnLButtonDown` události. Metoda [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) může být přepsána pro podporu vlastního výběru barev.

Objekt `CMFCColorButton` upozorní nadřazenou barvu, že se mění barva, a to tak, že mu WM_COMMAND | BN_CLICKED oznámení. Nadřazený používá metodu [CMFCColorButton::GetColor](#getcolor) k načtení aktuální barvy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat tlačítko barvy pomocí `CMFCColorButton` různých metod ve třídě. Metody nastavují barvu tlačítka barva a jeho počet sloupců a povolují automatické a ostatní tlačítka. Tento příklad je součástí [ukázky ukázky stavového řádku](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorbutton.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

Vytvoří nový `CMFCColorButton` objekt.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton

Povolte nebo zakažte tlačítko "automatické" ovládacího prvku pro výběr barvy a nastavte automatickou (výchozí) barvu.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Určuje text automatického tlačítka.

*colorAutomaticky*<br/>
[v] Hodnota RGB, která určuje výchozí barvu automatického tlačítka.

*bEnable*<br/>
[v] Určuje, zda je automatické tlačítko povoleno nebo zakázáno.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

Povolte nebo zakažte tlačítko "ostatní", které se zobrazí pod běžnými barevnými tlačítky.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Určuje text tlačítka.

*bAltColorDlg*<br/>
[v] Určuje, zda je po klepnutí na tlačítko otevřeno dialogové okno [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) nebo dialogové okno barvy systému.

*bEnable*<br/>
[v] Určuje, zda je tlačítko "ostatní" povoleno nebo zakázáno.

### <a name="remarks"></a>Poznámky

Kliknutím na tlačítko "ostatní" zobrazíte dialogové okno barev. Pokud je parametr *bAltColorDlg* TRUE, zobrazí se [třída CMFCColorDialog;](../../mfc/reference/cmfccolordialog-class.md) v opačném případě se zobrazí dialogové okno barva systému.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

Načte aktuální automatickou (výchozí) barvu.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB představující aktuální automatickou barvu.

### <a name="remarks"></a>Poznámky

Aktuální automatická barva je nastavena metodou [CMFCColorButton::EnableAutomaticButton.](#enableautomaticbutton)

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFCColorButton::GetColor

Načte aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

Označuje, zda je aktuální tlačítko barvy zobrazeno ve vizuálním stylu systému Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou podporovány vizuální styly a aktuální tlačítko barvy se zobrazí ve vizuálním stylu systému Windows XP; jinak NEPRAVDA.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

Nastaví tlačítko barev do režimu přizpůsobení.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Poznámky

Pokud potřebujete přidat tlačítko barvy na stránku dialogového okna vlastního nastavení (nebo povolit uživateli provést `m_bEnabledInCustomizeMode` jiný výběr barev během vlastního nastavení), povolte tlačítko nastavením člena na HODNOTU TRUE. Ve výchozím nastavení je tento člen nastaven na hodnotu NEPRAVDA.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFCColorButton::Ondraw

Volat rámci k vykreslení obrázku tlačítka.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Odkazuje na kontext zařízení, který se používá k vykreslení obrázku tlačítka.

*Rect*<br/>
[v] Obdélník, který ohraničuje tlačítko.

*uiState*<br/>
[v] Určuje vizuální stav tlačítka.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu přizpůsobit proces vykreslování.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

Volat rámci pro zobrazení okraje tlačítka.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Odkazuje na kontext zařízení použitý k nakreslení ohraničení.

*rectClient*<br/>
[v] Obdélník v kontextu zařízení, který je určen parametrem *pDC,* který definuje hranice tlačítka, které má být nakresleno.

*uiState*<br/>
[v] Určuje vizuální stav tlačítka.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce přizpůsobíte vzhled ohraničení tlačítka barvy.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect

Volat rámci zobrazit obdélník fokus, když má fokus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Odkazuje na kontext zařízení použitý k nakreslení obdélníku fokusu.

*rectClient*<br/>
[v] Obdélník v kontextu zařízení určené parametrem *pDC,* který definuje hranice tlačítka.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu přizpůsobit vzhled obdélníku fokus.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

Volána před zobrazením vyskakovacího panelu barev.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette

Inicializuje `m_pPalette` chráněný datový člen na zadanou paletu nebo výchozí systémovou paletu.

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pPal*|[v] Ukazatel na logickou paletu nebo HODNOTU NULL. Pokud null, je použita výchozí systémová paleta.|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCColorButton::SetColor

Určuje barvu tlačítka.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorButton::SetColorName

Určuje název barvy.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota RGB barvy.

*strName*<br/>
[v] Název té barvy.

### <a name="remarks"></a>Poznámky

Seznam názvů barev je globální pro aplikaci. V důsledku toho tato metoda přenese své parametry na [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

Definuje počet sloupců, které jsou zobrazeny v tabulce barev, která je zobrazena uživateli během procesu výběru barev uživatele.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nSloupce*<br/>
[v] Určuje počet sloupců.

### <a name="remarks"></a>Poznámky

Uživatel může vybrat barvu z rozbalovacího panelu barev, který zobrazuje tabulku předdefinovaných barev. Tato metoda slouží k definování počtu sloupců v tabulce.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

Určuje sadu barev a název sady. Sada barev se zobrazí pomocí objektu [třídy CMFCColorBar.](../../mfc/reference/cmfccolorbar-class.md)

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Určuje popisek, který se má zobrazit se sadou barev dokumentu.

*lstBarvy*<br/>
[v] Odkaz na seznam hodnot RGB.

### <a name="remarks"></a>Poznámky

Objekt `CMFCColorButton` udržuje seznam hodnot RGB, které jsou přeneseny do objektu [třídy CMFCColorBar.](../../mfc/reference/cmfccolorbar-class.md) Když je zobrazen pruh barev, tyto barvy jsou zobrazeny ve speciální masce, jejíž popisek je určen parametrem *lpszLabel.*

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCColorButton::SetPalette

Určuje standardní barvy, které se mají zobrazit na vyskakovacím panelu barev.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPaleta*<br/>
[v] Ukazatel na paletu barev.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCColorButton::SizeToContent

Změní velikost ovládacího prvku tlačítka tak, aby odpovídal jeho textu a obrazu.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[v] Pokud je nenulová, vypočítá se nová velikost ovládacího prvku tlačítka, ale skutečná velikost se nezmění.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CSize` který určuje novou velikost ovládacího prvku tlačítka.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCColorButton::Aktualizovat barvu

Volat rámci, když uživatel vybere barvu z panelu barev, který se zobrazí, když uživatel klepne na tlačítko barva.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Barva vybraná uživatelem.

### <a name="remarks"></a>Poznámky

Funkce `UpdateColor` změní barvu aktuálně vybraného tlačítka a upozorní nadřazenou položku odesláním zprávy WM_COMMAND standardním oznámením BN_CLICKED. K načtení vybrané barvy použijte metodu [CMFCColorButton:::GetColor.](#getcolor)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)<br/>
[Třída CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette – třída](../../mfc/reference/cpalette-class.md)<br/>
[Třída CArray](../../mfc/reference/carray-class.md)<br/>
[CList – třída](../../mfc/reference/clist-class.md)<br/>
[Cstring](../../atl-mfc-shared/reference/cstringt-class.md)
