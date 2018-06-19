---
title: Třída CMFCColorBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2083c26943768afff4b3b20a2ba95c709648dd50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376135"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar – třída
`CMFCColorBar` Třída reprezentuje ukotvení ovládacích pruhů, které můžete vybrat barvy v dokumentu nebo aplikace.  
  
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
|[CMFCColorBar::ContextToSize](#contexttosize)|Vypočítá svislého a vodorovného okraje, které se musí obsahovat tlačítek v ovládacím prvku pruhu barev a pak upraví umístění těchto tlačítek.|  
|[CMFCColorBar::CreateControl](#createcontrol)|Vytvoří okno pro řízení pruhu barev, připojí se k `CMFCColorBar` objektu a změní velikost ovládacího prvku tak, aby obsahovala zadaný paletu barev.|  
|[CMFCColorBar::Create](#create)|Okno pro řízení pruhu barev vytvoří a připojí jej k `CMFCColorBar` objektu.|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Zobrazí nebo skryje tlačítko Automatická.|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže zobrazení dialogu, který umožňuje uživateli vybrat více barev.|  
|[CMFCColorBar::GetColor](#getcolor)|Načte aktuálně vybrané barvy.|  
|[CMFCColorBar::GetCommandID](#getcommandid)|Načte ID příkazu, který aktuální ovládacího prvku pruhu barev.|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Načte barvu, která označuje, že barva tlačítko je aktivní; tlačítko je *aktivní*.|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Načte vodorovné okrajem, což je prostor mezi vlevo nebo vpravo barvu buňky a hranic oblasti klienta.|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Načte svislé okrajem, což je prostor mezi horní nebo dolní barvu buňky a hranic oblasti klienta.|  
|[CMFCColorBar::IsTearOff](#istearoff)|Určuje, zda je aktuální pruhu barev lze ukotvit.|  
|[CMFCColorBar::SetColor](#setcolor)|Nastaví barvu, která je aktuálně vybrané.|  
|[CMFCColorBar::SetColorName](#setcolorname)|Nastaví nový název pro zadaná barva.|  
|[CMFCColorBar::SetCommandID](#setcommandid)|Nastaví nové ID příkazu pro ovládací prvek pruhu barev.|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Nastaví seznam barev, které se používají v aktuálním dokumentu.|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Nastaví vodorovnou okrajem, což je prostor mezi vlevo nebo vpravo barvu buňky a hranic oblasti klienta.|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Nastaví svislé okraj, který je mezery mezi barvu buňky horní nebo dolní a hranic oblasti klienta.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Upraví pozic barva tlačítek v ovládacím prvku pruhu barev.|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Určuje, zda lze změnit textový popisek barva tlačítek.|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Označuje, zda objekt ovládacího prvku pruhu barev můžete zobrazit v seznamu panelu nástrojů během procesu přizpůsobení.|  
|[CMFCColorBar::CalcSize](#calcsize)|Voláno rámcem jako součást procesu výpočtu rozložení.|  
|[CMFCColorBar::CreatePalette](#createpalette)|Initalizes palety barev v zadané pole barev.|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Spočítá počet řádků a sloupců v mřížce ovládacího prvku pruhu barev.|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Vypočítá další výška, který aktuální pruhu barev vyžaduje, aby zobrazit různé prvky rozhraní, jako **jiných** tlačítko, barvy dokumentu a tak dále.|  
|[CMFCColorBar::InitColors](#initcolors)|Inicializuje pole barvy s barev v zadané palety nebo z výchozí palety systému.|  
|[CMFCColorBar::OnKey](#onkey)|Voláno rámcem po stisknutí tlačítka klávesnice.|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Voláno rámcem zavřete hierarchie ovládacích prvků v automaticky otevřeném okně.|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Voláno rámcem chcete povolit nebo zakázat uživatelské rozhraní položky ovládacího prvku pruhu barev předtím, než se zobrazí položka.|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Otevře dialogové okno barvy.|  
|[CMFCColorBar::Rebuild](#rebuild)|Úplně překreslí ovládacího prvku pruhu barev.|  
|[CMFCColorBar::SelectPalette](#selectpalette)|Nastaví logické paletu kontext zadané zařízení na paletu tlačítko nadřazeného prvku aktuální pruhu barev.|  
|[CMFCColorBar::SetPropList](#setproplist)|Nastaví `m_pWndPropList` chráněná data člena na zadané ukazatel do ovládacího prvku mřížky vlastnosti.|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Požadavky rámec okna, který vlastní ovládací prvek pruhu barev aktualizovat řádek zprávy ve stavovém řádku.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|`m_bInternal`|Logická hodnota pole, které určuje, zda se zpracují událostí myši. Obvykle se zpracovat události myši, když je toto pole `TRUE` a přizpůsobení režim je `FALSE`.|  
|`m_bIsEnabled`|Logická hodnota, která určuje, zda je povoleno ovládacího prvku.|  
|`m_bIsTearOff`|Logická hodnota, která určuje, zda ovládacího prvku pruhu barev podporuje ukotvení.|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který určuje velikost buňky v mřížce pruhu barev.|  
|`m_bShowDocColorsWhenDocked`|Logická hodnota, která určuje, zda zobrazit barvy dokumentu, když je ukotvena pruhu barev. Další informace najdete v tématu [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_bStdColorDlg`|Logická hodnota, která označuje, zda se zobrazí dialogové okno barvy standardní systém nebo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) dialogové okno. Další informace najdete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) , uloží aktuální automatické barvu. Další informace najdete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md) objekt, který přidruží sadu RGB barvy s jejich názvy.|  
|`m_colors`|A [carray –](../../mfc/reference/carray-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnoty, které obsahuje barev, které se zobrazují v ovládacím prvku pruhu barev.|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnota tedy barvu, která uživatel má aktuálně vybrané z ovládacího prvku pruhu barev.|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnoty, které obsahuje barev, které jsou aktuálně používány v dokumentu.|  
|`m_nCommandID`|Celé číslo bez znaménka, který je ID příkazu, který barva tlačítka.|  
|`m_nHorzMargin`|Celé číslo, které je vodorovné okraje mezi barva tlačítek v mřížce barev.|  
|`m_nHorzOffset`|Celé číslo, které je vodorovný posun do centra tlačítko barvy. Tato hodnota je důležité, pokud na tlačítko zobrazí text nebo obrázek kromě barvy.|  
|`m_nNumColumns`|Celé číslo, které je počet sloupců v tabulce barev řízení pruhu barev.|  
|`m_nNumColumnsVert`|Celé číslo, které je počet sloupců v mřížce svisle orientované barev.|  
|`m_nNumRowsHorz`|Celé číslo, které je počet sloupců v mřížce vodorovně orientované barev.|  
|`m_nRowHeight`|Celé číslo, které je výšku řádku barva tlačítek v mřížce barev.|  
|`m_nVertMargin`|Celé číslo, které je svislé okraje mezi barva tlačítek v mřížce barev.|  
|`m_nVertOffset`|Celé číslo, které je svislý posun do centra tlačítko barvy. Tato hodnota je důležité, pokud na tlačítko zobrazí text nebo obrázek kromě barvy.|  
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md) barev, které se používají v ovládacím prvku pruhu barev.|  
|`m_pParentBtn`|Ukazatel [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) objekt, který je nadřazený prvek na aktuální tlačítko. Tato hodnota je důležité, pokud je tlačítko barvy v hierarchii ovládací prvky panelu nástrojů nebo je v ovládacím prvku mřížky vlastností barev.|  
|`m_pParentRibbonBtn`|Ukazatel [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) objekt, který je na pásu karet a je tlačítko nadřazené aktuálního tlačítka. Tato hodnota je důležité, pokud je tlačítko barvy v hierarchii ovládací prvky panelu nástrojů nebo je v ovládacím prvku mřížky vlastností barev.|  
|`m_pWndPropList`|Ukazatel [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) objektu.|  
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) tedy text, který se zobrazí na **automatické** tlačítko. Další informace najdete v tématu [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|  
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) tedy text, který se zobrazí na tlačítko barvy dokumentu. Další informace najdete v tématu [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) tedy text, který se zobrazí na *jiných* tlačítko. Další informace najdete v tématu [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle nevytvoříte `CMFCColorBar` objektu přímo. Místo toho [CMFCColorMenuButton třída](../../mfc/reference/cmfccolormenubutton-class.md) (používá se v nabídek a panelů nástrojů) nebo [CMFCColorButton třída](../../mfc/reference/cmfccolorbutton-class.md) vytvoří `CMFCColorBar` objektu.  
  
 `CMFCColorBar` Třída poskytuje následující funkce:  
  
-   Automaticky upraví seznam barev dokumentu.  
  
-   Uloží a obnoví stav, společně s stavu dokumentu.  
  
-   Spravuje tlačítko "automatické".  
  
-   Používá [CMFCColorPickerCtrl třída](../../mfc/reference/cmfccolorpickerctrl-class.md) ovládacího prvku pro výběr vlastních barev.  
  
-   Podporuje stavu "úplné vypnuto" (Pokud je vytvořen pomocí [CMFCColorMenuButton třída](../../mfc/reference/cmfccolormenubutton-class.md)).  
  
 Chcete-li zahrnout `CMFCColorBar` funkce do vaší aplikace:  
  
1.  Vytvoření tlačítka s nabídkou regulární a přiřaďte ho ID, například ID_CHAR_COLOR.  
  
2.  Ve třídě rámce okna přepsat [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) metodu a nahraďte regulární nabídky tlačítka s [CMFCColorMenuButton třída](../../mfc/reference/cmfccolormenubutton-class.md) objektu (voláním [CMFCToolBar: : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).  
  
3.  Nastavit všechny styly a povolit nebo zakázat funkce `CMFCColorBar` objektu během [CMFCColorMenuButton třída](../../mfc/reference/cmfccolormenubutton-class.md) vytvoření. `CMFCColorMenuButton` Dynamicky vytvoří objekt `CMFCColorBar` objektu po volání framework `CreatePopupMenu` metoda.  
  
 Když uživatel klikne ovládací prvek tlačítko pruhu barev, používá rozhraní `ON_COMMAND` makro oznámit nadřazeného ovládacího prvku pruhu barev. Makro parametr ID příkazu je hodnota, který jste přiřadili pro ovládací prvek tlačítko pruhu barev v kroku 1 (ID_CHAR_COLOR v tomto příkladu). Další informace najdete v tématu [CMFCColorMenuButton třída](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton třída](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl třída](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx třída](../../mfc/reference/cframewndex-class.md), a [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md) třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat pomocí různých metod v pruhu barev `CMFCColorBar` třídy. Metody nastavení okrajů vodorovného a svislého, povolte na tlačítko Další, vytvořit okno pro řízení pruhu barev a nastaví aktuálně vybrané barvy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
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
 **Záhlaví:** afxcolorbar.h  
  
##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations  
 Upraví pozic barva tlačítek v ovládacím prvku pruhu barev.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rozhraním framework během `WM_SIZE` zpracování zprávy.  
  
##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels  
 Určuje, zda lze změnit textový popisek barva tlačítek.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda vždy vrátí `FALSE`, což znamená, že popisky text nemůže být upraven. Potlačí tuto metodu za účelem povolení popisky změny textu.  
  
##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList  
 Označuje, zda objekt ovládacího prvku pruhu barev můžete zobrazit v seznamu panelu nástrojů během procesu přizpůsobení.  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda vždy vrátí `TRUE`, což znamená, že rozhraní můžete zobrazit ovládacího prvku pruhu barev během procesu přizpůsobení. Potlačí tuto metodu implementovat různé chování.  
  
##  <a name="calcsize"></a>  CMFCColorBar::CalcSize  
 Voláno rámcem jako součást procesu výpočtu rozložení.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bVertDock`  
 `TRUE` Chcete-li určit, že ovládacího prvku pruhu barev ukotven svisle; `FALSE` k určení, že ovládacího prvku pruhu barev ukotven vodorovně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost pole Barva tlačítek v ovládacím prvku pruhu barev.  
  
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
 [v] `colors`  
 Pole barev, které rozhraní zobrazí v ovládacím prvku pruhu barev.  
  
 [v] `color`  
 Původně vybrané barvy.  
  
 [v] `lpszAutoColor`  
 Textový popisek *automatické* tlačítko barvy (výchozí), nebo `NULL`.  
  
 Standardní popisek tlačítka automatické je **automatické**.  
  
 [v] `lpszOtherColor`  
 Textový popisek *jiných* tlačítko, které zobrazí další volby barev, nebo `NULL`.  
  
 Standardní popisek pro tlačítko Další je **Další barvy...** .  
  
 [v] `lpszDocColors`  
 Textový popisek tlačítka barvy dokumentu. Barevná paleta dokumentu jsou uvedeny všechny barev, které aktuálně používá v dokumentu.  
  
 [v] `lstDocColors`  
 Seznam barev, které aktuálně používá v dokumentu.  
  
 [v] `nColumns`  
 Počet sloupců, které má pole barev.  
  
 [v] `nRowsDockHorz`  
 Počet řádků, které má pruhu barev, kde je umístěn vodorovně.  
  
 [v] `nColDockVert`  
 Počet sloupců, které nemá pruhu barev, pokud jej ukotven svisle.  
  
 [v] `colorAutomatic`  
 Výchozí barvu, která rozhraní platí po kliknutí na tlačítko Automatická.  
  
 [v] `nCommandID`  
 ID příkazu řízení pruhu barev.  
  
 [v] `pParentBtn`  
 Ukazatel na nadřazené tlačítko.  
  
 [v] `src`  
 Existující `CMFCColorBar` objekt, který má být zkopírován do nové `CMFCColorBar` objektu.  
  
 [v] `uiCommandID`  
 ID příkazu.  
  
##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize  
 Vypočítá svislého a vodorovného okraje, které se musí obsahovat tlačítek v ovládacím prvku pruhu barev a upraví umístění těchto tlačítek.  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `bSquareButtons`|`TRUE` že jsou tvaru tlačítek v ovládacím prvku pruhu barev odmocnina; v opačném `FALSE`. Výchozí hodnota je `TRUE`.|  
|[v] `bCenterButtons`|`TRUE` Chcete-li určit, zda je umístěn na střed obsah na přední ovládací prvek tlačítko pruhu barev; v opačném `FALSE`. Výchozí hodnota je `TRUE`.|  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>  CMFCColorBar::Create  
 Okno pro řízení pruhu barev vytvoří a připojí jej k `CMFCColorBar` objektu.  
  
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
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna.  
  
 [v] `dwStyle`  
 Bitovou kombinaci (nebo) [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v] `nID`  
 ID příkazu.  
  
 [v] `pPalette`  
 Ukazatel na paletu barev. Výchozí hodnota je `NULL`.  
  
 [v] `nColumns`  
 Počet sloupců v ovládacím prvku pruhu barev. Výchozí hodnota je 0.  
  
 [v] `nRowsDockHorz`  
 Počet řádků v ovládacím prvku pruhu barev, když je umístěn vodorovně. Výchozí hodnota je 0.  
  
 [v] `nColDockVert`  
 Počet sloupců v ovládacím prvku pruhu barev při ukotven svisle. Výchozí hodnota je 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšná. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 K vytvoření `CMFCColorBar` objektu, volání konstruktoru třídy pak tuto metodu. `Create` Metoda vytvoří ovládacího prvku Windows a inicializuje seznam barev.  
  
##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl  
 Vytvoří okno pro řízení pruhu barev, připojí se k `CMFCColorBar` objektu a změní velikost okna ovládacího prvku tak, aby obsahovala zadaný paletu barev.  
  
```  
virtual BOOL CreateControl(
    CWnd* pParentWnd,  
    const CRect& rect,  
    UINT nID,  
    int nColumns=-1,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna. Nemůže být `NULL`.  
  
 [v] `rect`  
 Ohraničující obdélník, která určuje, kde k vykreslení ovládacího prvku pruhu barev.  
  
 [v] `nID`  
 ID ovládacího prvku.  
  
 [v] `nColumns`  
 Ideální počet sloupců v ovládacím prvku pruhu barev. Tato metoda upraví počet podle zadaného paletu barev. Výchozí hodnota je -1, což znamená, že není tento parametr zadán.  
  
 [v] `pPalette`  
 Ukazatel na paletu barev, nebo `NULL`. Pokud tento parametr je `NULL`, tato metoda vypočítá velikost ovládacího prvku pruhu barev, jako kdyby byly zadány 20 barvy. Výchozí hodnota je `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá `rect`, `nColumns`, a `pPalette` parametry k výpočtu příslušné číslo nebo řádků a sloupců v řízení pruhu barev a poté zavolá [CMFCColorBar::Create](#create) metoda.  
  
##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette  
 Inicializuje palety barev v zadané pole barev.  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `arColors`|Pole barev.|  
|[v] `palette`|Palety barev.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšná. v opačném `FALSE`.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton  
 Zobrazí nebo skryje tlačítko Automatická.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Textový popisek *automatické* tlačítko barvy (výchozí), nebo `NULL`.  
  
 Standardní popisek tlačítka automatické je **automatické**.  
  
 [v] `colorAutomatic`  
 Výchozí barvu, která rozhraní platí po kliknutí na tlačítko Automatická.  
  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit automatické tlačítko; `FALSE` zakázat automatické tlačítko. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Textový popisek tlačítka automatické je odstraněna, když `lpszLabel` parametr `NULL` nebo `bEnable` parametr `FALSE`.  
  
##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton  
 Povolí nebo zakáže zobrazení dialogu, který umožňuje uživateli vybrat více barev.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Textový popisek *jiných* tlačítko, které zobrazí další volby barev, nebo `NULL`.  
  
 Standardní popisek pro toto tlačítko je **Další barvy...** .  
  
 [v] `bAltColorDlg`  
 `TRUE` Chcete-li zobrazit [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) dialogové okno; `FALSE` zobrazíte standardní [CColorDialog](../../mfc/reference/ccolordialog-class.md) dialogové okno. Výchozí hodnota je `TRUE`.  
  
 [v] `bEnable`  
 `TRUE` povolit tlačítko; `FALSE` na tlačítko zakázat. Výchozí hodnota je `TRUE`.  
  
##  <a name="getcolor"></a>  CMFCColorBar::GetColor  
 Načte aktuálně vybrané barvy.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuálně vybrané barvy.  
  
##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize  
 Spočítá počet řádků a sloupců v mřížce ovládacího prvku pruhu barev.  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `bVertDock`|`TRUE` k provedení výpočtu pro ovládací prvek svisle ukotveného pruhu barev; proveďte, jinak hodnota výpočtu vodorovně ukotvené ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, jehož `cx` součást obsahuje počet sloupců a jehož `cy` součást obsahuje počet řádků.  
  
##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID  
 Načte ID příkazu, který aktuální ovládacího prvku pruhu barev.  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel vybere novou barvu, rozhraní odešle ID příkazu, který `WM_COMMAND` zprávy s upozorněním nadřazeného `CMFCColorBar` objektu.  
  
##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight  
 Vypočítá další výška, který aktuální pruhu barev vyžaduje, aby zobrazit různé prvky rozhraní, jako například **jiných** barvy tlačítko nebo dokumentu.  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `nNumColumns`|Pokud ovládací prvek pruhu barev obsahuje dokument barvy, počet sloupců do zobrazení v mřížce barvy dokumentu. Tuto hodnotu, jinak se nepoužije.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Počítané navíc výška požadované.  
  
##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor  
 Načte barvu, která označuje, že barva tlačítko je aktivní; tlačítko je *aktivní*.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin  
 Načte vodorovné okrajem, což je prostor mezi vlevo nebo vpravo barvu buňky a hranic oblasti klienta.  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vodorovné okraj.  
  
##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin  
 Načte svislé okrajem, což je prostor mezi horní nebo dolní barvu buňky a hranic oblasti klienta.  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Svislý okraj.  
  
##  <a name="initcolors"></a>  CMFCColorBar::InitColors  
 Inicializuje pole barev v zadané palety nebo s systémové výchozí palety barev.  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `pPalette`|Ukazatel na objekt palety, nebo `NULL`. Pokud tento parametr je `NULL`, tato metoda používá výchozí palety operačního systému.|  
|[v] `arColors`|Pole barev.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet prvků v poli barvy.  
  
##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff  
 Určuje, zda je aktuální pruhu barev lze ukotvit.  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je lze ukotvit; aktuální ovládací prvek pruhu barev v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládací prvek pruhu barev lze ukotvit, můžete vypnout ovládací prvek panel odpojí a ukotvení v jiném umístění.  
  
##  <a name="onkey"></a>  CMFCColorBar::OnKey  
 Voláno rámcem po stisknutí tlačítka klávesnice.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nChar`  
 Kód virtuální klíče pro klíč, který uživatel stisknutí tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda zpracovává k zadanému klíči; v opačném `FALSE`.  
  
##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand  
 Voláno rámcem zavřete hierarchie automaticky otevírané okno Ovládací prvky.  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `pButton`|Ukazatel na ovládací prvek, který se nachází na panelu nástrojů.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšná. v opačném `FALSE`.  
  
##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI  
 Voláno rámcem chcete povolit nebo zakázat uživatelské rozhraní položky ovládacího prvku pruhu barev předtím, než se zobrazí položka.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pTarget`  
 Ukazatel na okno, které obsahuje položku uživatelského rozhraní k aktualizaci.  
  
 [v] `bDisableIfNoHndler`  
 `TRUE` zakázat uživatelské rozhraní položky, pokud žádná obslužná rutina je definována v mapy zpráv; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Když aplikace klepnutí položku uživatelského rozhraní, položka musí vědět, jestli by se měla zobrazit jako povolené nebo zakázané. Cíl zprávy příkaz implementací poskytuje tyto informace `ON_UPDATE_COMMAND_UI` obslužná rutina příkazu. Tuto metodu použijte ke zpracování tohoto příkazu. Další informace najdete v tématu [CCmdUI – třída](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog  
 Otevře dialogové okno barvy.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `colorDefault`  
 Barvu, která je standardně vybraná, když se otevře dialogové okno barev.  
  
 [out] `colorRes`  
 Barvu, která vybrané uživatele.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud uživatel vybral barvy; `FALSE` Pokud uživatel zrušil dialogové okno barev.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="rebuild"></a>  CMFCColorBar::Rebuild  
 Úplně překreslí ovládacího prvku pruhu barev.  
  
```  
virtual void Rebuild();
```  
  
##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette  
 Nastaví logické paletu kontext zadané zařízení na paletu tlačítko nadřazeného prvku aktuální pruhu barev.  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `pDC`|Ukazatel na zařízení kontextu tlačítko nadřazeného prvku aktuální pruhu barev.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na paletu, která je nahrazena paletu tlačítko nadřazeného prvku aktuální pruhu barev.  
  
##  <a name="setcolor"></a>  CMFCColorBar::SetColor  
 Nastaví barvu, která je aktuálně vybrané.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Hodnotu barva RGB.  
  
##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName  
 Nastaví nový název pro zadaná barva.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Hodnota RGB barvy.  
  
 [v] `strName`  
 Nový název pro zadaná barva.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda mění název zadaná barva ve všech `CMFCColorBar` objekty ve vaší aplikaci.  
  
##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID  
 Nastaví nové ID příkazu pro ovládací prvek pruhu barev.  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandID`  
 ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu, pokud chcete upravit příkaz ID ovládacího prvku pruhu barev a oznámit nadřazené okno ovládacího prvku, který se změnil Identifikátor.  
  
##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors  
 Nastaví seznam barev, které se používají v aktuálním dokumentu.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszCaption`  
 Popisek, který se zobrazí, pokud není ukotven ovládacího prvku pruhu barev.  
  
 [v] `lstDocColors`  
 Seznam barev, který nahrazuje aktuální barvy dokumentu.  
  
 [v] `bShowWhenDocked`  
 `TRUE` Zobrazit barvy dokumentu, když je ukotvena ovládacího prvku pruhu barev; v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 *Barvy dokumentu* jsou barev, které jsou aktuálně používány v dokumentu. Rozhraní framework automaticky udržuje seznam barev dokumentu, ale tuto metodu můžete použít k úpravě seznamu.  
  
##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin  
 Nastaví vodorovnou okrajem, což je prostor mezi vlevo nebo vpravo barvu buňky a hranice klientské oblasti.  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nHorzMargin`  
 Vodorovné okraje v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení [CMFCColorBar::CMFCColorBar](#cmfccolorbar) konstruktor nastaví vodorovné okraj 4 pixelů.  
  
##  <a name="setproplist"></a>  CMFCColorBar::SetPropList  
 Nastaví `m_pWndPropList` chráněná data člena na zadané ukazatel do ovládacího prvku mřížky vlastnosti.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `pWndList`|Ukazatel na objekt ovládacího prvku mřížky vlastnosti.|  
  
##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin  
 Nastaví svislé okraj, který je mezery mezi barvu buňky horní nebo dolní a hranic oblasti klienta.  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nVertMargin`  
 Svislé okraje v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení [CMFCColorBar::CMFCColorBar](#cmfccolorbar) konstruktor nastaví svislé okraj 4 pixelů.  
  
##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString  
 Požadavky rámec okna, který vlastní ovládací prvek pruhu barev aktualizovat řádek zprávy ve stavovém řádku.  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiCmdId`  
 ID příkazu. (Tento parametr bude ignorován.)  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá `WM_SETMESSAGESTRING` zpráva vlastníkovi ovládacího prvku pruhu barev.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
