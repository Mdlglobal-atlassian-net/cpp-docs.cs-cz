---
title: CMFCColorBar – třída
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
ms.openlocfilehash: 25bfe3ef67fcca7708179d1a316af05b3ba49dda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505432"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar – třída

`CMFCColorBar` Třída představuje ukotvené ovládací panel, který může vybírat barvy v dokumentu nebo v aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|`CMFCColorBar` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Vypočítá svislé a vodorovné okraje, které jsou požadovány pro nastavení tlačítek na ovládacím prvku pruh barev, a poté upraví umístění těchto tlačítek.|
|[CMFCColorBar::CreateControl](#createcontrol)|Vytvoří ovládací prvek panelu barev okno, připojí ho k `CMFCColorBar` objektu a změní velikost ovládacího prvku tak, aby obsahoval určenou paletu barev.|
|[CMFCColorBar:: Create](#create)|Vytvoří ovládací prvek panelu barev a připojí ho k `CMFCColorBar` objektu.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Zobrazí nebo skryje automatické tlačítko.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže zobrazení dialogového okna, které uživateli umožní vybrat další barvy.|
|[CMFCColorBar::GetColor](#getcolor)|Načte aktuálně vybranou barvu.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Načte ID příkazu aktuálního ovládacího prvku panelu barev.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Načte barvu, která značí, že tlačítko barvy má fokus. To znamená, že tlačítko je *horké*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Načte vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Načte svislou hranici, což je mezera mezi horní nebo dolní buňkou barvy a hranicí klientské oblasti.|
|[CMFCColorBar::IsTearOff](#istearoff)|Určuje, zda je aktuální panel barev ukotvit.|
|[CMFCColorBar::SetColor](#setcolor)|Nastaví barvu, která je aktuálně vybrána.|
|[CMFCColorBar::SetColorName](#setcolorname)|Nastaví nový název zadané barvy.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Nastaví nové ID příkazu pro ovládací prvek panelu barev.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Nastaví seznam barev použitých v aktuálním dokumentu.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Nastaví vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Nastaví svislý okraj, což je prostor mezi horní nebo dolní buňkou barvy a hranicí klientské oblasti.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Upraví umístění tlačítek barev na ovládacím prvku pruh barev.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Určuje, zda se může změnit textový popisek barevných tlačítek.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Určuje, zda se objekt ovládacího prvku pruh barev může zobrazit v seznamu panelů nástrojů během procesu přizpůsobení.|
|[CMFCColorBar::CalcSize](#calcsize)|Volá se rozhraním jako součást procesu výpočtu rozložení.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializuje paletu s barvami v zadaném poli barev.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Vypočítá počet řádků a sloupců v mřížce ovládacího prvku panel barev.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Vypočítá dodatečnou výšku, kterou aktuální pruh barev vyžaduje, aby zobrazoval různé prvky uživatelského rozhraní, jako je **druhé** tlačítko, barvy dokumentu a tak dále.|
|[CMFCColorBar::InitColors](#initcolors)|Inicializuje pole barev s barvami v zadané paletě nebo výchozí paletě systému.|
|[CMFCColorBar::OnKey](#onkey)|Volá se rozhraním, když uživatel stiskne tlačítko klávesnice.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Volá se rozhraním, aby se zavřela hierarchie překryvných ovládacích prvků.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Volá se rozhraním, aby se povolil nebo zakázal položka uživatelského rozhraní ovládacího prvku panel barev před tím, než se položka zobrazí.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Otevře dialogové okno barvy.|
|[CMFCColorBar:: Rebuild](#rebuild)|Zcela znovu vykreslí ovládací prvek panelu barev.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Nastaví logickou paletu určeného kontextu zařízení na paletu nadřazeného tlačítka pro aktuální ovládací prvek panelu barev.|
|[CMFCColorBar::SetPropList](#setproplist)|`m_pWndPropList` Nastaví chráněný datový člen na zadaný ukazatel na ovládací prvek mřížky vlastností.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Vyžádá okno rámce, které vlastní ovládací prvek Panel barev k aktualizaci čáry zprávy ve stavovém řádku.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|`m_bInternal`|Logické pole, které určuje, zda jsou zpracovány události myši. Události myši se typicky zpracovávají, pokud je toto pole pravdivé a režim přizpůsobení je FALSE.|
|`m_bIsEnabled`|Logická hodnota, která označuje, zda je ovládací prvek povolen.|
|`m_bIsTearOff`|Logická hodnota, která označuje, zda ovládací prvek pruh barev podporuje ukotvení.|
|`m_BoxSize`|Objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , který určuje velikost buňky v mřížce pruhů barev.|
|`m_bShowDocColorsWhenDocked`|Logická hodnota, která označuje, zda se mají zobrazovat barvy dokumentu v případě, že je panel barev ukotven. Další informace najdete v tématu [CMFCColorBar:: SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Logická hodnota, která označuje, zda se má zobrazit dialogové okno standardní systémová barva nebo dialogové okno [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) Další informace najdete v tématu [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref) , který ukládá aktuální automatickou barvu. Další informace najdete v tématu [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Objekt [CMAP](../../mfc/reference/cmap-class.md) , který přidruží sadu barev RGB k jejich názvům.|
|`m_colors`|[CArray –](../../mfc/reference/carray-class.md) hodnot [COLORREF](/windows/win32/gdi/colorref) , které obsahují barvy, které se zobrazují v ovládacím prvku pruh barev.|
|`m_ColorSelected`|Hodnota [COLORREF](/windows/win32/gdi/colorref) , která je barvou, kterou uživatel aktuálně vybral z ovládacího prvku panelu barev.|
|`m_lstDocColors`|[CList –](../../mfc/reference/clist-class.md) hodnot [COLORREF](/windows/win32/gdi/colorref) , které obsahují barvy, které jsou aktuálně použity v dokumentu.|
|`m_nCommandID`|Unsigned integer, který je ID příkazu pro tlačítko barvy.|
|`m_nHorzMargin`|Celé číslo, které je vodorovným okrajem barevných tlačítek v mřížce barev.|
|`m_nHorzOffset`|Celé číslo, které je vodorovným posunem na střed tlačítka barvy. Tato hodnota je významná, pokud tlačítko zobrazuje text nebo obrázek kromě barvy.|
|`m_nNumColumns`|Celé číslo, které je počtem sloupců v mřížce řídicích panelů barev.|
|`m_nNumColumnsVert`|Celé číslo, které je počtem sloupců v vertikálně orientované mřížce barev.|
|`m_nNumRowsHorz`|Celé číslo, které je počtem sloupců v horizontálně orientované mřížce barev.|
|`m_nRowHeight`|Celé číslo, které je výškou řádku barevných tlačítek v mřížce barev.|
|`m_nVertMargin`|Celé číslo, které je svislým okrajem barevných tlačítek v mřížce barev.|
|`m_nVertOffset`|Celé číslo, které je svislé posunutí na střed tlačítka barvy. Tato hodnota je významná, pokud tlačítko zobrazuje text nebo obrázek kromě barvy.|
|`m_Palette`|[CPalette –](../../mfc/reference/cpalette-class.md) barvy, které se používají v ovládacím prvku pruh barev.|
|`m_pParentBtn`|Ukazatel na objekt [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) , který je nadřazeným prvkem aktuálního tlačítka. Tato hodnota je významná, pokud je tlačítko barvy v hierarchii ovládacích prvků panelu nástrojů nebo je v ovládacím prvku mřížky vlastností Color.|
|`m_pParentRibbonBtn`|Ukazatel na objekt [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) , který je na pásu karet a je nadřazené tlačítko aktuálního tlačítka. Tato hodnota je významná, pokud je tlačítko barvy v hierarchii ovládacích prvků panelu nástrojů nebo je v ovládacím prvku mřížky vlastností Color.|
|`m_pWndPropList`|Ukazatel na objekt [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) .|
|`m_strAutoColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je text zobrazený na tlačítku pro **Automatické** zobrazení. Další informace najdete v tématu [CMFCColorBar:: EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je text zobrazený na tlačítku barvy dokumentu. Další informace najdete v tématu [CMFCColorBar:: SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je text zobrazený na *druhém* tlačítku. Další informace najdete v tématu [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Poznámky

Obvykle nevytváříte `CMFCColorBar` objekt přímo. Místo toho [Třída CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (použitá v nabídkách a panelech nástrojů) nebo [Třída CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) vytvoří `CMFCColorBar` objekt.

`CMFCColorBar` Třída nabízí následující funkce:

- Automaticky upraví seznam barev dokumentu.

- Uloží a obnoví svůj stav spolu se stavem dokumentu.

- Spravuje tlačítko "automatické".

- Používá ovládací prvek [třídy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) k výběru vlastní barvy.

- Podporuje stav "unoff" (Pokud je vytvořen pomocí [třídy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Zahrnutí `CMFCColorBar` funkcí do vaší aplikace:

1. Vytvořte regulární tlačítko nabídky a přiřaďte mu ID, například ID_CHAR_COLOR.

1. V rámci třídy okna rámce přepište metodu [CFrameWndEx:: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) a nahraďte tlačítko regulární nabídky objektem [třídy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (voláním [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Nastavte všechny styly a povolte nebo zakažte funkce `CMFCColorBar` objektu během vytváření [třídy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) . Objekt dynamicky vytvoří objekt poté, co rozhraní zavolá metodu.`CreatePopupMenu` `CMFCColorBar` `CMFCColorMenuButton`

Když uživatel klikne na tlačítko ovládacího prvku panel barev, rozhraní použije `ON_COMMAND` makro k upozorňování nadřazeného ovládacího prvku pruhu barev. V makru je parametr ID příkazu hodnotou, kterou jste přiřadili k ovládacímu tlačítku panelu barev v kroku 1 (ID_CHAR_COLOR v tomto příkladu). Další informace naleznete v tématu [Třída CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), třída [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md), třída [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md), třídy [CFrameWndEx](../../mfc/reference/cframewndex-class.md)a třídy [třídy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak konfigurovat pruh barev pomocí různých metod ve `CMFCColorBar` třídě. Metody nastaví vodorovné a svislé okraje, povolí druhé tlačítko, vytvoří okno ovládacího prvku panelu barev a nastaví aktuálně vybranou barvu. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorbar. h

##  <a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Upraví umístění tlačítek barev na ovládacím prvku pruh barev.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním během zpracování zprávy WM_SIZE.

##  <a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Určuje, zda se může změnit textový popisek barevných tlačítek.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy NEPRAVDA.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždycky vrátí hodnotu FALSE, což znamená, že textové popisky nelze upravovat. Tuto metodu přepište, pokud chcete povolit úpravu textových popisků.

##  <a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Určuje, zda se objekt ovládacího prvku pruh barev může zobrazit v seznamu panelů nástrojů během procesu přizpůsobení.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždycky TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu TRUE, což znamená, že rozhraní může zobrazit ovládací prvek panelu barev během procesu přizpůsobení. Tuto metodu přepište, pokud chcete implementovat jiné chování.

##  <a name="calcsize"></a>CMFCColorBar::CalcSize

Volá se rozhraním jako součást procesu výpočtu rozložení.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parametry

*bVertDock*<br/>
pro TRUE pro určení, zda je ovládací prvek Panel barev ukotvený svisle; FALSE, pokud chcete určit, že ovládací prvek Panel barev je ukotvený vodorovně.

### <a name="return-value"></a>Návratová hodnota

Velikost pole barevných tlačítek v ovládacím prvku panelu barev.

##  <a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

`CMFCColorBar` Vytvoří objekt.

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

*barvy*<br/>
pro Pole barev, které rozhraní zobrazuje v ovládacím prvku pruh barev.

*barevných*<br/>
pro Zpočátku vybraná barva.

*lpszAutoColor*<br/>
pro Textový popisek *automatického* (výchozí) barvy tlačítka nebo hodnota null

Standardní popisek pro automatické tlačítko je **Automatický**.

*lpszOtherColor*<br/>
pro Textový popisek *druhého* tlačítka, ve kterém se zobrazí více voleb barev nebo hodnota null.

Standardní popisek pro druhé tlačítko je **více barev...** .

*lpszDocColors*<br/>
pro Popisek textu tlačítka barvy dokumentu Paleta barvy dokumentu obsahuje seznam všech barev, které dokument aktuálně používá.

*lstDocColors*<br/>
pro Seznam barev, které dokument aktuálně používá.

*nColumns*<br/>
pro Počet sloupců, které má pole barev.

*nRowsDockHorz*<br/>
pro Počet řádků, které má pruh barev v případě, že je ukotvený vodorovně

*nColDockVert*<br/>
pro Počet sloupců, které má pruh barev v případě, že je ukotvený svisle

*colorAutomatic*<br/>
pro Výchozí barva, kterou rozhraní používá, když kliknete na tlačítko automaticky.

*nCommandID*<br/>
pro ID příkazu ovládacího prvku panelu barev

*pParentBtn*<br/>
pro Ukazatel na nadřazené tlačítko.

*src*<br/>
pro Existující `CMFCColorBar` objekt, který má být zkopírován do nového `CMFCColorBar` objektu.

*uiCommandID*<br/>
pro ID příkazu

##  <a name="contexttosize"></a>CMFCColorBar::ContextToSize

Vypočítá svislé a vodorovné okraje, které jsou požadovány pro zahrnutí tlačítek na ovládacím prvku panelu barev, a upraví umístění těchto tlačítek.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bSquareButtons*|pro TRUE pro určení, zda je tvar tlačítek na ovládacím prvku panelu barev čtvercový; v opačném případě FALSE. Výchozí hodnota je TRUE (pravda).|
|*bCenterButtons*|pro Hodnota TRUE, pokud má být obsah na ploše ovládacího tlačítka panelu barev zarovnán na střed; v opačném případě FALSE. Výchozí hodnota je TRUE (pravda).|

### <a name="remarks"></a>Poznámky

##  <a name="create"></a>CMFCColorBar:: Create

Vytvoří ovládací prvek panelu barev a připojí ho k `CMFCColorBar` objektu.

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
pro Ukazatel na nadřazené okno.

*dwStyle*<br/>
pro Bitová kombinace (nebo) [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
pro ID příkazu

*pPalette*<br/>
pro Ukazatel na paletu barev. Výchozí hodnota je NULL.

*nColumns*<br/>
pro Počet sloupců v ovládacím prvku panelu barev Výchozí hodnota je 0.

*nRowsDockHorz*<br/>
pro Počet řádků v ovládacím prvku panelu barev, pokud je ukotven vodorovně Výchozí hodnota je 0.

*nColDockVert*<br/>
pro Počet sloupců v ovládacím prvku pruh barev v případě, že je ukotvený svisle Výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li `CMFCColorBar` vytvořit objekt, zavolejte konstruktor třídy a pak tuto metodu. `Create` Metoda vytvoří ovládací prvek Windows a inicializuje seznam barev.

##  <a name="createcontrol"></a>CMFCColorBar::CreateControl

Vytvoří ovládací prvek Panel barev, připojí ho k `CMFCColorBar` objektu a změní velikost okna ovládacího prvku tak, aby obsahovalo určenou paletu barev.

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
pro Ukazatel na nadřazené okno. Nemůže mít hodnotu NULL.

*OBD*<br/>
pro Ohraničující obdélník, který určuje, kde má být ovládací prvek pruh barev nakreslen.

*nID*<br/>
pro ID ovládacího prvku

*nColumns*<br/>
pro Ideální počet sloupců v ovládacím prvku panelu barev. Tato metoda upraví toto číslo tak, aby odpovídalo zadané paletě barev. Výchozí hodnota je-1, což znamená, že tento parametr není zadán.

*pPalette*<br/>
pro Ukazatel na paletu barev nebo hodnotu NULL. Pokud má tento parametr hodnotu NULL, tato metoda vypočítá velikost ovládacího prvku pruh barev, jako kdyby byly zadány 20 barev. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda používá parametry *Rect*, *nColumns*a *pPalette* k výpočtu vhodného čísla nebo řádků a sloupců v ovládacím prvku panelu barev a poté volá metodu [CMFCColorBar:: Create](#create) .

##  <a name="createpalette"></a>CMFCColorBar::CreatePalette

Inicializuje paletu s barvami v zadaném poli barev.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*arColors*|pro Pole barev.|
|*zadání*|pro Paleta barev|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

##  <a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Zobrazí nebo skryje automatické tlačítko.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
pro Textový popisek *automatického* (výchozí) barvy tlačítka nebo hodnota null

Standardní popisek pro automatické tlačítko je **Automatický**.

*colorAutomatic*<br/>
pro Výchozí barva, kterou rozhraní používá, když kliknete na tlačítko automaticky.

*bEnable*<br/>
pro TRUE, pokud chcete povolit automatické tlačítko; FALSE, pokud chcete zakázat automatické tlačítko. Výchozí hodnota je TRUE (pravda).

### <a name="remarks"></a>Poznámky

Textový popisek automatického tlačítka se odstraní, pokud má parametr *lpszLabel* hodnotu null nebo je parametr *bEnable* false.

##  <a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Povolí nebo zakáže zobrazení dialogového okna, které uživateli umožní vybrat další barvy.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
pro Textový popisek *druhého* tlačítka, ve kterém se zobrazí více voleb barev nebo hodnota null.

Standardní popisek pro toto tlačítko je **více barev...** .

*bAltColorDlg*<br/>
pro TRUE pro zobrazení dialogového okna [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ; FALSE pro zobrazení standardního dialogového okna [CColorDialog](../../mfc/reference/ccolordialog-class.md) . Výchozí hodnota je TRUE (pravda).

*bEnable*<br/>
pro TRUE pro povolení tlačítka; Hodnota FALSE pro zakázání tlačítka Výchozí hodnota je TRUE (pravda).

##  <a name="getcolor"></a>CMFCColorBar:: GetColor

Načte aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuálně vybraná barva.

##  <a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize

Vypočítá počet řádků a sloupců v mřížce ovládacího prvku panel barev.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bVertDock*|pro TRUE pro provedení výpočtu vertikálně ukotveného ovládacího prvku panelu barev; v opačném případě proveďte výpočet pro horizontální ukotvený ovládací prvek.|

### <a name="return-value"></a>Návratová hodnota

Objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , jehož `cx` součást obsahuje počet sloupců a jejichž `cy` součást obsahuje počet řádků.

##  <a name="getcommandid"></a>CMFCColorBar::GetCommandID

Načte ID příkazu aktuálního ovládacího prvku panelu barev.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu

### <a name="remarks"></a>Poznámky

Když uživatel vybere novou barvu, rozhraní pošle ID příkazu ve zprávě WM_COMMAND pro upozornění nadřazeného `CMFCColorBar` objektu.

##  <a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Vypočítá dodatečnou výšku, kterou aktuální pruh barev vyžaduje pro zobrazení různých prvků uživatelského rozhraní, jako jsou **ostatní** barvy tlačítek nebo dokumentů.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nNumColumns*|pro Pokud ovládací prvek pruh barev obsahuje barvy dokumentu, počet sloupců, které se mají zobrazit v mřížce barev dokumentu. V opačném případě se tato hodnota nepoužívá.|

### <a name="return-value"></a>Návratová hodnota

Vypočítaná dodatečná výška je požadovaná.

##  <a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Načte barvu, která značí, že tlačítko barvy má fokus. To znamená, že tlačítko je *horké*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB.

### <a name="remarks"></a>Poznámky

##  <a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Načte vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí klientské oblasti.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Návratová hodnota

Vodorovný okraj

##  <a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Načte svislou hranici, což je mezera mezi horní nebo dolní buňkou barvy a hranicí klientské oblasti.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Svislý okraj

##  <a name="initcolors"></a>CMFCColorBar::InitColors

Inicializuje pole barev s barvami v zadané paletě nebo s výchozí paletou systému.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pPalette*|pro Ukazatel na objekt palety nebo hodnota NULL. Pokud má tento parametr hodnotu NULL, používá tato metoda výchozí paletu operačního systému.|
|*arColors*|pro Pole barev.|

### <a name="return-value"></a>Návratová hodnota

Počet prvků v poli barev.

##  <a name="istearoff"></a>CMFCColorBar::IsTearOff

Určuje, zda je aktuální panel barev ukotvit.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je aktuální ovládací prvek panelu barev ukotvit; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek panelu barev ukotvit, může být přerušen z ovládacího panelu a ukotven v jiném umístění.

##  <a name="onkey"></a>CMFCColorBar::OnKey

Volá se rozhraním, když uživatel stiskne tlačítko klávesnice.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
pro Kód virtuálního klíče pro klíč, který uživatel stiskne.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda zpracuje zadaný klíč. v opačném případě FALSE.

##  <a name="onsendcommand"></a>CMFCColorBar::OnSendCommand

Volá se rozhraním, aby se zavřela hierarchie místních ovládacích prvků.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pButton*|pro Ukazatel na ovládací prvek, který se nachází na panelu nástrojů.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

##  <a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Volá se rozhraním, aby se povolil nebo zakázal položka uživatelského rozhraní ovládacího prvku panel barev před tím, než se položka zobrazí.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
pro Ukazatel na okno obsahující položku uživatelského rozhraní, která se má aktualizovat.

*bDisableIfNoHndler*<br/>
pro TRUE pro zakázání položky uživatelského rozhraní, pokud není v mapě zpráv definována žádná obslužná rutina; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Když uživatel vaší aplikace klikne na položku uživatelského rozhraní, musí tato položka zjistit, jestli má být zobrazená jako povolená nebo zakázaná. Cíl zprávy příkazu poskytuje tyto informace implementací obslužné rutiny příkazu ON_UPDATE_COMMAND_UI. Tuto metodu použijte k tomu, abyste mohli zpracovat příkaz. Další informace naleznete v tématu [Třída CCmdUI –](../../mfc/reference/ccmdui-class.md).

##  <a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog

Otevře dialogové okno barvy.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
pro Barva, která je vybrána ve výchozím nastavení, když se otevře dialogové okno Barva.

*colorRes*<br/>
mimo Barva, kterou uživatel vybral.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud uživatel vybral barvu; FALSE, pokud uživatel zrušil dialogové okno Barva.

### <a name="remarks"></a>Poznámky

##  <a name="rebuild"></a>CMFCColorBar:: Rebuild

Zcela znovu vykreslí ovládací prvek panelu barev.

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>CMFCColorBar::SelectPalette

Nastaví logickou paletu určeného kontextu zařízení na paletu nadřazeného tlačítka pro aktuální ovládací prvek panelu barev.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pDC*|pro Ukazatel na kontext zařízení nadřazeného tlačítka aktuálního ovládacího prvku panelu barev.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na paletu, který je nahrazen paletou nadřazeného tlačítka pro aktuální ovládací prvek panelu barev.

##  <a name="setcolor"></a>CMFCColorBar::SetColor

Nastaví barvu, která je aktuálně vybrána.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
pro Hodnota barvy RGB.

##  <a name="setcolorname"></a>CMFCColorBar::SetColorName

Nastaví nový název zadané barvy.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
pro Hodnota RGB barvy

*strName*<br/>
pro Nový název zadané barvy.

### <a name="remarks"></a>Poznámky

Tato metoda změní název zadané barvy ve všech `CMFCColorBar` objektech aplikace.

##  <a name="setcommandid"></a>CMFCColorBar::SetCommandID

Nastaví nové ID příkazu pro ovládací prvek panelu barev.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parametry

*nCommandID*<br/>
pro ID příkazu

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro úpravu ID příkazu ovládacího prvku panelu barev a upozorní nadřazené okno ovládacího prvku, že se změnilo ID.

##  <a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Nastaví seznam barev použitých v aktuálním dokumentu.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszCaption*<br/>
pro Popisek, který se zobrazí, když není ukotven ovládací prvek panelu barev.

*lstDocColors*<br/>
pro Seznam barev, které nahradí aktuální barvy dokumentu.

*bShowWhenDocked*<br/>
pro TRUE pro zobrazení barev dokumentu při ukotvení ovládacího prvku pruh barev; v opačném případě FALSE. Výchozí hodnota je FALSE (NEPRAVDA).

### <a name="remarks"></a>Poznámky

*Barvy dokumentu* jsou barvy, které jsou aktuálně používány v dokumentu. Rozhraní automaticky udržuje seznam barev dokumentu, ale tuto metodu lze použít k úpravě seznamu.

##  <a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Nastaví vodorovný okraj, což je mezera mezi levou nebo pravou barevnou buňkou a hranicí oblasti klienta.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parametry

*nHorzMargin*<br/>
pro Vodorovný okraj v pixelech

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení konstruktor [CMFCColorBar:: CMFCColorBar](#cmfccolorbar) nastaví vodorovný okraj na 4 pixely.

##  <a name="setproplist"></a>CMFCColorBar::SetPropList

`m_pWndPropList` Nastaví chráněný datový člen na zadaný ukazatel na ovládací prvek mřížky vlastností.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pWndList*|pro Ukazatel na objekt ovládacího prvku mřížky vlastností.|

##  <a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Nastaví svislý okraj, což je prostor mezi horní nebo dolní buňkou barvy a hranicí klientské oblasti.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parametry

*nVertMargin*<br/>
pro Svislá hrana v pixelech

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení konstruktor [CMFCColorBar:: CMFCColorBar](#cmfccolorbar) nastaví svislý okraj na 4 pixely.

##  <a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Vyžádá okno rámce, které vlastní ovládací prvek Panel barev k aktualizaci čáry zprávy ve stavovém řádku.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
pro ID příkazu (Tento parametr je ignorován.)

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu WM_SETMESSAGESTRING vlastníkovi ovládacího prvku panel barev.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
