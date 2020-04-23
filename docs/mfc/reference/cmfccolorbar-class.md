---
title: Třída CMFCColorBar
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
ms.openlocfilehash: 58fddeef9cb0afe930af84b05e6a87871f729da4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752572"
---
# <a name="cmfccolorbar-class"></a>Třída CMFCColorBar

Třída `CMFCColorBar` představuje řídicí panel ukotvení, který může vybrat barvy v dokumentu nebo aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Vytvoří `CMFCColorBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorBar::ContexttoSize](#contexttosize)|Vypočítá svislé a vodorovné okraje, které musí obsahovat tlačítka na ovládacím prvku pruhu barev, a potom upraví umístění těchto tlačítek.|
|[CMFCColorBar::Ovládací prvek CreateControl](#createcontrol)|Vytvoří okno ovládacího prvku panelu `CMFCColorBar` barev, připojí jej k objektu a změní jeho velikost tak, aby obsahoval zadanou paletu barev.|
|[CMFCColorBar::Vytvořit](#create)|Vytvoří ovládací okno panelu barev a `CMFCColorBar` připojí ho k objektu.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Zobrazí nebo skryje automatické tlačítko.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže zobrazení dialogového okna, které umožňuje uživateli vybrat více barev.|
|[CMFCColorBar::GetColor](#getcolor)|Načte aktuálně vybranou barvu.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Načte ID příkazu aktuálního ovládacího prvku panelu barev.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Načte barvu, která znamená, že barevné tlačítko má fokus; to znamená, že tlačítko je *horké*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Načte vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Načte svislý okraj, což je mezera mezi horní nebo dolní barevnou buňkou a hranicí klientské oblasti.|
|[CMFCColorBar::IsTearoff](#istearoff)|Označuje, zda je aktuální barevný pruh dokovatelný.|
|[CMFCColorBar:SetColor](#setcolor)|Nastaví barvu, která je aktuálně vybraná.|
|[CMFCColorBar::SetColorName](#setcolorname)|Nastaví nový název pro zadanou barvu.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Nastaví nové ID příkazu pro ovládací prvek pruhu barev.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Nastaví seznam barev, které se používají v aktuálním dokumentu.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Nastaví vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Nastaví svislý okraj, což je mezera mezi horní nebo dolní barevnou buňkou a hranicí klientské oblasti.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorBar::adjustlocations](#adjustlocations)|Upraví polohy barevných tlačítek na ovládacím prvku pruhu barev.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Označuje, zda se může změnit textový popisek barevných tlačítek.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Označuje, zda se objekt ovládacího prvku panelu barev může během procesu vlastního nastavení zobrazit v seznamu panelů nástrojů.|
|[CMFCColorBar::Velikost čárky](#calcsize)|Volat rámci jako součást procesu výpočtu rozložení.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializuje paletu s barvami v zadaném poli barev.|
|[CMFCColorBar::Getcolorgridsize](#getcolorgridsize)|Vypočítá počet řádků a sloupců v mřížce ovládacího prvku pruhu barev.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Vypočítá další výšku, kterou aktuální barevný pruh vyžaduje k zobrazení vedlejších prvků uživatelského rozhraní, jako je tlačítko **Jiné,** barvy dokumentu a tak dále.|
|[CMFCColorBar::InitColors](#initcolors)|Inicializuje pole barev s barvami v zadané paletě nebo výchozí paletě systému.|
|[CMFCColorBar::OnKey](#onkey)|Volat rámci při stisknutí tlačítka klávesnice uživatele.|
|[CMFCColorBar::Příkaz OnSendCommand](#onsendcommand)|Volat rámci zavřít hierarchii místní ovládací prvky.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Volat rámci povolit nebo zakázat položku uživatelského rozhraní ovládacího prvku panelu barev před zobrazením položky.|
|[CMFCColorBar::Dialog OpenColorDialog](#opencolordialog)|Otevře dialogové okno barva.|
|[CMFCColorBar::Znovu sestavit](#rebuild)|Zcela překreslí ovládací prvek pruhu barev.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Nastaví logickou paletu zadaného kontextu zařízení na paletu nadřazeného tlačítka aktuálního ovládacího prvku pruhu barev.|
|[CMFCColorBar:SetPropList](#setproplist)|Nastaví `m_pWndPropList` chráněný datový člen na zadaný ukazatel na ovládací prvek mřížky vlastností.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Požaduje okno rámce, které vlastní ovládací prvek panelu barev, aby aktualizovalo řádek zprávy ve stavovém řádku.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|`m_bInternal`|Logické pole, které určuje, zda jsou zpracovány události myši. Události myši jsou obvykle zpracovány, pokud je toto pole PRAVDA a režim přizpůsobení je FALSE.|
|`m_bIsEnabled`|Logická hodnota, která označuje, zda je povolen ovládací prvek.|
|`m_bIsTearOff`|Logická hodnota označující, zda ovládací prvek panelu barev podporuje ukotvení.|
|`m_BoxSize`|Objekt [CSize,](../../atl-mfc-shared/reference/csize-class.md) který určuje velikost buňky v mřížce barev.|
|`m_bShowDocColorsWhenDocked`|Logická hodnota, která označuje, zda se mají při ukotvení pruhu barev zobrazovat barvy dokumentu. Další informace naleznete v tématu [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Logická hodnota, která označuje, zda se má zobrazit dialogové okno standardní barvy systému nebo dialogové okno [CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md) Další informace naleznete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[Colorref,](/windows/win32/gdi/colorref) který ukládá aktuální automatickou barvu. Další informace naleznete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md) objekt, který přidružuje sadu barev RGB s jejich názvy.|
|`m_colors`|[CArray](../../mfc/reference/carray-class.md) hodnot [COLORREF,](/windows/win32/gdi/colorref) které obsahuje barvy, které jsou zobrazeny v ovládacím prvku pruhu barev.|
|`m_ColorSelected`|Hodnota [COLORREF,](/windows/win32/gdi/colorref) která je barvou, kterou uživatel aktuálně vybral z ovládacího prvku panelu barev.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) [colorref](/windows/win32/gdi/colorref) hodnoty, které obsahuje barvy, které jsou aktuálně používány v dokumentu.|
|`m_nCommandID`|Nepodepsané celé číslo, které je ID příkazu tlačítka barvy.|
|`m_nHorzMargin`|Celé číslo, které je vodorovným okrajem mezi barevnými tlačítky v mřížce barev.|
|`m_nHorzOffset`|Celé číslo, které je vodorovným odsazením od středu tlačítka barvy. Tato hodnota je významná, pokud tlačítko zobrazuje kromě barvy text nebo obrázek.|
|`m_nNumColumns`|Celé číslo, které je počet sloupců v řídicí mřížce barev.|
|`m_nNumColumnsVert`|Celé číslo, které je počet sloupců ve svisle orientované mřížce barev.|
|`m_nNumRowsHorz`|Celé číslo, které je počet sloupců v vodorovně orientované mřížky barev.|
|`m_nRowHeight`|Celé číslo, které je výškou řady barevných tlačítek v mřížce barev.|
|`m_nVertMargin`|Celé číslo, které je svislým okrajem mezi barevnými tlačítky v mřížce barev.|
|`m_nVertOffset`|Celé číslo, které je svislým odsazením od středu tlačítka barvy. Tato hodnota je významná, pokud tlačítko zobrazuje kromě barvy text nebo obrázek.|
|`m_Palette`|[CPalette](../../mfc/reference/cpalette-class.md) barev, které se používají v ovládacím prvku panelu barev.|
|`m_pParentBtn`|Ukazatel na objekt [CMFCColorButton,](../../mfc/reference/cmfccolorbutton-class.md) který je nadřazeným objektem aktuálního tlačítka. Tato hodnota je významná, pokud je tlačítko barva v hierarchii ovládacích prvků panelu nástrojů nebo je v ovládacím prvku mřížky vlastností barvy.|
|`m_pParentRibbonBtn`|Ukazatel na objekt [CMFCRibbonColorButton,](../../mfc/reference/cmfcribboncolorbutton-class.md) který je na pásu karet a je nadřazeným tlačítkem aktuálního tlačítka. Tato hodnota je významná, pokud je tlačítko barva v hierarchii ovládacích prvků panelu nástrojů nebo je v ovládacím prvku mřížky vlastností barvy.|
|`m_pWndPropList`|Ukazatel na objekt [CMFCPropertyGridCtrl.](../../mfc/reference/cmfcpropertygridctrl-class.md)|
|`m_strAutoColor`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který je text, který je zobrazen na **tlačítko Automatické.** Další informace naleznete v tématu [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který je text, který je zobrazen na tlačítko barvy dokumentu. Další informace naleznete v tématu [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který je text, který je zobrazen na *druhém* tlačítku. Další informace naleznete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Poznámky

Obvykle nevytváříte `CMFCColorBar` objekt přímo. Místo toho objekt vytvoří `CMFCColorBar` třída [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (používaná v nabídkách a panelech nástrojů) nebo třída [CMFCColorButton.](../../mfc/reference/cmfccolorbutton-class.md)

Třída `CMFCColorBar` poskytuje následující funkce:

- Automaticky upraví seznam barev dokumentu.

- Uloží a obnoví jeho stav spolu se stavem dokumentu.

- Spravuje tlačítko "automatické".

- Používá ovládací prvek [třídy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) k výběru vlastní barvy.

- Podporuje "odtrhnut" stav (pokud je vytvořen pomocí [CMFCColorMenuButton class).](../../mfc/reference/cmfccolormenubutton-class.md)

Chcete-li `CMFCColorBar` začlenit funkce do aplikace:

1. Vytvořte běžné tlačítko nabídky a přiřaďte mu ID, například ID_CHAR_COLOR.

1. Ve třídě okna rámce přepište metodu [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) a nahraďte běžné tlačítko nabídky objektem [třídy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (voláním [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Nastavte všechny styly a povolte `CMFCColorBar` nebo zakažte funkce objektu během vytváření [třídy CMFCColorMenuButton.](../../mfc/reference/cmfccolormenubutton-class.md) Objekt `CMFCColorMenuButton` dynamicky vytvoří `CMFCColorBar` objekt po framework `CreatePopupMenu` volá metodu.

Když uživatel klepne na ovládací tlačítko panelu `ON_COMMAND` barev, rozhraní framework pomocí makra upozorní nadřazený ovládací prvek pruhu barev. V makru je parametr ID příkazu hodnota, kterou jste přiřadili ovládacímu tlačítku panelu barev v kroku 1 (ID_CHAR_COLOR v tomto příkladu). Další informace naleznete v [třídách TŘÍDY CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)a [CMFCToolBar.](../../mfc/reference/cmfctoolbar-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat barevný pruh pomocí `CMFCColorBar` různých metod ve třídě. Metody nastavují vodorovné a svislé okraje, povolte druhé tlačítko, vytvoří ovládací okno panelu barev a nastaví aktuálně vybranou barvu. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCPanel](../../mfc/reference/cmfctoolbar-class.md)

[CmFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCBarevný pruh](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorbar.h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar::adjustlocations

Upraví polohy barevných tlačítek na ovládacím prvku pruhu barev.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci během zpracování WM_SIZE zpráv.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Označuje, zda se může změnit textový popisek barevných tlačítek.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy FALSE

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu NEPRAVDA, což znamená, že textové popisky nelze změnit. Přepište tuto metodu, abyste povolili úpravy textových popisků.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Označuje, zda se objekt ovládacího prvku panelu barev může během procesu vlastního nastavení zobrazit v seznamu panelů nástrojů.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu TRUE, což znamená, že rozhraní framework může zobrazit ovládací prvek panelu barev během procesu vlastního nastavení. Přepsat tuto metodu implementovat jiné chování.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar::Velikost čárky

Volat rámci jako součást procesu výpočtu rozložení.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parametry

*bVertDock*<br/>
[v] TRUE, chcete-li určit, že ovládací prvek pruhu barev je ukotven svisle; FALSE, chcete-li určit, že ovládací prvek pruhu barev je ukotven vodorovně.

### <a name="return-value"></a>Návratová hodnota

Velikost pole barevných tlačítek v ovládacím prvku panelu barev.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

Vytvoří `CMFCColorBar` objekt.

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
[v] Pole barev, které se v rámci zobrazí na ovládacím prvku panelu barev.

*color*<br/>
[v] Původně vybraná barva.

*lpszAutoColor*<br/>
[v] Textový popisek *automatického* (výchozího) tlačítka barvy nebo NULL.

Standardní štítek pro automatické tlačítko je **Automatické**.

*lpszOtherColor*<br/>
[v] Textový popisek *druhého* tlačítka, který zobrazuje více voleb barev, nebo NULL.

Standardní popisek pro druhé tlačítko je **Více barev...**.

*lpszDocBarvy*<br/>
[v] Textový popis tlačítka barvy dokumentu. Paleta barev dokumentu obsahuje seznam všech barev, které dokument aktuálně používá.

*Barvy lstDoc*<br/>
[v] Seznam barev, které dokument aktuálně používá.

*nSloupce*<br/>
[v] Počet sloupců, které má pole barev.

*nRowsDockHorz*<br/>
[v] Počet řádků, které má barevný pruh, když je ukotven vodorovně.

*nColDockVert*<br/>
[v] Počet sloupců, které má barevný pruh, když je ukotven svisle.

*colorAutomaticky*<br/>
[v] Výchozí barva, kterou rozhraní použije po klepnutí na tlačítko automatické.

*nID příkazu*<br/>
[v] ID příkazu ovládacího prvku color bar.

*pParentBtn*<br/>
[v] Ukazatel na nadřazené tlačítko.

*src*<br/>
[v] Existující `CMFCColorBar` objekt, který má být `CMFCColorBar` zkopírován do nového objektu.

*uiCommandID*<br/>
[v] ID příkazu.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorBar::ContexttoSize

Vypočítá svislé a vodorovné okraje, které musí obsahovat tlačítka na ovládacím prvku pruhu barev, a upraví umístění těchto tlačítek.

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bSquareTlačítka*|[v] TRUE, chcete-li určit, že tvar tlačítek na ovládacím prvku pruhu barev jsou čtvercové; jinak NEPRAVDA. Výchozí hodnota je TRUE.|
|*bCenterTlačítka*|[v] TRUE, chcete-li určit, že obsah na ploše ovládacího tlačítka panelu barev je vystředěný; jinak NEPRAVDA. Výchozí hodnota je TRUE.|

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar::Vytvořit

Vytvoří ovládací okno panelu barev a `CMFCColorBar` připojí ho k objektu.

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
[v] Ukazatel na nadřazené okno.

*dwStyl*<br/>
[v] Bitová kombinace (OR) [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Nid*<br/>
[v] ID příkazu.

*pPaleta*<br/>
[v] Ukazatel na paletu barev. Výchozí hodnota je NULL.

*nSloupce*<br/>
[v] Počet sloupců v ovládacím prvku panelu barev. Výchozí hodnota je 0.

*nRowsDockHorz*<br/>
[v] Počet řádků v ovládacím prvku pruhu barev, když je ukotven vodorovně. Výchozí hodnota je 0.

*nColDockVert*<br/>
[v] Počet sloupců v ovládacím prvku pruhu barev, když je ukotven svisle. Výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Chcete-li `CMFCColorBar` vytvořit objekt, volání konstruktoru třídy pak tuto metodu. Metoda `Create` vytvoří ovládací prvek systému Windows a inicializuje seznam barev.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar::Ovládací prvek CreateControl

Vytvoří ovládací okno panelu barev, `CMFCColorBar` připojí ho k objektu a změní jeho velikost tak, aby obsahovalo zadanou paletu barev.

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
[v] Ukazatel na nadřazené okno. Nemůže být null.

*Rect*<br/>
[v] Ohraničující obdélník, který určuje, kam nakreslit ovládací prvek pruhu barev.

*Nid*<br/>
[v] ID ovládacího prvku.

*nSloupce*<br/>
[v] Ideální počet sloupců v ovládacím prvku panelu barev. Tato metoda upraví toto číslo tak, aby odpovídalo zadané paletě barev. Výchozí hodnota je -1, což znamená, že tento parametr není zadán.

*pPaleta*<br/>
[v] Ukazatel na paletu barev nebo NULL. Pokud je tento parametr NULL, tato metoda vypočítá velikost ovládacího prvku panelu barev, jako by bylo zadáno 20 barev. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda je úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá parametry *rect*, *nColumns*a *pPalette* k výpočtu příslušného čísla nebo řádků a sloupců v ovládacím prvku panelu barev a poté volá metodu [CMFCColorBar::Create.](#create)

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar::CreatePalette

Inicializuje paletu s barvami v zadaném poli barev.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*arBarvy*|[v] Pole barev.|
|*Palety*|[v] Paleta barev.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Zobrazí nebo skryje automatické tlačítko.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Textový popisek *automatického* (výchozího) tlačítka barvy nebo NULL.

Standardní štítek pro automatické tlačítko je **Automatické**.

*colorAutomaticky*<br/>
[v] Výchozí barva, kterou rozhraní použije po klepnutí na tlačítko automatické.

*bEnable*<br/>
[v] TRUE pro povolení automatického tlačítka; False zakázat automatické tlačítko. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Textový popisek automatického tlačítka se odstraní, pokud je parametr *lpszLabel* NULL nebo *parametr bEnable* je FALSE.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Povolí nebo zakáže zobrazení dialogového okna, které umožňuje uživateli vybrat více barev.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Textový popisek *druhého* tlačítka, který zobrazuje více voleb barev, nebo NULL.

Standardní popisek pro toto tlačítko je **Více barev...**.

*bAltColorDlg*<br/>
[v] TRUE pro zobrazení dialogového okna [CMFCColorDialog;](../../mfc/reference/cmfccolordialog-class.md) NEPRAVDA pro zobrazení standardního dialogového okna [CColorDialog.](../../mfc/reference/ccolordialog-class.md) Výchozí hodnota je TRUE.

*bEnable*<br/>
[v] TRUE pro povolení tlačítka; Nepravda pro zakázání tlačítka. Výchozí hodnota je TRUE.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar::GetColor

Načte aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuálně vybraná barva.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar::Getcolorgridsize

Vypočítá počet řádků a sloupců v mřížce ovládacího prvku pruhu barev.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bVertDock*|[v] TRUE pro provedení výpočtu pro svisle ukotvený ovládací prvek pruhu barev; v opačném případě proveďte výpočet pro horizontálně ukotvený ovládací prvek.|

### <a name="return-value"></a>Návratová hodnota

A [CSize](../../atl-mfc-shared/reference/csize-class.md) `cx` objekt, jehož komponenta `cy` obsahuje počet sloupců a jehož součást obsahuje počet řádků.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar::GetCommandID

Načte ID příkazu aktuálního ovládacího prvku panelu barev.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu.

### <a name="remarks"></a>Poznámky

Když uživatel vybere novou barvu, rozhraní odešle ID příkazu v WM_COMMAND `CMFCColorBar` zprávě upozornit nadřazený objekt.

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Vypočítá další výšku, kterou aktuální barevný pruh vyžaduje k zobrazení různých prvků uživatelského rozhraní, například barvy tlačítka **Jiné** nebo dokumentu.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nSloupce Num*|[v] Pokud ovládací prvek panelu barev obsahuje barvy dokumentu, počet sloupců, které se mají zobrazit v mřížce barev dokumentu. V opačném případě se tato hodnota nepoužívá.|

### <a name="return-value"></a>Návratová hodnota

Vypočtená extra výška, která je požadována.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Načte barvu, která znamená, že barevné tlačítko má fokus; to znamená, že tlačítko je *horké*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Načte vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Návratová hodnota

Vodorovný okraj.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Načte svislý okraj, což je mezera mezi horní nebo dolní barevnou buňkou a hranicí klientské oblasti.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Svislý okraj.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorBar::InitColors

Inicializuje pole barev s barvami v zadané paletě nebo s výchozí paletou systému.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pPaleta*|[v] Ukazatel na objekt palety nebo NULL. Pokud je tento parametr NULL, tato metoda používá výchozí paletu operačního systému.|
|*arBarvy*|[v] Pole barev.|

### <a name="return-value"></a>Návratová hodnota

Počet prvků v poli barev.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar::IsTearoff

Označuje, zda je aktuální barevný pruh dokovatelný.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je aktuální ovládací prvek pruhu barev dokovatelný; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek panelu barev dokovatelný, lze jej utrhnout z ovládacího panelu a ukotvit na jiném místě.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorBar::OnKey

Volat rámci při stisknutí tlačítka klávesnice uživatele.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parametry

*Nchar*<br/>
[v] Kód virtuální klávesy pro klíč, který uživatel stiskl.

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud tato metoda zpracuje zadaný klíč; jinak NEPRAVDA.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorBar::Příkaz OnSendCommand

Volat rámci uzavřít hierarchii automaticky otevíraných ovládacích prvků.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pTlačítko*|[v] Ukazatel na ovládací prvek, který je umístěn na panelu nástrojů.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Volat rámci povolit nebo zakázat položku uživatelského rozhraní ovládacího prvku panelu barev před zobrazením položky.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

*pCíl*<br/>
[v] Ukazatel na okno, které obsahuje položku uživatelského rozhraní k aktualizaci.

*bDisableIfNoHndler*<br/>
[v] TRUE zakázat položku uživatelského rozhraní, pokud není definována žádná obslužná rutina v mapě zpráv; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Když uživatel aplikace klepne na položku uživatelského rozhraní, musí vědět, zda má být zobrazena jako povolená nebo zakázaná. Cíl zprávy příkazu poskytuje tyto informace implementací obslužné rutiny příkazu ON_UPDATE_COMMAND_UI. Pomocí této metody můžete příkaz zpracovat. Další informace naleznete v tématu [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::Dialog OpenColorDialog

Otevře dialogové okno barva.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
[v] Barva, která je vybrána ve výchozím nastavení při otevření dialogového okna barva.

*colorRes*<br/>
[out] Barva, kterou uživatel vybral.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud uživatel vybral barvu; FALSE, pokud uživatel zrušil dialogové okno barva.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar::Znovu sestavit

Zcela překreslí ovládací prvek pruhu barev.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColorBar::SelectPalette

Nastaví logickou paletu zadaného kontextu zařízení na paletu nadřazeného tlačítka aktuálního ovládacího prvku pruhu barev.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Pdc*|[v] Ukazatel na kontext zařízení nadřazeného tlačítka aktuálního ovládacího prvku pruhu barev.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na paletu, která je nahrazena paletou nadřazeného tlačítka aktuálního ovládacího prvku pruhu barev.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColorBar:SetColor

Nastaví barvu, která je aktuálně vybraná.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota barvy RGB.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFCColorBar::SetColorName

Nastaví nový název pro zadanou barvu.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota RGB barvy.

*strName*<br/>
[v] Nový název pro zadanou barvu.

### <a name="remarks"></a>Poznámky

Tato metoda změní název zadané barvy `CMFCColorBar` ve všech objektech v aplikaci.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar::SetCommandID

Nastaví nové ID příkazu pro ovládací prvek pruhu barev.

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parametry

*nID příkazu*<br/>
[v] ID příkazu.

### <a name="remarks"></a>Poznámky

Volání této metody upravit ID příkazu ovládacího prvku panelu barev a upozornit nadřazené okno ovládacího prvku, který změnil ID.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Nastaví seznam barev, které se používají v aktuálním dokumentu.

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszTitulek*<br/>
[v] Titulek, který se zobrazí, když ovládací prvek pruhu barev není ukotven.

*Barvy lstDoc*<br/>
[v] Seznam barev, které nahrazují aktuální barvy dokumentu.

*bZobrazitWhenDocked*<br/>
[v] PRAVDA, chcete-li zobrazit barvy dokumentu, když je ovládací prvek pruhu barev ukotven; jinak NEPRAVDA. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

*Barvy dokumentu* jsou barvy, které se aktuálně používají v dokumentu. Rozhraní framework automaticky udržuje seznam barev dokumentu, ale tuto metodu můžete použít k úpravě seznamu.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Nastaví vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parametry

*nHorzMarná*<br/>
[v] Vodorovný okraj v obrazových bodech.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení konstruktor [CMFCColorBar::CMFCColorBar](#cmfccolorbar) nastaví vodorovný okraj na 4 obrazové body.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColorBar:SetPropList

Nastaví `m_pWndPropList` chráněný datový člen na zadaný ukazatel na ovládací prvek mřížky vlastností.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pWndList*|[v] Ukazatel na objekt ovládacího prvku mřížky vlastností.|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Nastaví svislý okraj, což je mezera mezi horní nebo dolní barevnou buňkou a hranicí klientské oblasti.

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parametry

*nVertMargin*<br/>
[v] Svislý okraj v pixelech.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení konstruktor [CMFCColorBar::CMFCColorBar](#cmfccolorbar) nastaví svislý okraj na 4 obrazové body.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Požaduje okno rámce, které vlastní ovládací prvek panelu barev, aby aktualizovalo řádek zprávy ve stavovém řádku.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[v] ID příkazu. (Tento parametr je ignorován.)

### <a name="remarks"></a>Poznámky

Tato metoda odešle zprávu WM_SETMESSAGESTRING vlastníkovi ovládacího prvku panelu barev.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
