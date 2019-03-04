---
title: Cmfccolorbar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: f1f7610fc315da65145798058fdcf9752e7873d0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283251"
---
# <a name="cmfccolorbar-class"></a>Cmfccolorbar – třída

`CMFCColorBar` Třída představuje dokovací panel ovládacího prvku, který umožňuje vybírat barvy v dokumentu nebo aplikace.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Vytvoří `CMFCColorBar` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Vypočítá vertikálním a horizontálním okraje, které jsou nutné tak, aby obsahovala tlačítek v ovládacím prvku pruhu barev a pak nastaví umístění těchto tlačítek.|
|[CMFCColorBar::CreateControl](#createcontrol)|Vytvoří okno Ovládací prvek pruhu barev, připojí se k `CMFCColorBar` objektu a změní velikost ovládacího prvku tak, aby obsahovala zadaný palety barev.|
|[CMFCColorBar::Create](#create)|Vytvoří okno ovládacího prvku pruhu barev a připojí ho k `CMFCColorBar` objektu.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Zobrazí nebo skryje automatické tlačítko.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže zobrazení dialogového okna, která umožňuje uživateli vybrat více barev.|
|[CMFCColorBar::GetColor](#getcolor)|Načte aktuálně vybranou barvu.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Načte Identifikátor příkazu aktuální ovládací prvek pruhu barev.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Zjišťuje barvu, která označuje, že barevné tlačítko má fokus; To znamená, tlačítko je *horké*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Získá vodorovný okraj je mezera mezi vlevo nebo pravá barva buněk a ohraničení oblasti klienta.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Získá svislý okraj, což je prostor mezi horní nebo dolní buňka barvu a ohraničení oblasti klienta.|
|[CMFCColorBar::IsTearOff](#istearoff)|Označuje, zda je aktuální pruhu barev ukotvit.|
|[CMFCColorBar::SetColor](#setcolor)|Nastaví barvu, která aktuálně není vybrán.|
|[CMFCColorBar::SetColorName](#setcolorname)|Nastaví nový název pro zadanou barvu.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Nastaví nový Identifikátor příkazu pro ovládací prvek pruhu barev.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Nastaví seznam barev, které se používají v aktuálním dokumentu.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Nastaví na vodorovný okraj je mezera mezi vlevo nebo pravá barva buněk a ohraničení oblasti klienta.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Nastaví na svislé okraj je mezera mezi horní nebo spodní buňce barvy a ohraničení oblasti klienta.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Upraví pozice barvu tlačítka v ovládacím prvku pruhu barev.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Označuje, zda lze změnit označení textového barvu tlačítka.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Označuje, zda lze během procesu přizpůsobení panelu nástrojů seznamu zobrazit objekt ovládacího prvku pruhu barev.|
|[CMFCColorBar::CalcSize](#calcsize)|Volá se rozhraním, jako součást procesu výpočet rozložení.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializuje barevnou paletu barev v určeném poli barvy.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Vypočítá počet řádků a sloupců v mřížce ovládací prvek pruhu barev.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Vypočítá dalších výška vyžadující aktuální panelu barev. Chcete-li zobrazit prvky různé uživatelského rozhraní, jako **jiných** tlačítko barvy dokumentu a tak dále.|
|[CMFCColorBar::InitColors](#initcolors)|Inicializuje pole barvy, barvy v paletu zadaný nebo výchozí palety systému.|
|[CMFCColorBar::OnKey](#onkey)|Volá se rozhraním, když uživatel stiskne tlačítko klávesnice.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Volá se rozhraním, zavřete hierarchii překryvných ovládacích prvků.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Volá se rozhraním, které chcete povolit nebo zakázat uživatelské rozhraní položky ovládacího prvku pruhu barev než položka je zobrazena.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Otevře se dialogové okno barvy.|
|[CMFCColorBar::Rebuild](#rebuild)|Zcela překreslí ovládací prvek pruhu barev.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Nastaví logickou paletu kontextu zadané zařízení na paletě tlačítko nadřazeného ovládacího prvku aktuální pruhu barev.|
|[CMFCColorBar::SetPropList](#setproplist)|Nastaví `m_pWndPropList` chráněný datový člen na zadaný ukazatel na ovládací prvek mřížky vlastností.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Požádá o okno rámce, který vlastní ovládací prvek pruhu barev k aktualizaci řádku zprávy ve stavovém řádku.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|`m_bInternal`|Logická pole, která určuje, zda se zpracovávají události myši. Události myši se zpracovávají obvykle, když toto pole je PRAVDA a režim úprav je FALSE.|
|`m_bIsEnabled`|Logická hodnota, která určuje, zda je ovládací prvek povolený.|
|`m_bIsTearOff`|Logická hodnota, která určuje, zda ovládací prvek pruhu barev podporuje ukotvení.|
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který určuje velikost buňky v mřížce pruhu barev.|
|`m_bShowDocColorsWhenDocked`|Logická hodnota, která určuje, jestli se má zobrazit barvy dokumentu, pokud je ukotven pruhu barev. Další informace najdete v tématu [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Logická hodnota, která určuje, jestli se má zobrazit dialogové okno Barva standardní systém nebo [cmfccolordialog –](../../mfc/reference/cmfccolordialog-class.md) dialogové okno. Další informace najdete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|A [COLORREF](/windows/desktop/gdi/colorref) , který ukládá aktuální Automatická barva. Další informace najdete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md) objekt, který přidruží sady RGB barvy s jejich názvy.|
|`m_colors`|A [carray –](../../mfc/reference/carray-class.md) z [COLORREF](/windows/desktop/gdi/colorref) hodnoty, které obsahuje barev, které jsou zobrazeny v ovládacím prvku pruhu barev.|
|`m_ColorSelected`|A [COLORREF](/windows/desktop/gdi/colorref) hodnotu barvy, který uživatel vybral aktuálně z ovládacího prvku pruhu barev.|
|`m_lstDocColors`|A [CList –](../../mfc/reference/clist-class.md) z [COLORREF](/windows/desktop/gdi/colorref) hodnoty, které obsahuje barvy, které jsou aktuálně používány v dokumentu.|
|`m_nCommandID`|Celé číslo bez znaménka, která je Identifikátor příkazu tlačítka barvu.|
|`m_nHorzMargin`|Celé číslo, které je vodorovný okraj mezi barvu tlačítka v tabulce barev.|
|`m_nHorzOffset`|Celé číslo, které je vodorovný posun do centra bude tlačítko barev. Tato hodnota je důležité, pokud na tomto tlačítku zobrazí text nebo obrázek kromě barvu.|
|`m_nNumColumns`|Celé číslo, které je počet sloupců v mřížce ovládací prvek barevného pruhu barev.|
|`m_nNumColumnsVert`|Celé číslo, které je počet sloupců v mřížce svisle orientovaný barev.|
|`m_nNumRowsHorz`|Celé číslo, které je počet sloupců v mřížce orientovaný vodorovně barev.|
|`m_nRowHeight`|Celé číslo, které má výšku řádku barvu tlačítka v tabulce barev.|
|`m_nVertMargin`|Celé číslo, které je svislý okraje mezi barvu tlačítka v tabulce barev.|
|`m_nVertOffset`|Celé číslo, které je svislý posun do centra bude tlačítko barev. Tato hodnota je důležité, pokud na tomto tlačítku zobrazí text nebo obrázek kromě barvu.|
|`m_Palette`|A [cpalette –](../../mfc/reference/cpalette-class.md) barev, které se používají v ovládacím prvku pruhu barev.|
|`m_pParentBtn`|Ukazatel [cmfccolorbutton –](../../mfc/reference/cmfccolorbutton-class.md) objekt, který je nadřazeného člena aktuální tlačítko. Tato hodnota je důležité, pokud bude tlačítko barev je v hierarchii ovládacích prvků panelu nástrojů nebo je v ovládacím prvku mřížky vlastností barev.|
|`m_pParentRibbonBtn`|Ukazatel [cmfcribboncolorbutton –](../../mfc/reference/cmfcribboncolorbutton-class.md) objekt, který je na pásu karet a je nadřazené tlačítko aktuální tlačítka. Tato hodnota je důležité, pokud bude tlačítko barev je v hierarchii ovládacích prvků panelu nástrojů nebo je v ovládacím prvku mřížky vlastností barev.|
|`m_pWndPropList`|Ukazatel [cmfcpropertygridctrl –](../../mfc/reference/cmfcpropertygridctrl-class.md) objektu.|
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je text, který se zobrazí na **automatické** tlačítko. Další informace najdete v tématu [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je text, který je zobrazený na tlačítku pro barvy dokumentu. Další informace najdete v tématu [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je text, který se zobrazí na *jiných* tlačítko. Další informace najdete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Poznámky

Obvykle nevytvoříte `CMFCColorBar` objektu přímo. Místo toho [cmfccolormenubutton – třída](../../mfc/reference/cmfccolormenubutton-class.md) (používá se v nabídkách a panelech nástrojů) nebo [cmfccolorbutton – třída](../../mfc/reference/cmfccolorbutton-class.md) vytvoří `CMFCColorBar` objektu.

`CMFCColorBar` Třída poskytuje následující funkce:

- Automaticky upraví seznam barvy dokumentu.

- Uloží a obnoví jeho stav, společně s stav dokumentu.

- Spravuje tlačítko "automatické".

- Používá [CMFCColorPickerCtrl – třída](../../mfc/reference/cmfccolorpickerctrl-class.md) ovládacího prvku pro výběr vlastní barvy.

- Podporuje stav "odtržených" (Pokud je vytvořena pomocí [cmfccolormenubutton – třída](../../mfc/reference/cmfccolormenubutton-class.md)).

Začlenit `CMFCColorBar` funkce do vaší aplikace:

1. Vytvoření tlačítka s nabídkou pravidelné a přiřaďte ho ID, například ID_CHAR_COLOR.

1. Ve své třídě okna rámce přepsat [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) metoda a nahrazení regulárních nabídky tlačítka s [cmfccolormenubutton – třída](../../mfc/reference/cmfccolormenubutton-class.md) objektu (voláním [cmfctoolbar –: : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Nastavit všechny styly a povolit nebo zakázat funkce `CMFCColorBar` objektu během [cmfccolormenubutton – třída](../../mfc/reference/cmfccolormenubutton-class.md) vytváření. `CMFCColorMenuButton` Dynamicky vytvoří objekt `CMFCColorBar` objektu po rámec volá `CreatePopupMenu` metoda.

Když uživatel klikne na tlačítko pro ovládací prvek pruhu barev, systém použije `ON_COMMAND` – makro upozorní nadřazený ovládací prvek pruhu barev. V makru parametr ID příkazu je hodnota, která jste přiřadili do ovládacího prvku tlačítko pruhu barev v kroku 1 (ID_CHAR_COLOR v tomto příkladu). Další informace najdete v tématu [cmfccolormenubutton – třída](../../mfc/reference/cmfccolormenubutton-class.md), [cmfccolorbutton – třída](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl – třída](../../mfc/reference/cmfccolorpickerctrl-class.md), [cframewndex–třída](../../mfc/reference/cframewndex-class.md), a [cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md) třídy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat pomocí různých metod v pruhu barev `CMFCColorBar` třídy. Metody nastavení vodorovného a svislého okrajů, povolte na tlačítko, vytvoření okna pro ovládací prvek pruhu barev a nastavuje barvu aktuálně vybraný. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorbar.h

##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations

Upraví pozice barvu tlačítka v ovládacím prvku pruhu barev.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, při zpracování zprávy WM_SIZE.

##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels

Označuje, zda lze změnit označení textového barvu tlačítka.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu FALSE, což znamená, že popisky text nemůže být upraven. Potlačí tuto metodu za účelem povolení změny textové popisky.

##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList

Označuje, zda lze během procesu přizpůsobení panelu nástrojů seznamu zobrazit objekt ovládacího prvku pruhu barev.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu TRUE, což znamená, že rozhraní můžete zobrazit ovládací prvek pruhu barev během procesu přizpůsobení. Potlačí tuto metodu za účelem implementace různé chování.

##  <a name="calcsize"></a>  CMFCColorBar::CalcSize

Volá se rozhraním, jako součást procesu výpočet rozložení.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parametry

*bVertDock*<br/>
[in] TRUE, pokud chcete určit, že ovládací prvek pruhu barev je ukotven. FALSE, pokud chcete určit, že ovládací prvek pruhu barev je ukotven vodorovně.

### <a name="return-value"></a>Návratová hodnota

Velikost pole barvu tlačítka v ovládacím prvku pruhu barev.

##  <a name="cmfccolorbar"></a>  CMFCColorBar::CMFCColorBar

Vytvoří `CMFCColorBar` objektu.

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>Parametry

*Barvy*<br/>
[in] Pole barvy, které zobrazí rozhraní na ovládací prvek pruhu barev.

*color*<br/>
[in] Původně Vybraní barvu.

*lpszAutoColor*<br/>
[in] Textový popisek *automatické* tlačítko barvy (výchozí), nebo hodnota NULL.

Standardní popisek bude automatické tlačítka je **automatické**.

*lpszOtherColor*<br/>
[in] Textový popisek *jiných* tlačítko, které zobrazuje více volby barev, nebo hodnotu NULL.

Standardní popisek pro jiné tlačítko je **Další barvy...** .

*lpszDocColors*<br/>
[in] Textový popisek tlačítka pro barvy dokumentu. Barevná paleta dokumentu jsou uvedeny všechny barvy, které aktuálně používá dokumentu.

*lstDocColors*<br/>
[in] Seznam barvy, které se aktuálně používá dokumentu.

*nColumns*<br/>
[in] Počet sloupců, které má škály barev.

*nRowsDockHorz*<br/>
[in] Počet řádků, které nemá pruhu barev, pokud je ukotven vodorovně.

*nColDockVert*<br/>
[in] Počet sloupců, které nemá pruhu barev, pokud je ukotven svisle.

*colorAutomatic*<br/>
[in] Výchozí barva, která se použije rozhraní po kliknutí na tlačítko Automatické.

*nCommandID*<br/>
[in] ID příkazu pro ovládací prvek pruhu barev.

*pParentBtn*<br/>
[in] Ukazatel na tlačítku nadřazené.

*src*<br/>
[in] Existující `CMFCColorBar` objektu, které se mají zkopírovat do nové `CMFCColorBar` objektu.

*uiCommandID*<br/>
[in] ID příkazu.

##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize

Vypočítá vertikálním a horizontálním okraje, které jsou nutné tak, aby obsahovala tlačítek v ovládacím prvku pruhu barev a upraví umístění těchto tlačítek.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bSquareButtons*|[in] PRAVDA, pokud chcete určit, že tvar tlačítek v ovládacím panelu barev čtvereček; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.|
|*bCenterButtons*|[in] TRUE, pokud chcete určit, že je obsah na přední tlačítka ovládací prvek pruhu barev zarovnaný na střed; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.|

### <a name="remarks"></a>Poznámky

##  <a name="create"></a>  CMFCColorBar::Create

Vytvoří okno ovládacího prvku pruhu barev a připojí ho k `CMFCColorBar` objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Ukazatel do nadřazeného okna.

*dwStyle*<br/>
[in] Bitová kombinace (nebo) [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[in] ID příkazu.

*pPalette*<br/>
[in] Ukazatel na paletu barev. Výchozí hodnota je NULL.

*nColumns*<br/>
[in] Počet sloupců v ovládacím prvku pruhu barev. Výchozí hodnota je 0.

*nRowsDockHorz*<br/>
[in] Počet řádků v pruhu barev řízení, když je ukotveno vodorovně. Výchozí hodnota je 0.

*nColDockVert*<br/>
[in] Počet sloupců v pruhu barev řízení, když je ukotveno svisle. Výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

K vytvoření `CMFCColorBar` objektu, volání konstruktoru třídy pak tato metoda. `Create` Metoda vytvoří ovládací prvek Windows a inicializuje seznam barev.

##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl

Vytvoří okno Ovládací prvek pruhu barev, připojí se k `CMFCColorBar` objektu a změní velikost okna ovládacího prvku tak, aby obsahovala zadaný palety barev.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Ukazatel do nadřazeného okna. Nemůže mít hodnotu NULL.

*Rect*<br/>
[in] Ohraničující obdélník, který určuje, kde nakreslete ovládací prvek pruhu barev.

*nID*<br/>
[in] ID ovládacího prvku.

*nColumns*<br/>
[in] Ideální počet sloupců v ovládacím prvku pruhu barev. Tato metoda mění toto číslo podle zadaného palety barev. Výchozí hodnota je -1, což znamená, že tento parametr není zadán.

*pPalette*<br/>
[in] Ukazatel na paletu barev, nebo hodnota NULL. Pokud tento parametr hodnotu NULL, tato metoda vypočítá velikost ovládacího prvku pruhu barev, jakoby byly zadány 20 barvy. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda uspěje; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá *rect*, *nColumns*, a *pPalette* parametry pro výpočet vhodným číslem nebo řádků a sloupců do ovládacího prvku pruhu barev a poté zavolá [CMFCColorBar::Create](#create) metody.

##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette

Inicializuje barevnou paletu barev v určeném poli barvy.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*arColors*|[in] Pole barvy.|
|*palette*|[in] Palety barev.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton

Zobrazí nebo skryje automatické tlačítko.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Textový popisek *automatické* tlačítko barvy (výchozí), nebo hodnota NULL.

Standardní popisek bude automatické tlačítka je **automatické**.

*colorAutomatic*<br/>
[in] Výchozí barva, která se použije rozhraní po kliknutí na tlačítko Automatické.

*bEnable*<br/>
[in] TRUE, pokud chcete povolit automatické tlačítko; FALSE, pokud chcete zakázat automatické tlačítko. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Textový popisek tlačítka pro automatické je odstraněna, když *lpszLabel* parametr hodnotu NULL nebo *bEnable* má hodnotu FALSE.

##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton

Povolí nebo zakáže zobrazení dialogového okna, která umožňuje uživateli vybrat více barev.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Textový popisek *jiných* tlačítko, které zobrazuje více volby barev, nebo hodnotu NULL.

Standardní popisek pro toto tlačítko je **Další barvy...** .

*bAltColorDlg*<br/>
[in] True pro zobrazení [cmfccolordialog –](../../mfc/reference/cmfccolordialog-class.md) dialogové okno; FALSE, pokud chcete zobrazit standardní [ccolordialog –](../../mfc/reference/ccolordialog-class.md) dialogové okno. Výchozí hodnota je TRUE.

*bEnable*<br/>
[in] TRUE, pokud chcete povolit tlačítko; FALSE, pokud chcete zakázat tlačítko. Výchozí hodnota je TRUE.

##  <a name="getcolor"></a>  CMFCColorBar::GetColor

Načte aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuálně vybraná barva.

##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize

Vypočítá počet řádků a sloupců v mřížce ovládací prvek pruhu barev.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bVertDock*|[in] TRUE, pokud chcete výpočet pro ovládací prvek svisle pruhu barev; v opačném případě proveďte výpočty vodorovně ukotvené ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

A [CSize](../../atl-mfc-shared/reference/csize-class.md) jehož `cx` komponenta obsahuje počet sloupců a jejichž `cy` komponenta obsahuje počet řádků.

##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID

Načte Identifikátor příkazu aktuální ovládací prvek pruhu barev.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu.

### <a name="remarks"></a>Poznámky

Když uživatel vybere novou barvu, rozhraní pošle ID příkazu, který v wm_command – zprávy s upozorněním nadřazeného člena `CMFCColorBar` objektu.

##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight

Vypočítá dalších výšku aktuální pruhu barev vyžaduje pro zobrazení prvků různé uživatelského rozhraní, jako **jiných** barvy tlačítka nebo dokumentu.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nNumColumns*|[in] Pokud ovládací prvek pruhu barev obsahuje barvy dokumentu, číslo sloupce, které chcete zobrazit v mřížce barvy dokumentu. V opačném případě tuto hodnotu nepoužívá.|

### <a name="return-value"></a>Návratová hodnota

Počítané navíc výšku, které je povinný.

##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor

Zjišťuje barvu, která označuje, že barevné tlačítko má fokus; To znamená, tlačítko je *horké*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB.

### <a name="remarks"></a>Poznámky

##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin

Získá vodorovný okraj je mezera mezi vlevo nebo pravá barva buněk a ohraničení oblasti klienta.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Návratová hodnota

Vodorovný okraj.

##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin

Získá svislý okraj, což je prostor mezi horní nebo dolní buňka barvu a ohraničení oblasti klienta.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Svislý okraj.

##  <a name="initcolors"></a>  CMFCColorBar::InitColors

Inicializuje pole barvy v zadané palety, nebo s systémové výchozí palety barev.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pPalette*|[in] Ukazatel na objekt palety, nebo hodnota NULL. Pokud má parametr hodnotu NULL, tato metoda používá výchozí palety operačního systému.|
|*arColors*|[in] Pole barvy.|

### <a name="return-value"></a>Návratová hodnota

Počet prvků v poli barvy.

##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff

Označuje, zda je aktuální pruhu barev ukotvit.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktuální ovládací prvek pruhu barev ukotvitelné; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek pruhu barev ukotvitelné, může být odtržení ovládací panel a ukotven na jiném místě.

##  <a name="onkey"></a>  CMFCColorBar::OnKey

Volá se rozhraním, když uživatel stiskne tlačítko klávesnice.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
[in] Kód virtuální klíče pro klíč, který uživatel stiskne.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda zpracovává se zadaným klíčem; v opačném případě hodnota FALSE.

##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand

Volá se rozhraním, zavřete hierarchii překryvných ovládacích prvků.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pButton*|[in] Ukazatel na ovládací prvek, který se nachází na panelu nástrojů.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI

Volá se rozhraním, které chcete povolit nebo zakázat uživatelské rozhraní položky ovládacího prvku pruhu barev než položka je zobrazena.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
[in] Ukazatel na okno, které obsahuje položku uživatelského rozhraní. Chcete-li aktualizovat.

*bDisableIfNoHndler*<br/>
[in] TRUE, pokud chcete zakázat položku uživatelského rozhraní, pokud žádná obslužná rutina je definována v mapování zprávy; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Uživatelské rozhraní položky kliknutí uživatele vaší aplikace položky musíte vědět, jestli by se měla zobrazit jako povolené nebo zakázané. Cíl příkazu zpráv poskytuje tyto informace pomocí implementace obslužné rutiny příkazu ON_UPDATE_COMMAND_UI. Pomocí této metody můžete pomoct zpracování příkazu. Další informace najdete v tématu [ccmdui – třída](../../mfc/reference/ccmdui-class.md).

##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog

Otevře se dialogové okno barvy.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
[in] Barva, která je standardně vybraná, když se otevře dialogové okno barev.

*colorRes*<br/>
[out] Barva, která vybrané uživatele.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud uživatel vybral barvu. FALSE, pokud uživatel zrušil dialogové okno barev.

### <a name="remarks"></a>Poznámky

##  <a name="rebuild"></a>  CMFCColorBar::Rebuild

Zcela překreslí ovládací prvek pruhu barev.

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette

Nastaví logickou paletu kontextu zadané zařízení na paletě tlačítko nadřazeného ovládacího prvku aktuální pruhu barev.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pDC*|[in] Ukazatel na kontext zařízení tlačítka nadřazeného ovládacího prvku aktuální pruhu barev.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na paletu, která je nahrazena palety tlačítko nadřazeného ovládacího prvku aktuální pruhu barev.

##  <a name="setcolor"></a>  CMFCColorBar::SetColor

Nastaví barvu, která aktuálně není vybrán.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Hodnota barvy RGB.

##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName

Nastaví nový název pro zadanou barvu.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Hodnota RGB barvu.

*strName*<br/>
[in] Nový název pro zadanou barvu.

### <a name="remarks"></a>Poznámky

Tato metoda se změní název zadané barvy ve všech `CMFCColorBar` objekty ve vaší aplikaci.

##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID

Nastaví nový Identifikátor příkazu pro ovládací prvek pruhu barev.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parametry

*nCommandID*<br/>
[in] ID příkazu.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu, upravte Identifikátor příkazu ovládacího prvku pruhu barev a upozorní nadřazené okno ovládacího prvku, který se změnil Identifikátor.

##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors

Nastaví seznam barev, které se používají v aktuálním dokumentu.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszCaption*<br/>
[in] Titulek, který se zobrazí, pokud není ukotven ovládací prvek pruhu barev.

*lstDocColors*<br/>
[in] Seznam barvy, který nahrazuje barvy aktuálního dokumentu.

*bShowWhenDocked*<br/>
[in] TRUE, pokud chcete zobrazit barvy dokumentu, když ovládací prvek pruhu barev je ukotven; v opačném případě hodnota FALSE. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

*Barvy dokumentu* jsou barvy, které jsou aktuálně používány v dokumentu. Rozhraní automaticky udržuje seznam barvy dokumentu, ale tuto metodu můžete použít k úpravě seznamu.

##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin

Nastaví na vodorovný okraj je mezera mezi vlevo nebo pravá barva buněk a ohraničení oblasti klienta.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parametry

*nHorzMargin*<br/>
[in] Vodorovný okraj v pixelech.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [CMFCColorBar::CMFCColorBar](#cmfccolorbar) konstruktor nastaví Vodorovný okraj na 4 pixelů.

##  <a name="setproplist"></a>  CMFCColorBar::SetPropList

Nastaví `m_pWndPropList` chráněný datový člen na zadaný ukazatel na ovládací prvek mřížky vlastností.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pWndList*|[in] Ukazatel na objekt ovládacího prvku mřížky vlastností.|

##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin

Nastaví na svislé okraj je mezera mezi horní nebo spodní buňce barvy a ohraničení oblasti klienta.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parametry

*nVertMargin*<br/>
[in] Svislé okraje v pixelech.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [CMFCColorBar::CMFCColorBar](#cmfccolorbar) konstruktor nastaví svislý okraj na 4 pixelů.

##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString

Požádá o okno rámce, který vlastní ovládací prvek pruhu barev k aktualizaci řádku zprávy ve stavovém řádku.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] ID příkazu. (Tento parametr je ignorován.)

### <a name="remarks"></a>Poznámky

Tato metoda odešle zprávu WM_SETMESSAGESTRING vlastníkovi ovládacího prvku pruhu barev.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
