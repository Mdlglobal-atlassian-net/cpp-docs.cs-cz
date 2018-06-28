---
title: Třída CMFCRibbonEdit | Microsoft Docs
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
ms.openlocfilehash: 2a67696289603697ddac541382d63f989881afaf
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040857"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit – třída
Implementuje ovládací prvek úprav, který se nachází na panelu pásu karet.  
  
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
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Určuje, zda výšku `CMFCRibbonEdit` řízení zvýšit svisle na výšku řádku pásu karet.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Vytvoří `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Zkopíruje stav zadaného `CMFCRibbonEdit` objektu na aktuální `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|Vytvoří nové textové pole pro `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Zničí `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Zahodí dolů pole se seznamem.|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Povolí a nastaví rozsah číselníku pro textové pole.|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Načte compact velikost `CFMCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|Načte text v textovém poli.|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Načte zprostředkující velikost `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Načte zarovnání textu v textovém poli.|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|Načte šířku v pixelech z `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Určuje, zda zobrazení velikost `CMFCRibbonEdit` řízení může být compact.|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Určuje, zda `CMFCRIbbonEdit` ovládací prvek fokus.|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Určuje, zda zobrazení velikost `CMFCRibbonEdit` řízení může být velký.|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Označuje, zda má textového pole číselníku.|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Určuje, zda `CMFCRibbonEdit` je označený ovládací prvek.|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Voláno rámcem při dimenze rámeček pro zobrazení `CMFCRibbonEdit` řízení změn.|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|Voláno rámcem kreslení `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Voláno rámcem k vykreslení popisku a bitové kopie pro `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Voláno rámcem kreslení `CMFCRibbonEdit` ovládacího prvku pole se seznamem příkazy.|  
|[CMFCRibbonEdit::OnEnable](#onenable)|Voláno rámcem chcete povolit nebo zakázat `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Voláno rámcem, když ukazatel vstoupí do nebo opustí hranice `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::OnKey](#onkey)|Voláno rámcem, když uživatel stiskne keytip a `CMFCRibbonEdit` ovládací prvek fokus.|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Voláno rámcem aktualizovat `CMFCRibbonEdit` řídit, kdy uživatel stiskne levým tlačítkem myši na ovládací prvek.|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Voláno rámcem, když uživatel uvolní levé tlačítko.|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Voláno rámcem aktualizovat `CMFCRibbonEdit` řídit, kdy rozložení změní směr.|  
|[CMFCRibbonEdit::OnShow](#onshow)|Voláno rámcem zobrazit nebo skrýt `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::Redraw](#redraw)|Aktualizace zobrazení `CMFCRibbonEdit` ovládacího prvku.|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Nastaví data pro usnadnění přístupu `CMFCRibbonEdit` objektu.|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|Nastaví text v textovém poli.|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Nastaví zarovnání textu textového pole.|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|Nastaví šířku textového pole pro `CMFCRibbonEdit` ovládacího prvku.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCRibbonEdit` objektu, zobrazit typu číselník tlačítka vedle textové pole a nastavit text ovládacích prvků pro úpravy. Tento fragment kódu je součástí [MS Office 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched  
 Určuje, zda výšku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) řízení zvýšit svisle na výšku řádku pásu karet.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit  
 Vytvoří [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nID*  
 ID pro příkaz `CMFCRibbonEdit` ovládacího prvku.  
  
 [v] *nWindth*  
 Šířka v pixelech textového pole pro `CMFCRibbonEdit` ovládacího prvku.  
  
 [v] *lpszLabel*  
 Popisek pro `CMFCRibbonEdit` ovládacího prvku.  
  
 [v] *nImage*  
 Index pro malý obrázek `CMFCRibbonEdit` ovládacího prvku. Kolekce malé bitové kopie je možný díky kategorie nadřazeného pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCRibbonEdit` Řízení nepoužívá velký obrázek.  
  
##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom  
 Zkopíruje stav zadaného [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu na aktuální [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *src*  
 Zdroj `CMFCRibbonEdit` objektu.  
  
### <a name="remarks"></a>Poznámky  
 *Src* parametr musí být typu `CMFCRibbonEdit`.  
  
##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit  
 Vytvoří nové textové pole pro [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pWndParent*  
 Ukazatel na okno nadřazené `CMFCRibbonEdit` objektu.  
  
 [v] *dwEditStyle*  
 Určuje styl textového pole. Styly oken uvedené v části poznámky s můžete kombinovat [upravit styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775464) , jsou popsány v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové textové pole, pokud metoda byla úspěšná. v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě a vytvořit vlastní textové pole.  
  
 Můžete použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) textového pole:  
  
- **WS_CHILD –**  
  
- **WS_VISIBLE –**  
  
- **WS_DISABLED –**  
  
- **WS_GROUP –**  
  
- **WS_TABSTOP –**  
  
##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl  
 Zničí [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList  
 Zahodí dolů pole se seznamem.  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci. Potlačí tuto metodu za účelem rozevírací pole se seznamem.  
  
##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons  
 Povolí a nastaví rozsah číselníku pro textové pole.  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nMin*  
 Minimální hodnota číselníku.  
  
 [v] *nMax*  
 Maximální hodnota číselníku.  
  
### <a name="remarks"></a>Poznámky  
 Otočení tlačítka zobrazit také až šipku dolů a povolit uživatelům přesunovat prostřednictvím pevnou sadu hodnot.  
  
##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize  
 Načte compact velikost [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Compact velikost `CMFCRibbonEdit` objektu.  
  
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
 Načte zprostředkující velikost [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
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
 Zarovnání textu ve výčtu objevit hodnotu. Možné hodnoty v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota je jedním z následujících styly ovládacích prvků pro úpravy:  
  
- **Es_left –** pro zarovnání doleva  
  
- **Es_center –** pro zarovnání na střed  
  
- **Es_right –** pro zarovnání doprava  
  
 Další informace o těchto styly najdete v tématu [upravit styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth  
 Načte šířku v pixelech z [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bInFloatyMode*  
 `TRUE` Pokud `CMFCRibbonEdit` ovládací prvek nachází plovoucí režimu, jinak hodnota `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka v pixelech z `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode  
 Určuje, zda zobrazení velikost [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) řízení může být compact.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vždy vrátí `TRUE`. Potlačí tuto metodu indikující, zda může mít velikost zobrazení compact.  
  
##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus  
 Určuje, zda [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek fokus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud `CMFCRibbonEdit` ovládací prvek fokus jinak `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode  
 Určuje, zda zobrazení velikost [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) řízení může být velký.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vždy vrátí `FALSE`. Potlačí tuto metodu indikující, zda zobrazení může být velký.  
  
##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons  
 Označuje, zda má textového pole číselníku.  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud má textového pole číselníku; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted  
 Určuje, zda [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) je označený ovládací prvek.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud `CMFCRibbonEdit` ovládací prvek je zvýrazněná; jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect  
 Voláno rámcem při dimenze rámeček pro zobrazení [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) řízení změn.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw  
 Voláno rámcem kreslení [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage  
 Voláno rámcem k vykreslení popisku a bitové kopie pro [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList  
 Voláno rámcem kreslení [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku pole se seznamem příkazy.  
  
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
 [v] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládacího prvku.  
  
 [v] *strText*  
 Zobrazovaný text [cmfcribbonedit třída](../../mfc/reference/cmfcribbonedit-class.md "").  
  
 [v] *nTextOffset*  
 Vzdálenost v pixelech, z levé strany zobrazovaný text v rozevíracím seznamu.  
  
 [v] *Rect –*  
 Rámeček pro zobrazení `CMFCRibbonEdit` ovládacího prvku.  
  
 [v] *bIsSelected*  
 Tento parametr není používán.  
  
 [v] *bHighlighted*  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
 Pole se seznamem příkazy zobrazí ovládacích prvků pásu karet k uživatelům umožnit přizpůsobení panelu nástrojů Rychlý přístup.  
  
##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable  
 Voláno rámcem chcete povolit nebo zakázat [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bEnable*  
 `TRUE` Chcete-li povolit ovládacího prvku; `FALSE` zakázat ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight  
 Voláno rámcem, když ukazatel vstoupí do nebo opustí hranice [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bHighlight*  
 `TRUE` Pokud je ukazatel v hranice `CMFCRibbonEdit` řízení; jinak `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey  
 Voláno rámcem, když uživatel stiskne keytip a [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek fokus.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bIsMenuKey*  
 `TRUE` Pokud keytip zobrazí místní nabídky; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byla zpracována událost; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown  
 Voláno rámcem aktualizovat [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) řídit, kdy uživatel stiskne levým tlačítkem myši na ovládací prvek.  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bodu*  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp  
 Voláno rámcem, když uživatel uvolní levé tlačítko.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bodu*  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged  
 Voláno rámcem aktualizovat [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) řídit, kdy rozložení změní směr.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bIsRTL*  
 `TRUE` Pokud je rozložení-doleva; `FALSE` Pokud je rozložení zleva doprava.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow  
 Voláno rámcem zobrazit nebo skrýt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bShow*  
 `TRUE` Chcete-li zobrazit ovládací prvek; `FALSE` ke skrytí ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw  
 Aktualizace zobrazení [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ho překreslí rámeček pro zobrazení `CMFCRibbonEdit` objekt nepřímo voláním [CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911) s `RDW_INVALIDATE`, `RDW_ERASE`, a `RDW_UPDATENOW` flags sady.  
  
##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData  
 Nastaví data pro usnadnění přístupu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objektu.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 *pParent*  
 Ukazatel do nadřazeného okna pro `CMFCRibbonEdit` objektu.  
  
 *data*  
 Data pro usnadnění přístupu `CMFCRibbonEdit` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText  
 Nastaví text v textovém poli.  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *strText*  
 Text pro textové pole.  
  
##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign  
 Nastaví zarovnání textu textového pole.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nAlign*  
 Zarovnání textu ve výčtu objevit hodnotu. Možné hodnoty v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Parametr *nAlign* je jedním z následujících upravit styly ovládacího prvku:  
  
- **Es_left –** pro zarovnání doleva  
  
- **Es_center –** pro zarovnání na střed  
  
- **Es_right –** pro zarovnání doprava  
  
 Další informace o těchto styly najdete v tématu [upravit styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth  
 Nastaví šířku textového pole pro [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nWindth*  
 Šířka v pixelech textového pole.  
  
 *bInFloatyMode*  
 `TRUE` Chcete-li nastavit šířku pro plovoucí režim; `FALSE` nastavit šířku pro regulární režim.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCRibbonEdit` Ovládací prvek má dva šířek v závislosti na jeho režimu zobrazení: plovoucí režim a režim regulární.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)