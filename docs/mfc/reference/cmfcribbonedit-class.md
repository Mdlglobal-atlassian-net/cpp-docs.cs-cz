---
title: CMFCRibbonEdit – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 4f973074fbec3d04b1c1a74852b02ff2564217c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504953"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit – třída

Implementuje ovládací prvek pro úpravy, který je umístěn na panelu pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|`CMFCRibbonEdit` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Označuje, zda se výška `CMFCRibbonEdit` ovládacího prvku může zvětšit svisle na výšku řádku pásu karet.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|`CMFCRibbonEdit` Vytvoří objekt.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Zkopíruje stav zadaného `CMFCRibbonEdit` objektu do aktuálního `CMFCRibbonEdit` objektu.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Vytvoří nové textové pole pro `CMFCRibbonEdit` objekt.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|`CMFCRibbonEdit` Odstraní objekt.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Zruší seznam.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Povolí a nastaví rozsah číselníku pro textové pole.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Načte kompaktní velikost `CFMCRibbonEdit` objektu.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Načte text v textovém poli.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Načte mezilehlé velikosti `CMFCRibbonEdit` objektu.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Načte zarovnání textu v textovém poli.|
|[CMFCRibbonEdit:: getwidth](#getwidth)|Načte šířku `CMFCRibbonEdit` ovládacího prvku v pixelech.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Označuje, zda může být velikost zobrazení `CMFCRibbonEdit` pro ovládací prvek komprimována.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Určuje, zda `CMFCRIbbonEdit` má ovládací prvek fokus.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Označuje, zda velikost zobrazení pro `CMFCRibbonEdit` ovládací prvek může být velká.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Označuje, zda je v textovém poli tlačítko číselníku.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Označuje, zda `CMFCRibbonEdit` je ovládací prvek zvýrazněn.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Volá se rozhraním, když se změní rozměry obdélníku `CMFCRibbonEdit` zobrazení ovládacího prvku.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Volá se rozhraním, aby se `CMFCRibbonEdit` nakreslil ovládací prvek.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Volá se rozhraním, aby se nakreslil popisek a obrázek `CMFCRibbonEdit` ovládacího prvku.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Volá se rozhraním, aby se `CMFCRibbonEdit` ovládací prvek nakreslil v seznamu příkazů.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Volá se rozhraním, aby se povolil nebo `CMFCRibbonEdit` zakázal ovládací prvek.|
|[CMFCRibbonEdit:: inzvýrazňovat](#onhighlight)|Volá se rozhraním, když ukazatel vloží nebo opustí hranice `CMFCRibbonEdit` ovládacího prvku.|
|[CMFCRibbonEdit::OnKey](#onkey)|Volá se rozhraním, když uživatel stiskne KeyTip a `CMFCRibbonEdit` ovládací prvek má fokus.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Volá se rozhraním, aby se `CMFCRibbonEdit` aktualizoval ovládací prvek, když uživatel stiskne levé tlačítko myši na ovládacím prvku.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Volá se rozhraním, když uživatel uvolní levé tlačítko myši.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Volá se rozhraním, aby se `CMFCRibbonEdit` aktualizoval ovládací prvek, když se změní směr rozvržení.|
|[CMFCRibbonEdit::OnShow](#onshow)|Volá se rozhraním pro zobrazení nebo skrytí `CMFCRibbonEdit` ovládacího prvku.|
|[CMFCRibbonEdit:: redraw](#redraw)|Aktualizuje zobrazení `CMFCRibbonEdit` ovládacího prvku.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Nastaví data přístupnosti pro `CMFCRibbonEdit` objekt.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Nastaví text v textovém poli.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Nastaví zarovnání textu v textovém poli.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Nastaví šířku textového pole pro `CMFCRibbonEdit` ovládací prvek.|

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCRibbonEdit` objekt, Zobrazit tlačítka vedle ovládacího prvku pro úpravy a nastavit text ovládacího prvku pro úpravy. Tento fragment kódu je součástí [ukázky ukázky sady MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonEdit. h

##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched

Určuje, zda se výška ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) může zvětšit svisle na výšku řádku pásu karet.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

Vytvoří objekt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parametry

*nID*<br/>
pro ID příkazu pro `CMFCRibbonEdit` ovládací prvek

*nWidth*<br/>
pro Šířka textového pole `CMFCRibbonEdit` ovládacího prvku v pixelech

*lpszLabel*<br/>
pro Popisek `CMFCRibbonEdit` ovládacího prvku

*nImage*<br/>
pro Index malého obrázku, který má být použit pro `CMFCRibbonEdit` ovládací prvek Kolekce malých obrázků je udržována nadřazenou kategorií pásu karet.

### <a name="remarks"></a>Poznámky

`CMFCRibbonEdit` Ovládací prvek nepoužívá velký obrázek.

##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom

Zkopíruje stav zadaného objektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) do aktuálního objektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
pro Zdrojový `CMFCRibbonEdit` objekt.

### <a name="remarks"></a>Poznámky

Parametr *Src* musí být typu `CMFCRibbonEdit`.

##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit

Vytvoří nové textové pole pro objekt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nadřazené okno `CMFCRibbonEdit` objektu.

*dwEditStyle*<br/>
pro Určuje styl textového pole. Můžete zkombinovat styly oken uvedené v části poznámky pomocí [stylů textových ovládacích prvků](/windows/win32/Controls/edit-control-styles) , které jsou popsány v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nové textové pole, pokud byla metoda úspěšná; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Přepsáním této metody v odvozené třídě vytvoříte vlastní textové pole.

V textovém poli můžete použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) :

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>CMFCRibbonEdit::D estroyCtrl

Odstraní objekt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Poznámky

##  <a name="dropdownlist"></a>CMFCRibbonEdit::D ropDownList

Zruší seznam.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovádí žádnou akci. Tuto metodu přepište, pokud chcete rozevírací seznam vyřadit.

##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

Povolí a nastaví rozsah číselníku pro textové pole.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
pro Minimální hodnota tlačítka číselníku

*Nmaximum*<br/>
pro Maximální hodnota tlačítka číselníku

### <a name="remarks"></a>Poznámky

Tlačítka se zobrazují se šipkou nahoru a dolů a umožňují uživatelům přesouvat pevně danou sadu hodnot.

##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize

Načte kompaktní velikost objektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení pro `CMFCRibbonEdit` objekt.

### <a name="return-value"></a>Návratová hodnota

Kompaktní velikost `CMFCRibbonEdit` objektu.

### <a name="remarks"></a>Poznámky

##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText

Načte text v textovém poli.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Návratová hodnota

Text v textovém poli

### <a name="remarks"></a>Poznámky

##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize

Načte mezilehlé velikosti objektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení pro `CMFCRibbonEdit` objekt.

### <a name="return-value"></a>Návratová hodnota

Střední velikost `CMFCRibbonEdit` objektu.

### <a name="remarks"></a>Poznámky

##  <a name="gettextalign"></a>CMFCRibbonEdit:: gettextalign

Načte zarovnání textu v textovém poli.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota ve výčtu zarovnání textu. Možné hodnoty jsou uvedeny v části poznámky.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je jeden z následujících stylů ovládacích prvků pro úpravy:

- **ES_LEFT** pro zarovnání doleva

- **ES_CENTER** pro zarovnání na střed

- **ES_RIGHT** pro správné zarovnání

Další informace o těchto stylech naleznete v tématu [Editing Control Styles](/windows/win32/Controls/edit-control-styles).

##  <a name="getwidth"></a>CMFCRibbonEdit:: getwidth

Načte šířku ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) v pixelech.

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bInFloatyMode*<br/>
pro TRUE, pokud `CMFCRibbonEdit` je ovládací prvek v plovoucím režimu. v opačném případě false.

### <a name="return-value"></a>Návratová hodnota

Šířka `CMFCRibbonEdit` ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

Označuje, zda lze komprimovat velikost zobrazení pro ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu TRUE. Tuto metodu přepište, pokud chcete určit, zda může být velikost zobrazení komprimována.

##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus

Určuje, zda má ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud `CMFCRibbonEdit` má ovládací prvek fokus; v opačném případě false.

### <a name="remarks"></a>Poznámky

##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

Označuje, zda velikost zobrazení pro ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) může být velká.

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždycky vrátí hodnotu FALSE. Tuto metodu přepište, pokud chcete určit, zda může být velikost zobrazení velká.

##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

Označuje, zda je v textovém poli tlačítko číselníku.

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud má textové pole tlačítko číselníku; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="ishighlighted"></a>CMFCRibbonEdit::-zvýrazňovat

Určuje, zda je zvýrazněn ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, je `CMFCRibbonEdit` -li ovládací prvek zvýrazněn; v opačném případě false.

### <a name="remarks"></a>Poznámky

##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

Volá se rozhraním, když se změní rozměry obdélníku zobrazení pro změnu ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládací prvek.

### <a name="remarks"></a>Poznámky

##  <a name="ondraw"></a>CMFCRibbonEdit:: Draw

Volá se rozhraním, aby se nakreslil ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládací prvek.

### <a name="remarks"></a>Poznámky

##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

Volá se rozhraním, aby se nakreslil popisek a obrázek pro ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládací prvek.

### <a name="remarks"></a>Poznámky

##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList

Volá se rozhraním, aby se nakreslil ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) v seznamu příkazů.

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

*pDC*<br/>
pro Ukazatel na kontext zařízení pro `CMFCRibbonEdit` ovládací prvek.

*strText*<br/>
pro Třída zobrazovaného [ ]textu (../../mfc/reference/cmfcribbonedit-class.md "CMFCRibbonEdit")

*nTextOffset*<br/>
pro Vzdálenost v pixelech, od levé strany seznamu až po zobrazený text

*OBD*<br/>
pro Obdélník `CMFCRibbonEdit` zobrazení ovládacího prvku

*bIsSelected*<br/>
pro Tento parametr se nepoužívá.

*bHighlighted*<br/>
pro Tento parametr se nepoužívá.

### <a name="remarks"></a>Poznámky

Seznam příkazy zobrazí ovládací prvky pásu karet, které uživatelům umožňují přizpůsobit panel nástrojů Rychlý přístup.

##  <a name="onenable"></a>CMFCRibbonEdit::-Enable

Volá se rozhraním, aby se povolil nebo zakázal ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE pro povolení ovládacího prvku; FALSE pro zakázání ovládacího prvku

### <a name="remarks"></a>Poznámky

##  <a name="onhighlight"></a>CMFCRibbonEdit:: inzvýrazňovat

Volá se rozhraním, když ukazatel vloží nebo opustí hranice ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
pro TRUE, pokud je ukazatel v mezích `CMFCRibbonEdit` ovládacího prvku; v opačném případě false.

### <a name="remarks"></a>Poznámky

##  <a name="onkey"></a>CMFCRibbonEdit::OnKey

Volá se rozhraním, když uživatel stiskne KeyTip a ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) má fokus.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parametry

*bIsMenuKey*<br/>
pro TRUE, pokud KeyTip zobrazí místní nabídku; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla událost zpracována; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown

Volá se rozhraním, aby se aktualizoval ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) , když uživatel stiskne levé tlačítko myši na ovládacím prvku.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
pro Tento parametr se nepoužívá.

### <a name="remarks"></a>Poznámky

##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Volá se rozhraním, když uživatel uvolní levé tlačítko myši.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
pro Tento parametr se nepoužívá.

### <a name="remarks"></a>Poznámky

##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

Volá se rozhraním, aby se aktualizoval ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) , když se změní směr rozvržení.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parametry

*bIsRTL*<br/>
pro TRUE, pokud je rozložení zprava doleva; FALSE, pokud je rozložení zleva doprava.

### <a name="remarks"></a>Poznámky

##  <a name="onshow"></a>CMFCRibbonEdit:: inshow

Volá se rozhraním, aby se zobrazil nebo skryl ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
pro TRUE pro zobrazení ovládacího prvku; FALSE pro skrytí ovládacího prvku

### <a name="remarks"></a>Poznámky

##  <a name="redraw"></a>CMFCRibbonEdit:: redraw

Aktualizuje zobrazení ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void Redraw();
```

### <a name="remarks"></a>Poznámky

Tato metoda překreslí zobrazovací obdélník pro `CMFCRibbonEdit` objekt nepřímo voláním [CWnd:: RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) se sadou příznaků RDW_INVALIDATE, RDW_ERASE a RDW_UPDATENOW.

##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData

Nastaví data přístupnosti pro objekt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Ukazatel na nadřazené okno `CMFCRibbonEdit` objektu.

*data*<br/>
Data přístupnosti pro `CMFCRibbonEdit` objekt.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText

Nastaví text v textovém poli.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
pro Text textového pole

##  <a name="settextalign"></a>CMFCRibbonEdit:: členskou

Nastaví zarovnání textu v textovém poli.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nAlign*<br/>
pro Hodnota ve výčtu zarovnání textu. Možné hodnoty jsou uvedeny v části poznámky.

### <a name="remarks"></a>Poznámky

Parametr *nAlign* je jedním z následujících stylů ovládacích prvků pro úpravy:

- ES_LEFT pro zarovnání doleva

- ES_CENTER pro zarovnání na střed

- ES_RIGHT pro správné zarovnání

Další informace o těchto stylech naleznete v tématu [Editing Control Styles](/windows/win32/Controls/edit-control-styles).

##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth

Nastaví šířku textového pole pro ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
pro Šířka textového pole v pixelech

*bInFloatyMode*<br/>
TRUE pro nastavení šířky pro plovoucí režim; FALSE pro nastavení šířky pro normální režim.

### <a name="remarks"></a>Poznámky

`CMFCRibbonEdit` Ovládací prvek má dvě šířky v závislosti na režimu zobrazení: plovoucí režim a běžný režim.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
