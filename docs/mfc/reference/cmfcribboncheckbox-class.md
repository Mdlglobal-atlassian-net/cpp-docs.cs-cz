---
title: Cmfcribboncheckbox – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 34af1ae818125abd51b9eaf04cd98f9ac24addb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392541"
---
# <a name="cmfcribboncheckbox-class"></a>Cmfcribboncheckbox – třída

`CMFCRibbonCheckBox` Třída implementuje zaškrtávací políčko, které můžete přidat do nabídky pásu karet panelu, v panelu nástrojů Rychlý přístup nebo automaticky otevíraného okna.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Přepíše [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Přepíše [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Přepíše [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepíše `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Přepíše [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Přepíše [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Přepíše `CMFCRibbonButton::OnDrawOnList`.)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Přepíše [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Poznámky

Použití `CMFCRibbonCheckBox` ve vaší aplikaci, přidejte následující konstruktor do kódu:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```
kde *nID* je Identifikátor příkazu zaškrtávací políčko a *lpszText* je textový popisek zaškrtávacího políčka.

Zaškrtávací políčko můžete přidat do panelu pásu karet pomocí [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncheckbox.h

##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox

Konstruktor objektu zaškrtávacího políčka pásu karet

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Určuje ID příkazu.

*lpszText*<br/>
[in] Určuje textový popisek.

### <a name="return-value"></a>Návratová hodnota

Vytvoří objekt zaškrtávacího políčka pásu karet.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonCheckBox` třídy.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize

Při přepisu, získá compact velikost zaškrtávacího políčka.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na funkci CDC přidružené k zaškrtnutí políčka.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CSize` objekt, který obsahuje compact velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud přepsána nebyla, vrátí zprostředkující velikost zaškrtávacího políčka.

##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize

Získá zprostředkující velikost zaškrtávacího políčka.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na funkci CDC přidružené toto zaškrtávací políčko.

### <a name="return-value"></a>Návratová hodnota

A `CSize` objekt, který obsahuje zprostředkující velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud přepsána nebyla, vypočítá velikost zprostředkující jako výchozí velikost zaškrtávacího políčka ( `AFX_CHECK_BOX_DEFAULT_SIZE`) plus velikost textu a okraje.

##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize

Získá regulární velikost zaškrtávacího políčka.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na funkci CDC objekt přidružený k toto zaškrtávací políčko.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CSize` objekt, který obsahuje regulární velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud přepsána nebyla, vrátí zprostředkující velikost zaškrtávacího políčka.

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage

Určuje, zda je popis obrázku přidružený k zaškrtnutí políčka.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je popis obrázku přidružený k zaškrtnutí políčka, nebo hodnotu FALSE, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw

Volá se rozhraním, chcete-li nakreslit zaškrtávací políčko pomocí kontextu zařízení.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na funkci CDC, ve kterém chcete-li nakreslit zaškrtávací políčko.

### <a name="remarks"></a>Poznámky

##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage

Volá se rozhraním, chcete-li nakreslit obrázek nabídky pro zaškrtávací políčko.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

[in] *CDC&#42;*<br/>
Ukazatel na funkci CDC přidružené k zaškrtnutí políčka.

*Crect –*<br/>
[in] A `CRect` určující obdélník, ve kterém chcete-li nakreslit obrázek nabídky.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byl nakreslen bitovou kopii nebo hodnotu NEPRAVDA, pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Pokud přepsána nebyla, vrátí hodnotu FALSE.

##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList

Volá se rozhraním, chcete-li nakreslit zaškrtávací políčko v seznamu příkazů.

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
[in] Ukazatel na kontext zařízení, ve kterém chcete-li nakreslit zaškrtávací políčko.

*strText*<br/>
[in] Zobrazení textu.

*nTextOffset*<br/>
[in] Vzdálenost v pixelech na levé straně pole se seznamem k zobrazení textu.

*Rect*<br/>
[in] Obdélník zobrazení pro zaškrtávací políčko.

*bIsSelected*<br/>
[in] TRUE, pokud je toto políčko vybrané, nebo hodnotu FALSE, pokud není.

*bHighlighted*<br/>
[in] TRUE, pokud je toto políčko zvýrazněné nebo hodnotu NEPRAVDA, pokud tomu tak není.

### <a name="remarks"></a>Poznámky

##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData

Nastaví data pro usnadnění pro zaškrtávací políčko.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Nadřazené okno zaškrtávacího políčka.

*data*<br/>
Data pro usnadnění pro zaškrtávací políčko.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda nastaví data pro usnadnění pro zaškrtávací políčko a vždy vrátí hodnotu TRUE. Potlačí tuto metodu za účelem usnadnění dat a vrátí hodnotu udávající úspěch nebo neúspěch.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
