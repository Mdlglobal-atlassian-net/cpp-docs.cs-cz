---
title: Cmfccolormenubutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f307a5c0d1c1666c4d8a016496d9a6bf717c6d48
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083008"
---
# <a name="cmfccolormenubutton-class"></a>Cmfccolormenubutton – třída

`CMFCColorMenuButton` Třída podporuje příkaz nabídky nebo tlačítko panelu nástrojů, které spustí dialogové okno Výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Vytvoří `CMFCColorMenuButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí nebo zakáže "automatické" tlačítko, které je umístěn nad regulární barvy tlačítka. (Standardní systém automatické tlačítko má název **automatické**.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Umožňuje zobrazovat konkrétní dokumenty barvy místo systémových barev.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže "other" tlačítko, který je umístěn pod regulární barvy tlačítka. (Standardní systém je označené jako "other" tlačítko **Další barvy**.)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Umožňuje odtrhnout podokno Barva.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální Automatická barva.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Načte aktuální tlačítko barvy.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Zjišťuje barvu, která odpovídá ID zadaného příkazu.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Volá se rozhraním, když se změní nadřazeného okna.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Otevře se dialogové okno Výběr barvy.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Nastavuje barvu aktuální barva – tlačítko.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Nastavuje barvu zadaná barva tlačítek nabídky.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Nastaví nový název pro zadanou barvu.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců, které jsou zobrazeny `CMFCColorBar` objektu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Zkopíruje jiné tlačítko panelu nástrojů na tlačítko aktuální.|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Vytvoří dialogové okno Výběr barvy.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Označuje, zda jsou prázdné nabídky.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Volá se rozhraním, aby zobrazení obrázku na tlačítku.|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Volá se rozhraním před `CMFCColorMenuButton` objektu se zobrazí v seznamu dialogového okna úpravy panelu nástrojů.|

## <a name="remarks"></a>Poznámky

Nahradit původní příkaz nabídky nebo panelu nástrojů tlačítko s `CMFCColorMenuButton` objektu, vytvořte `CMFCColorMenuButton` objektu, nastavit všechny příslušné [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md) styly a poté zavolejte `ReplaceButton` metoda [Cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md) třídy. Pokud si přizpůsobit panel nástrojů, zavolejte [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) metody.

Dialogové okno Výběr barvy se vytvoří během zpracování [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) obslužné rutiny události. Obslužná rutina události upozorní zprávou wm_command – nadřazeného rámce. `CMFCColorMenuButton` Objekt odesílá ID ovládacího prvku, který je přiřazen k původní příkaz nabídky nebo panelu nástrojů tlačítko.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit a nakonfigurovat pomocí různých metod v barva tlačítek nabídky `CMFCColorMenuButton` třídy. V příkladu `CPalette` objektu se nejprve vytvoří a použije k vytvoření objektu `CMFCColorMenuButton` třídy. `CMFCColorMenuButton` Objektu je nakonfigurovaný tak, že povolit jeho automatické a další tlačítka a nastavení jeho barvu a počet sloupců. Tento kód je součástí [slovo panel vzorku](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton –](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfctoolbarmenubutton –](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[Cmfccolormenubutton –](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolormenubutton.h

##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton

Vytvoří `CMFCColorMenuButton` objektu.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] Identifikátor příkazu tlačítka

*lpszText*<br/>
[in] Text tlačítka.

*pPalette*<br/>
[in] Ukazatel na tlačítko palety barev.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

První konstruktor je výchozí konstruktor. Aktuální barva objektu a Automatická barva jsou inicializovány na černé (RGB (0, 0, 0)).

Druhý konstruktor inicializuje tlačítka barvu, která odpovídá ID zadaného příkazu.

##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom

Kopíruje jeden [cmfctoolbarmenubutton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md)-odvozenému objektu na jiný.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Tlačítko Zdroj kopírování.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu za účelem kopírování objektů, které jsou odvozeny z `CMFCColorMenuButton` objektu.

##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu

Vytvoří dialogové okno Výběr barvy.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, který představuje dialogové okno Výběr barvy.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když uživatel stiskne barva tlačítek nabídky.

##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton

Povolí nebo zakáže "automatické" tlačítko, které je umístěn nad regulární barvy tlačítka. (Standardní systém automatické tlačítko má název **automatické**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Určuje text tlačítka, který se zobrazí, když bude automatické tlačítka.

*barvaAutomatická*<br/>
[in] Určuje barvu automatického nové.

*bEnable*<br/>
[in] Určuje, zda je tlačítko Automatické.

### <a name="remarks"></a>Poznámky

Automatické tlačítko použije aktuální výchozí barvu.

##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors

Umožňuje zobrazovat konkrétní dokumenty barvy místo systémových barev.

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Určuje text tlačítka.

*bEnable*<br/>
[in] TRUE, pokud chcete zobrazit konkrétní dokumenty barvy nebo FALSE pro zobrazení systémových barev.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete zobrazit aktuální barvy dokumentu nebo systémové barvy palety, když uživatel klikne na tlačítko nabídky barvu.

##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton

Povolí nebo zakáže "other" tlačítko, který je umístěn pod regulární barvy tlačítka. (Standardní systém je označené jako "other" tlačítko **Další barvy**.)

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
[in] Zadejte hodnotu TRUE pro zobrazení `CMFCColorDialog` dialogového okna, nebo hodnotu FALSE, chcete-li zobrazit dialogové okno Barva standardní systém.

*bEnable*<br/>
[in] Zadejte TRUE, pokud chcete zobrazit tlačítko "other"; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff

Umožňuje odtrhnout podokno Barva.

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Určuje ID pro podokno odnímatelnými nabídkami.

*nVertDockColumns*<br/>
[in] Určuje počet sloupců v podokně svisle barva ve stavu odnímatelnými nabídkami.

*nHorzDockRows*<br/>
[in] Určuje počet řádků pro podokna vodorovně ukotvené barva ve stavu odnímatelnými nabídkami.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem povolení této funkce "odtržených" pro podokno barvu, která se zobrazí, když `CMFCColorMenuButton` stisknutí tlačítka.

##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor

Načte aktuální Automatická barva.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB, který představuje aktuální Automatická barva.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem získání Automatická barva, která nastavuje [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).

##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor

Načte aktuální tlačítko barvy.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva tlačítka.

### <a name="remarks"></a>Poznámky

##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID

Zjišťuje barvu, která odpovídá ID zadaného příkazu.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] ID příkazu.

### <a name="return-value"></a>Návratová hodnota

Barva, která odpovídá ID zadaného příkazu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud máte několik barvu tlačítka v aplikaci. Když uživatel klikne na tlačítko barvy, na tlačítko odešle jeho ID příkazu wm_command – zprávy k nadřazené úloze. `GetColorByCmdID` Metoda používá ID příkazu, který Pokud chcete načíst barvu odpovídající.

##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed

Označuje, zda jsou prázdné nabídky.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou povoleny prázdné nabídky. jinak, nula.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou podporovány prázdné nabídky. Potlačí tuto metodu ke změně tohoto chování v odvozené třídě.

##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd

Volá se rozhraním, když se změní nadřazeného okna.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Ukazatel do nového nadřazeného okna.

### <a name="remarks"></a>Poznámky

##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw

Volá se rozhraním, aby zobrazení obrázku na tlačítku.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Obdélník, který oblasti, ke které se měl překreslit za rozsahem.

*pImages*<br/>
[in] Odkazuje na seznam obrázků panelu nástrojů.

*bHorz*<br/>
[in] TRUE, pokud chcete určit, že panelu nástrojů v vodorovné ukotvených stavu; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

*bCustomizeMode*<br/>
[in] TRUE, pokud chcete určit, že aplikace je v režimu úprav. v opačném případě hodnota FALSE. Výchozí hodnota je FALSE.

*bHighlight*<br/>
[in] TRUE, pokud chcete určit, že tlačítko bude zvýrazněný. v opačném případě hodnota FALSE. Výchozí hodnota je FALSE.

*bDrawBorder*<br/>
[in] TRUE, pokud chcete určit, že se zobrazí okraj tlačítka. v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

*bGrayDisabledButtons*<br/>
[in] TRUE, pokud chcete určit, že jsou zakázané tlačítka šedým (neaktivní) v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList

Volá se rozhraním před `CMFCColorMenuButton` objektu se zobrazí v seznamu dialogového okna úpravy panelu nástrojů.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Obdélník, který za rozsahem tlačítko, které chcete kreslit.

*bSelected*<br/>
[in] Hodnota TRUE Určuje, že je tlačítko ve vybraném stavu; v opačném případě hodnota FALSE.

### <a name="return-value"></a>Návratová hodnota

Šířka tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když `CMFCColorMenuButton` objektu se zobrazí v seznamu během procesu přizpůsobení panelu nástrojů.

##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog

Otevře se dialogové okno Výběr barvy.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
[in] Výchozí barva, která je vybrána v dialogovém okně barev.

*colorRes*<br/>
[out] Vrátí barvu, kterou uživatel vybere v dialogovém okně barev.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel vybere novou barvu. jinak, nula.

### <a name="remarks"></a>Poznámky

Po kliknutí na tlačítko nabídky volejte tuto metodu za účelem otevřete dialogové okno barvy. Pokud vrácená hodnota je nenulový, barva, kterou uživatel vybere je uložen v *colorRes* parametru. Použití [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) metoda přepínat mezi standardní barvu dialogových oken a [cmfccolordialog – třída](../../mfc/reference/cmfccolordialog-class.md) dialogové okno.

##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor

Nastavuje barvu aktuální barva – tlačítko.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
[in] Hodnota barvy RGB.

*bNotify*<br/>
[in] PRAVDA, pokud chcete použít *clr* parametr barva jakékoli přidružené nabídky nebo panelu nástrojů tlačítko; jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Voláním této metody lze změnit barvu aktuální barva – tlačítko. Pokud *bNotify* je parametr nenulovou hodnotu, se změní barvu na odpovídající tlačítko na jakékoli přidružené místní nabídky nebo panelu nástrojů na barva určená *clr* parametru.

##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID

Nastavuje barvu zadaná barva tlačítek nabídky.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] ID prostředku barva tlačítek nabídky.

*Barva*<br/>
[in] Hodnota barvy RGB.

##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName

Nastaví nový název pro zadanou barvu.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*Barva*<br/>
[in] Hodnota RGB barvy, jehož název se změní.

*%{strName/*<br/>
[in] Nový název barvy.

### <a name="remarks"></a>Poznámky

##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber

Nastaví počet sloupců na zobrazení v ovládacím prvku pro výběr barvy ( [cmfccolorbar –](../../mfc/reference/cmfccolorbar-class.md) objekt).

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nColumns*<br/>
[in] Počet zobrazovaných sloupců.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton – třída](../../mfc/reference/cmfccolorbutton-class.md)
