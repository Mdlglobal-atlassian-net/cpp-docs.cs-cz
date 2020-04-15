---
title: CmFC, stuha na pásu karet
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
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375182"
---
# <a name="cmfcribbonedit-class"></a>CmFC, stuha na pásu karet

Implementuje ovládací prvek úprav, který je umístěn na panelu pásu karet.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Vytvoří `CMFCRibbonEdit` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Označuje, zda se `CMFCRibbonEdit` výška ovládacího prvku může zvětšovat svisle do výšky řádku pásu karet.|
|[CMFCRibbonRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Vytvoří `CMFCRibbonEdit` objekt.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Zkopíruje stav zadaného `CMFCRibbonEdit` objektu `CMFCRibbonEdit` na aktuální objekt.|
|[CMFCRibbonRibbonEdit::CreateEdit](#createedit)|Vytvoří nové textové pole `CMFCRibbonEdit` pro objekt.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Zničí `CMFCRibbonEdit` objekt.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Klesne seznam.|
|[CMFCRibbonRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Povolí a nastaví rozsah číselníku pro textové pole.|
|[CMFCRibbonRibbonEdit::GetCompactSize](#getcompactsize)|Načte kompaktní velikost `CFMCRibbonEdit` objektu.|
|[CMFCRibbonRibbonEdit::GetEditText](#getedittext)|Načte text v textovém poli.|
|[CMFCRibbonRibbonEdit::GetIntermediateSize](#getintermediatesize)|Načte mezilehlou `CMFCRibbonEdit` velikost objektu.|
|[CMFCRibbonRibbonEdit::GetTextAlign](#gettextalign)|Načte zarovnání textu v textovém poli.|
|[CMFCRibbonRibbonEdit::GetWidth](#getwidth)|Načte šířku `CMFCRibbonEdit` ovládacího prvku v obrazových bodech.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Označuje, zda může `CMFCRibbonEdit` být velikost zobrazení ovládacího prvku kompaktní.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Označuje, `CMFCRIbbonEdit` zda má ovládací prvek fokus.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Označuje, zda velikost `CMFCRibbonEdit` zobrazení ovládacího prvku může být velká.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Označuje, zda je textové pole číselné tlačítko.|
|[CMFCRibbonEdit::Zvýrazněný](#ishighlighted)|Označuje, `CMFCRibbonEdit` zda je zvýrazněn ovládací prvek.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Volat rámci při změny rozměry obdélníku `CMFCRibbonEdit` zobrazení pro ovládací prvek.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Volat rámci k nakreslení ovládacího `CMFCRibbonEdit` prvku.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Volat rámci k nakreslení popisek `CMFCRibbonEdit` a obrázek pro ovládací prvek.|
|[CMFCRibbonEdit::OndrawOnList](#ondrawonlist)|Volat rámci nakreslit `CMFCRibbonEdit` ovládací prvek v seznamu příkazů.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Volat rámci povolit nebo `CMFCRibbonEdit` zakázat ovládací prvek.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Volat rámci při ukazatel zadá nebo opustí hranice `CMFCRibbonEdit` ovládacího prvku.|
|[CMFCRibbonEdit::OnKey](#onkey)|Volat rámci při stisknutí klávesy a `CMFCRibbonEdit` ovládací prvek má fokus.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Volat rámci aktualizovat `CMFCRibbonEdit` ovládací prvek, když uživatel stiskne levé tlačítko myši na ovládacím prvku.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Volat rámci při uživatel uvolní levé tlačítko myši.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Volat rámci aktualizovat ovládací `CMFCRibbonEdit` prvek při změně směru rozložení.|
|[CMFCRibbonEdit::OnShow](#onshow)|Volat rámci zobrazit nebo skrýt `CMFCRibbonEdit` ovládací prvek.|
|[CMFCRibbonEdit::Překreslit](#redraw)|Aktualizuje zobrazení ovládacího `CMFCRibbonEdit` prvku.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Nastaví data usnadnění `CMFCRibbonEdit` přístupu pro objekt.|
|[CMFCRibbonRibbonEdit::SetEditText](#setedittext)|Nastaví text v textovém poli.|
|[CMFCRibbonRibbonEdit::SetTextAlign](#settextalign)|Nastaví zarovnání textu textového pole.|
|[CMFCRibbonRibbonEdit::SetWidth](#setwidth)|Nastaví šířku textového `CMFCRibbonEdit` pole ovládacího prvku.|

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCRibbonEdit` vytvořit objekt, zobrazit tlačítka otočení vedle ovládacího prvku upravit a nastavit text ovládacího prvku pro úpravy. Tento fragment kódu je součástí [ukázky ukázky ukázky ukázky ms office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched

Označuje, zda výška ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) může zvýšit svisle na výšku řádku pásu karet.

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFCRibbonRibbonEdit::CMFCRibbonEdit

Vytvoří objekt [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] ID příkazu `CMFCRibbonEdit` pro ovládací prvek.

*nŠířka*<br/>
[v] Šířka textového pole `CMFCRibbonEdit` ovládacího prvku v obrazových bodech.

*popisek lpsz*<br/>
[v] Popisek ovládacího `CMFCRibbonEdit` prvku.

*nObrázek*<br/>
[v] Index malého obrázku, který `CMFCRibbonEdit` má být pro ovládací prvek určen. Kolekce malých obrázků je udržována nadřazenou kategorií pásu karet.

### <a name="remarks"></a>Poznámky

Ovládací `CMFCRibbonEdit` prvek nepoužívá velký obrázek.

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom

Zkopíruje stav zadaného objektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) do aktuálního objektu [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Zdrojový `CMFCRibbonEdit` objekt.

### <a name="remarks"></a>Poznámky

Parametr *src* musí být `CMFCRibbonEdit`typu .

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFCRibbonRibbonEdit::CreateEdit

Vytvoří nové textové pole pro objekt [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno objektu. `CMFCRibbonEdit`

*dwEditstyl*<br/>
[v] Určuje styl textového pole. Styly oken uvedené v části Poznámky můžete kombinovat se [styly ovládacích prvků úprav,](/windows/win32/Controls/edit-control-styles) které jsou popsány v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nové textové pole, pokud byla metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě vytvořit vlastní textové pole.

Na textové pole můžete použít následující [styly oken:](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl

Zničí objekt [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList

Klesne seznam.

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovede žádnou akci. Přepište tuto metodu a rozbalte seznam.

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFCRibbonRibbonEdit::EnableSpinButtons

Povolí a nastaví rozsah číselníku pro textové pole.

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
[v] Minimální hodnota číselníku.

*nMax*<br/>
[v] Maximální hodnota číselníku.

### <a name="remarks"></a>Poznámky

Číselná tlačítka zobrazují šipku nahoru a dolů a umožňují uživatelům procházet pevnou sadou hodnot.

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonRibbonEdit::GetCompactSize

Načte kompaktní velikost objektu [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonEdit` pro objekt.

### <a name="return-value"></a>Návratová hodnota

Kompaktní velikost objektu. `CMFCRibbonEdit`

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFCRibbonRibbonEdit::GetEditText

Načte text v textovém poli.

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>Návratová hodnota

Text v textovém poli.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonRibbonEdit::GetIntermediateSize

Načte mezilehlou velikost objektu [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonEdit` pro objekt.

### <a name="return-value"></a>Návratová hodnota

Mezilehlá velikost `CMFCRibbonEdit` objektu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFCRibbonRibbonEdit::GetTextAlign

Načte zarovnání textu v textovém poli.

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota výčtu zarovnání textu. Možné hodnoty naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je jedním z následujících stylů ovládacího prvku úprav:

- **ES_LEFT** pro zarovnání vlevo

- **ES_CENTER** pro zarovnání na střed

- **ES_RIGHT** pro správné zarovnání

Další informace o těchto stylech naleznete v [tématu Úpravy stylů ovládacích prvků](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFCRibbonRibbonEdit::GetWidth

Načte šířku ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) v obrazových bodech.

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bInFloatyMode*<br/>
[v] TRUE, `CMFCRibbonEdit` pokud je ovládací prvek v plovoucím režimu; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

Šířka `CMFCRibbonEdit` ovládacího prvku v obrazových bodech.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

Označuje, zda velikost zobrazení ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) může být kompaktní.

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu PRAVDA. Přepište tuto metodu a označte, zda může být velikost zobrazení kompaktní.

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFCRibbonEdit::HasFocus

Označuje, zda má ovládací prvek [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) fokus.

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, `CMFCRibbonEdit` pokud má ovládací prvek fokus; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

Označuje, zda velikost zobrazení ovládacího prvku [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) může být velká.

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu NEPRAVDA. Přepište tuto metodu a označte, zda může být velikost zobrazení velká.

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

Označuje, zda je textové pole číselné tlačítko.

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud textové pole má číselník; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonEdit::Zvýrazněný

Označuje, zda je zvýrazněn ovládací prvek [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, `CMFCRibbonEdit` pokud je ovládací prvek zvýrazněn; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

Volat rámci při změně rozměry obdélníku zobrazení pro ovládací prvek [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonEdit` pro ovládací prvek.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFCRibbonEdit::OnDraw

Volat rámci k nakreslení [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek.

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonEdit` pro ovládací prvek.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

Volat rámci k nakreslení popisek a obrázek pro ovládací prvek [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonEdit` pro ovládací prvek.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonEdit::OndrawOnList

Volat rámci k nakreslení OVLÁDACÍHO PRVKU [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) v seznamu příkazů.

```cpp
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonEdit` pro ovládací prvek.

*strText*<br/>
[v] Text [ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit třídy")zobrazení .

*nTextOffset*<br/>
[v] Vzdálenost v obrazových bodech od levé strany seznamu k zobrazenému textu.

*Rect*<br/>
[v] Obdélník zobrazení ovládacího `CMFCRibbonEdit` prvku.

*bIsVybrané*<br/>
[v] Tento parametr se nepoužívá.

*bZvýrazněno*<br/>
[v] Tento parametr se nepoužívá.

### <a name="remarks"></a>Poznámky

V seznamu příkazy se zobrazují ovládací prvky pásu karet, které uživatelům umožňují přizpůsobit panel nástrojů rychlý přístup.

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFCRibbonEdit::OnEnable

Volat rámci povolit nebo zakázat OVLÁDACÍ PRVEK [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE povolit ovládací prvek; Nepravda pro zakázání ovládacího prvku.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight

Volat rámci při ukazatel zadá nebo opustí hranice [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládacího prvku.

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bZvýraznění*<br/>
[v] TRUE, pokud je ukazatel v `CMFCRibbonEdit` mezích ovládacího prvku; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFCRibbonEdit::OnKey

Volat rámci při uživatel stiskne klávesu a [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ovládací prvek má fokus.

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parametry

*bIsMenuKlíč*<br/>
[v] TRUE, pokud klávesová zkratka zobrazuje rozbalovací nabídku; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla událost zpracována; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown

Volat rámci aktualizovat OVLÁDACÍ PRVEK [CMFCRibbonEdit,](../../mfc/reference/cmfcribbonedit-class.md) když uživatel stiskne levé tlačítko myši na ovládacím prvku.

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Tento parametr se nepoužívá.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Volat rámci při uživatel uvolní levé tlačítko myši.

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Tento parametr se nepoužívá.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

Volat rámci aktualizovat OVLÁDACÍ PRVEK [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) při změně směru rozložení.

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parametry

*bIsRTL*<br/>
[v] TRUE, pokud je rozložení zprava doleva; False, pokud je rozložení zleva doprava.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFCRibbonEdit::OnShow

Volat rámci zobrazit nebo skrýt OVLÁDACÍ PRVEK [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] TRUE pro zobrazení ovládacího prvku; FALSE skrýt ovládací prvek.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFCRibbonEdit::Překreslit

Aktualizuje zobrazení ovládacího prvku [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Poznámky

Tato metoda překreslí obdélník `CMFCRibbonEdit` zobrazení pro objekt nepřímo voláním [CWnd::RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) s RDW_INVALIDATE, RDW_ERASE a RDW_UPDATENOW příznaky nastaveny.

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonEdit::SetACCData

Nastaví data usnadnění přístupu pro objekt [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Ukazatel na nadřazené okno objektu. `CMFCRibbonEdit`

*Dat*<br/>
Data usnadnění přístupu `CMFCRibbonEdit` pro objekt.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFCRibbonRibbonEdit::SetEditText

Nastaví text v textovém poli.

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
[v] Text textového pole.

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFCRibbonRibbonEdit::SetTextAlign

Nastaví zarovnání textu textového pole.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nZarovnat*<br/>
[v] Hodnota výčtu zarovnání textu. Možné hodnoty naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Parametr *nAlign* je jedním z následujících stylů ovládacího prvku:

- ES_LEFT pro zarovnání vlevo

- ES_CENTER pro zarovnání na střed

- ES_RIGHT pro správné zarovnání

Další informace o těchto stylech naleznete v [tématu Úpravy stylů ovládacích prvků](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFCRibbonRibbonEdit::SetWidth

Nastaví šířku textového pole pro ovládací prvek [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
[v] Šířka textového pole v obrazových bodech.

*bInFloatyMode*<br/>
TRUE pro nastavení šířky pro plovoucí režim; FALSE pro nastavení šířky pro běžný režim.

### <a name="remarks"></a>Poznámky

Ovládací `CMFCRibbonEdit` prvek má dvě šířky v závislosti na režimu zobrazení: plovoucí režim a běžný režim.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
