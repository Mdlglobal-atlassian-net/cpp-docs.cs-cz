---
title: CMFCColorMenuButton – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 22208aec505033d372f5a80ba2a9641b1bd15874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367706"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton – třída

Třída `CMFCColorMenuButton` podporuje příkaz nabídky nebo tlačítko panelu nástrojů, které spustí dialogové okno pro výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Vytvoří `CMFCColorMenuButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí a zakáže "automatické" tlačítko, které je umístěno nad běžnými barevnými tlačítky. (Standardní automatické tlačítko systému je označeno **automaticky**.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Umožňuje zobrazení barev specifických pro dokument namísto systémových barev.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Povolí a zakáže tlačítko "ostatní", které je umístěno pod běžnými barevnými tlačítky. (Standardní systémové tlačítko "ostatní" je označeno **více barev**.)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Umožňuje odtrhnout podokno barev.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální automatickou barvu.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Načte barvu aktuálního tlačítka.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Načte barvu, která odpovídá zadanému ID příkazu.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Volat rámci při změně nadřazeného okna.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Otevře dialogové okno pro výběr barvy.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Nastaví barvu aktuálního tlačítka barvy.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Nastaví barvu zadaného tlačítka nabídky barvy.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Nastaví nový název pro zadanou barvu.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců, které `CMFCColorBar` jsou zobrazeny objektem.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Zkopíruje jiné tlačítko panelu nástrojů na aktuální tlačítko.|
|[CMFCColorMenuButton::Nabídka CreatePopupMenu](#createpopupmenu)|Vytvoří dialogové okno pro výběr barvy.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Označuje, zda jsou podporovány prázdné nabídky.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Volat rámci pro zobrazení obrázku na tlačítko.|
|[CMFCColorMenuButton::OndrawOnCustomizeList](#ondrawoncustomizelist)|Volat rámci před `CMFCColorMenuButton` objekt se zobrazí v seznamu panelu nástrojů přizpůsobení dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li nahradit původní příkaz nabídky `CMFCColorMenuButton` nebo tlačítko `CMFCColorMenuButton` panelu nástrojů objektem, vytvořte objekt, nastavte `ReplaceButton` všechny příslušné styly [třídy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) a pak zavolejte metodu [třídy CMFCToolBar.](../../mfc/reference/cmfctoolbar-class.md) Pokud upravujete panel nástrojů, zavolejte metodu [CMFCToolBarsCustomizeDialog::ReplaceButton.](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)

Dialogové okno pro výběr barvy je vytvořeno během zpracování obslužné rutiny události [CMFCColorMenuButton::CreatePopupMenu.](#createpopupmenu) Obslužná rutina události upozorní nadřazený rámec zprávou WM_COMMAND. Objekt `CMFCColorMenuButton` odešle ID ovládacího prvku, které je přiřazeno k původnímu příkazu nabídky nebo tlačítku panelu nástrojů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit a nakonfigurovat tlačítko nabídky `CMFCColorMenuButton` barev pomocí různých metod ve třídě. V příkladu `CPalette` je objekt nejprve vytvořen a poté `CMFCColorMenuButton` použit k vytvoření objektu třídy. Objekt `CMFCColorMenuButton` je pak nakonfigurován povolením jeho automatické a další tlačítka a nastavení jeho barvu a počet sloupců. Tento kód je součástí [ukázky wordpadu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[Tlačítko CMFCColorMenu](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolormenubutton.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton

Vytvoří `CMFCColorMenuButton` objekt.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[v] ID příkazu tlačítka.

*lpszText*<br/>
[v] Text tlačítka.

*pPaleta*<br/>
[v] Ukazatel na paletu barev tlačítka.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

První konstruktor je výchozí konstruktor. Aktuální barva objektu a automatická barva jsou inicializovány na černou (RGB(0, 0, 0)).

Druhý konstruktor inicializuje tlačítko na barvu, která odpovídá zadanému ID příkazu.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom

Zkopíruje jeden objekt [cmfctoolbarmenubutton třídy](../../mfc/reference/cmfctoolbarmenubutton-class.md)odvozené do jiného.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Zdrojové tlačítko ke kopírování.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu kopírovat objekty, `CMFCColorMenuButton` které jsou odvozeny od objektu.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCColorMenuButton::Nabídka CreatePopupMenu

Vytvoří dialogové okno pro výběr barvy.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, který představuje dialogové okno pro výběr barvy.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci, když uživatel stiskne tlačítko nabídky barev.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton

Povolí a zakáže "automatické" tlačítko, které je umístěno nad běžnými barevnými tlačítky. (Standardní automatické tlačítko systému je označeno **automaticky**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Určuje text tlačítka, který se zobrazí, když se tlačítko stane automatickým.

*colorAutomaticky*<br/>
[v] Určuje novou automatickou barvu.

*bEnable*<br/>
[v] Určuje, zda je tlačítko automatické nebo ne.

### <a name="remarks"></a>Poznámky

Automatické tlačítko aplikuje aktuální výchozí barvu.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors

Umožňuje zobrazení barev specifických pro dokument namísto systémových barev.

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Určuje text tlačítka.

*bEnable*<br/>
[v] PRAVDA pro zobrazení barev specifických pro dokument nebo FALSE pro zobrazení systémových barev.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k zobrazení aktuálních barev dokumentu nebo barev systémové palety, když uživatel klepne na tlačítko nabídky barev.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton

Povolí a zakáže tlačítko "ostatní", které je umístěno pod běžnými barevnými tlačítky. (Standardní systémové tlačítko "ostatní" je označeno **více barev**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Určuje text tlačítka.

*bAltColorDlg*<br/>
[v] Určete hodnotu `CMFCColorDialog` TRUE, chcete-li zobrazit dialogové okno, nebo NEPRAVDA, chcete-li zobrazit dialogové okno se standardními barvami systému.

*bEnable*<br/>
[v] Zadejte hodnotu TRUE, chcete-li zobrazit tlačítko "ostatní"; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff

Umožňuje odtrhnout podokno barev.

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] Určuje ID podokna odtržení.

*nVertDockColumns*<br/>
[v] Určuje počet sloupců ve svisle ukotveném barevném podokně ve stavu odtržení.

*nHorzDockRows*<br/>
[v] Určuje počet řádků pro vodorovně ukotvené podokno barev v odtrhnutém stavu.

### <a name="remarks"></a>Poznámky

Volání této metody povolit "odtržení" funkce pro podokno barev, která se objeví při stisknutí `CMFCColorMenuButton` tlačítka.

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor

Načte aktuální automatickou barvu.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB, která představuje aktuální automatickou barvu.

### <a name="remarks"></a>Poznámky

Volání této metody získat automatickou barvu, která je nastavena [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColorMenuButton::GetColor

Načte barvu aktuálního tlačítka.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva tlačítka.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID

Načte barvu, která odpovídá zadanému ID příkazu.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[v] ID příkazu.

### <a name="return-value"></a>Návratová hodnota

Barva, která odpovídá zadanému ID příkazu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud máte v aplikaci několik barevných tlačítek. Když uživatel klepne na tlačítko barva, tlačítko odešle jeho ID příkazu v WM_COMMAND zprávu nadřazené zprávě. Metoda `GetColorByCmdID` používá ID příkazu k načtení odpovídající barvy.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed

Označuje, zda jsou podporovány prázdné nabídky.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou povoleny prázdné nabídky; jinak nula.

### <a name="remarks"></a>Poznámky

Prázdné nabídky jsou ve výchozím nastavení podporovány. Přepsat tuto metodu změnit toto chování v odvozené třídě.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd

Volat rámci při změně nadřazeného okna.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nové nadřazené okno.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColorMenuButton::OnDraw

Volat rámci pro zobrazení obrázku na tlačítko.

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

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Obdélník, který ohraničuje oblast, která má být překreslena.

*pObrázky*<br/>
[v] Odkazuje na seznam obrázků panelu nástrojů.

*bHorz*<br/>
[v] TRUE, chcete-li určit, že panel nástrojů je v vodorovném ukotveném stavu; jinak NEPRAVDA. Výchozí hodnota je TRUE.

*bPřizpůsobitrežim*<br/>
[v] TRUE určit, že aplikace je v režimu přizpůsobení; jinak NEPRAVDA. Výchozí hodnota je FALSE.

*bZvýraznění*<br/>
[v] TRUE, chcete-li určit, že tlačítko je zvýrazněno; jinak NEPRAVDA. Výchozí hodnota je FALSE.

*bDrawBorder*<br/>
[v] TRUE, chcete-li určit, že se zobrazí ohraničení tlačítka; jinak NEPRAVDA. Výchozí hodnota je TRUE.

*bGrayDisabledTlačítka*<br/>
[v] TRUE, chcete-li určit, že zakázaná tlačítka jsou šedě (ztlumená) ven; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OndrawOnCustomizeList

Volat rámci před `CMFCColorMenuButton` objekt se zobrazí v seznamu panelu nástrojů přizpůsobení dialogového okna.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Obdélník, který ohraničuje tlačítko, které má být nakresleno.

*bVybrané*<br/>
[v] TRUE určuje, že tlačítko je ve vybraném stavu; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

Šířka tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda je volána `CMFCColorMenuButton` rámci při objektu se zobrazí v seznamu během procesu přizpůsobení panelu nástrojů.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog

Otevře dialogové okno pro výběr barvy.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
[v] Výchozí barva, která je vybraná v dialogovém okně barva.

*colorRes*<br/>
[out] Vrátí barvu, kterou uživatel vybere z dialogového okna barva.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel vybere novou barvu; jinak nula.

### <a name="remarks"></a>Poznámky

Po klepnutí na tlačítko nabídky voláním této metody otevřete dialogové okno barev. Pokud je vrácená hodnota nenulová, barva, kterou uživatel vybere, je uložena v parametru *colorRes.* Pomocí metody [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) přepínejte mezi standardním barevným dialogem a dialogem [Třída CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md)

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColorMenuButton::SetColor

Nastaví barvu aktuálního tlačítka barvy.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
[v] Hodnota barvy RGB.

*bUpozornit*<br/>
[v] TRUE pro aplikování barvy parametru *clr* na libovolné přidružené tlačítko nabídky nebo tlačítko panelu nástrojů; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Volánítéto metody změnit barvu aktuálního tlačítka barvy. Pokud je parametr *bNotify* nenulový, změní se barva odpovídajícího tlačítka v libovolné přidružené místní nabídce nebo panelu nástrojů na barvu určenou parametrem *clr.*

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID

Nastaví barvu zadaného tlačítka nabídky barvy.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[v] ID prostředku tlačítka nabídky barev.

*color*<br/>
[v] Hodnota barvy RGB.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorMenuButton::SetColorName

Nastaví nový název pro zadanou barvu.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota RGB barvy, jejíž název se změní.

*strName*<br/>
[v] Nový název barvy.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber

Nastaví počet sloupců, které se mají zobrazit v ovládacím prvku výběru barev (objekt [CMFCColorBar).](../../mfc/reference/cmfccolorbar-class.md)

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parametry

*nSloupce*<br/>
[v] Počet sloupců, které chcete zobrazit.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton – třída](../../mfc/reference/cmfccolorbutton-class.md)
