---
title: Cmfcribbonedit – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46d96d574fedf9af2fe7eb46c872819cf54a364e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216456"
---
# <a name="cmfcribbonedit-class"></a>Cmfcribbonedit – třída
Implementuje ovládací prvek úprav, který se nachází na panel pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Vytvoří `CMFCRibbonEdit` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Určuje, zda výšku `CMFCRibbonEdit` vertikálně zvýšit ovládacího prvku na výšku řádku pásu karet.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Vytvoří `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Zkopíruje stav zadaného `CMFCRibbonEdit` objektů na aktuální `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|Vytvoří nové textové pole pro `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Odstraní `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Rozbalí pole se seznamem.|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Povolí a nastaví rozsah číselníku pro textové pole.|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Načte compact velikost `CFMCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|Načte text v textovém poli.|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Načte zprostředkující velikost `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Načte zarovnání textu v textovém poli.|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|Načte šířka v pixelech, o `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Určuje, zda pro velikost zobrazení `CMFCRibbonEdit` ovládací prvek může být compact.|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Určuje, zda `CMFCRIbbonEdit` ovládací prvek má fokus.|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Určuje, zda pro velikost zobrazení `CMFCRibbonEdit` ovládacího prvku mohou být velké.|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Označuje, jestli se do textového pole typu číselník.|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Určuje, zda `CMFCRibbonEdit` zvýrazněný ovládací prvek.|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Volá se rozhraním, když dimenze zobrazovací obdélník pro `CMFCRibbonEdit` řízení změn.|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Volá se rozhraním, aby vykreslení popisku a obrázků pro `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Volá se rozhraním, chcete-li nakreslit `CMFCRibbonEdit` ovládací prvek v seznamu příkazů.|  
|[CMFCRibbonEdit::OnEnable](#onenable)|Volá se rozhraním, které chcete povolit nebo zakázat `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Volá se rozhraním, když ukazatel myši vstoupí do nebo opustí hranice `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnKey](#onkey)|Volá se rozhraním, když uživatel stiskne popisek tlačítka a `CMFCRibbonEdit` ovládací prvek má fokus.|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Volá se rozhraním, aby aktualizace `CMFCRibbonEdit` ovládací prvek, když uživatel stiskne levé tlačítko myši v ovládacím prvku.|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Volá se rozhraním, když uživatel uvolní levé tlačítko myši.|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Volá se rozhraním, aby aktualizace `CMFCRibbonEdit` ovládací prvek při změně směr rozložení.|  
|[CMFCRibbonEdit::OnShow](#onshow)|Volá se rozhraním, zobrazení nebo skrytí `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::Redraw](#redraw)|Aktualizuje zobrazení `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Nastaví data pro usnadnění pro `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|Nastaví text v textovém poli.|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Nastaví zarovnání textu v textovém poli.|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|Nastavuje šířku do textového pole u `CMFCRibbonEdit` ovládacího prvku.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCRibbonEdit` objekt zobrazení tlačítka typu číselník vedle ovládacího prvku pro úpravy a nastavit text ovládacího prvku pro úpravy. Tento fragment kódu je součástí [MS Office 2007 demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched  
 Určuje, zda výšku [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) vertikálně zvýšit ovládacího prvku na výšku řádku pásu karet.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 vždy vrátí hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit  
 Vytvoří [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nID*  
 Pro ID příkazu `CMFCRibbonEdit` ovládacího prvku.  
  
 [in] *nWidth*  
 Šířka v pixelech, v textovém poli pro `CMFCRibbonEdit` ovládacího prvku.  
  
 [in] *lpszLabel*  
 Popisek `CMFCRibbonEdit` ovládacího prvku.  
  
 [in] *nvybrán Nobrázek*  
 Index malý obrázek pro `CMFCRibbonEdit` ovládacího prvku. Kolekce malé obrázky se spravuje pomocí nadřazené kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCRibbonEdit` Ovládací prvek nepoužívá velký obrázek.  
  
##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom  
 Zkopíruje stav zadaného [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektů na aktuální [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *src*  
 Zdroj `CMFCRibbonEdit` objektu.  
  
### <a name="remarks"></a>Poznámky  
 *Src* parametr musí být typu `CMFCRibbonEdit`.  
  
##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit  
 Vytvoří nové textové pole pro [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWndParent*  
 Ukazatel do nadřazeného okna `CMFCRibbonEdit` objektu.  
  
 [in] *dwEditStyle*  
 Určuje styl do textového pole. Styly oken uvedených v části poznámky s můžete kombinovat [styly ovládacího prvku pro úpravy](/windows/desktop/Controls/edit-control-styles) , které jsou popsány v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové textové pole, pokud metoda byla úspěšná. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě k vytvoření vlastní textové pole.  
  
 Můžete použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do textového pole:  
  
- **WS_CHILD**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl  
 Odstraní [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList  
 Rozbalí pole se seznamem.  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda nemá žádný účinek. Potlačí tuto metodu za účelem rozevírací seznam pole se seznamem.  
  
##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons  
 Povolí a nastaví rozsah číselníku pro textové pole.  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Nminimum*  
 Minimální hodnotu číselníku.  
  
 [in] *Nmaximum*  
 Maximální hodnotu číselníku.  
  
### <a name="remarks"></a>Poznámky  
 Číselníků zobrazení nahoru a Šipka dolů a umožňují uživatelům procházení pevnou sadu hodnot.  
  
##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize  
 Načte compact velikost [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kompaktní velikost `CMFCRibbonEdit` objektu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText  
 Načte text v textovém poli.  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Text v textovém poli.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize  
 Načte zprostředkující velikost [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zprostředkující velikost `CMFCRibbonEdit` objektu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign  
 Načte zarovnání textu v textovém poli.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Textová hodnota zarovnání ve výčtu. Možné hodnoty v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota je jeden z následujících – styly ovládacího prvku úprav:  
  
- **ES_LEFT** pro zarovnání doleva  
  
- **ES_CENTER** pro zarovnání na střed  
  
- **ES_RIGHT** pro zarovnání doprava  
  
 Další informace o těchto stylů, najdete v části [upravit styly ovládacího prvku](/windows/desktop/Controls/edit-control-styles).  
  
##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth  
 Načte šířka v pixelech, o [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bInFloatyMode*  
 Hodnota TRUE, pokud `CMFCRibbonEdit` ovládací prvek je v režimu s plovoucí desetinnou čárkou; jinak hodnota FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka v pixelech, o `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode  
 Určuje, zda pro velikost zobrazení [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek může být compact.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vždy vrátí hodnotu TRUE. Přepsáním této metody můžete určit, jestli je možné compact velikost zobrazení.  
  
##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus  
 Určuje, zda [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek má fokus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `CMFCRibbonEdit` ovládací prvek má fokus, jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode  
 Určuje, zda pro velikost zobrazení [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku mohou být velké.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 vždy vrátí hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vždy vrátí hodnotu FALSE. Potlačí tuto metodu, která označuje, zda zobrazení může být velký.  
  
##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons  
 Označuje, jestli se do textového pole typu číselník.  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud textové pole má číselníku; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted  
 Určuje, zda [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) zvýrazněný ovládací prvek.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `CMFCRibbonEdit` ovládací prvek je zvýrazněný; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect  
 Volá se rozhraním, když dimenze zobrazovací obdélník pro [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) řízení změn.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw  
 Volá se rozhraním, chcete-li nakreslit [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage  
 Volá se rozhraním, aby vykreslení popisku a obrázků pro [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList  
 Volá se rozhraním, chcete-li nakreslit [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek v seznamu příkazů.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
 [in] *strText*  
 Zobrazovaný text [](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit třída").  
  
 [in] *nTextOffset*  
 Vzdálenost v pixelech na levé straně pole se seznamem k zobrazení textu.  
  
 [in] *rect*  
 Obdélník zobrazení pro `CMFCRibbonEdit` ovládacího prvku.  
  
 [in] *bIsSelected*  
 Tento parametr není používán.  
  
 [in] *bHighlighted*  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
 Pole se seznamem příkazy zobrazí ovládací prvky pásu karet k uživatelům umožnit přizpůsobení panelu nástrojů Rychlý přístup.  
  
##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable  
 Volá se rozhraním, které chcete povolit nebo zakázat [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bEnable*  
 TRUE, pokud chcete povolte stažení ovládacího prvku; FALSE, pokud chcete zakázat ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight  
 Volá se rozhraním, když ukazatel myši vstoupí do nebo opustí hranice [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bHighlight*  
 Hodnota TRUE, pokud je ukazatel myši v ohraničené `CMFCRibbonEdit` řízení; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey  
 Volá se rozhraním, když uživatel stiskne popisek tlačítka a [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek má fokus.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bIsMenuKey*  
 Hodnota TRUE, pokud je klávesová zkratka zobrazí místní nabídka; v opačném případě hodnota FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud událost byla zpracována; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown  
 Volá se rozhraním, aby aktualizace [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek, když uživatel stiskne levé tlačítko myši v ovládacím prvku.  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bodu*  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp  
 Volá se rozhraním, když uživatel uvolní levé tlačítko myši.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bodu*  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged  
 Volá se rozhraním, aby aktualizace [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek při změně směr rozložení.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bIsRTL*  
 Hodnota TRUE v případě rozložení je right to left; FALSE, pokud je rozložení zleva doprava.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow  
 Volá se rozhraním, zobrazení nebo skrytí [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShow*  
 TRUE, pokud chcete zobrazit ovládací prvek; FALSE, pokud chcete skrýt ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw  
 Aktualizuje zobrazení [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda překreslí zobrazovací obdélník pro `CMFCRibbonEdit` nepřímo zavoláním [CWnd::RedrawWindow](/windows/desktop/api/winuser/nf-winuser-redrawwindow) Flags RDW_INVALIDATE RDW_ERASE a RDW_UPDATENOW nastavit.  
  
##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData  
 Nastaví data pro usnadnění pro [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 *pParent*  
 Ukazatel do nadřazeného okna pro `CMFCRibbonEdit` objektu.  
  
 *data*  
 Usnadnění data `CMFCRibbonEdit` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText  
 Nastaví text v textovém poli.  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strText*  
 Text do textového pole.  
  
##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign  
 Nastaví zarovnání textu v textovém poli.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nAlign*  
 Textová hodnota zarovnání ve výčtu. Možné hodnoty v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Parametr *nAlign* je jedním z následujících úprav – styly ovládacích prvků:  
  
- ES_LEFT pro zarovnání doleva  
  
- ES_CENTER pro zarovnání na střed  
  
- ES_RIGHT pro zarovnání doprava  
  
 Další informace o těchto stylů, najdete v části [upravit styly ovládacího prvku](/windows/desktop/Controls/edit-control-styles).  
  
##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth  
 Nastavuje šířku do textového pole u [cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nWidth*  
 Šířka v pixelech, v textovém poli.  
  
 *bInFloatyMode*  
 TRUE, pokud chcete nastavit šířku pro režim s plovoucí desetinnou čárkou. FALSE, pokud chcete nastavit šířku běžného režimu.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCRibbonEdit` Ovládací prvek má dva šířku v závislosti na jeho režimu zobrazení: s plovoucí desetinnou čárkou a pravidelné režimu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfcribbonbutton – třída](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)