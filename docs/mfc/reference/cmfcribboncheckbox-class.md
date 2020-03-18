---
title: CMFCRibbonCheckBox – třída
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
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446243"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox – třída

Třída `CMFCRibbonCheckBox` implementuje zaškrtávací políčko, které lze přidat na panel pásu karet, na panel nástrojů Rychlý přístup nebo v místní nabídce.

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
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Overrides [CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Overrides [CMFCRibbonButton:: GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Overrides [CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepisuje `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonCheckBox:: Draw](#ondraw)|(Overrides [CMFCRibbonButton:: nakreslit](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Overrides [CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Přepisuje `CMFCRibbonButton::OnDrawOnList`.)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Overrides [CMFCRibbonButton:: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Poznámky

Chcete-li ve své aplikaci použít `CMFCRibbonCheckBox`, přidejte do kódu následující konstruktor:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

kde *NID* je ID příkazu zaškrtávacího políčka a *lpszText* je textový popisek zaškrtávacího políčka.

Můžete přidat zaškrtávací políčko na panel pásu karet pomocí [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncheckbox. h

##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Konstruktor objektu zaškrtávacího políčka pásu karet

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
pro Určuje ID příkazu.

*lpszText*<br/>
pro Určuje textový popisek.

### <a name="return-value"></a>Návratová hodnota

Vytvoří objekt zaškrtávacího políčka pásu karet.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt třídy `CMFCRibbonCheckBox`.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Při přepsání získá kompaktní velikost zaškrtávacího políčka.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na CDC přidružený k zaškrtávacímu poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt `CSize`, který obsahuje kompaktní velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud není přepsán, vrátí mezilehlou velikost zaškrtávacího políčka.

##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize

Získá mezilehlou velikost zaškrtávacího políčka.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na CDC přidružený k tomuto zaškrtávacímu poli.

### <a name="return-value"></a>Návratová hodnota

Objekt `CSize`, který obsahuje mezilehlou velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud není přepsáno, vypočítá mezilehlou velikost jako výchozí velikost zaškrtávacího políčka (`AFX_CHECK_BOX_DEFAULT_SIZE`) a velikost textu a také okraje.

##  <a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize

Získá běžnou velikost zaškrtávacího políčka.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na objekt CDC přidružený k tomuto zaškrtávacímu poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt `CSize`, který obsahuje běžnou velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud není přepsán, vrátí mezilehlou velikost zaškrtávacího políčka.

##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Označuje, zda je k zaškrtávacímu poli přidružen obrázek popisku.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud je k zaškrtávacímu poli přidružen obrázek popisku nebo hodnota FALSE, pokud ne.

### <a name="remarks"></a>Poznámky

##  <a name="ondraw"></a>CMFCRibbonCheckBox:: Draw

Volá se rozhraním, aby se nakreslilo zaškrtávací políčko pomocí zadaného kontextu zařízení.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na CDC, ve kterém se má nakreslit zaškrtávací políčko

### <a name="remarks"></a>Poznámky

##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Volá se rozhraním, aby se nakreslila image nabídky pro zaškrtávací políčko.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

pro *CDC&#42;*<br/>
Ukazatel na CDC přidružený k zaškrtávacímu poli.

*CRect*<br/>
pro Objekt `CRect` určující obdélník, ve kterém se má nakreslit obrázek nabídky.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byla obrázek vykreslena, nebo hodnotu FALSE, pokud není.

### <a name="remarks"></a>Poznámky

Pokud není přepsán, vrátí hodnotu FALSE.

##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Volá se rozhraním, aby se nakreslilo zaškrtávací políčko v seznamu příkazů.

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

*Emulátor*<br/>
pro Ukazatel na kontext zařízení, ve kterém se má nakreslit zaškrtávací políčko

*strText*<br/>
pro Zobrazený text

*nTextOffset*<br/>
pro Vzdálenost v pixelech, od levé strany seznamu až po zobrazený text

*OBD*<br/>
pro Obdélník zobrazení pro zaškrtávací políčko

*bIsSelected*<br/>
pro TRUE, pokud je zaškrtnuto políčko, nebo FALSE, pokud není.

*bHighlighted*<br/>
pro TRUE, pokud je zaškrtávací políčko zvýrazněno nebo FALSE, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData

Nastaví pro zaškrtávací políčko data přístupnosti.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Nadřazené okno zaškrtávacího políčka

*údajů*<br/>
Data přístupnosti zaškrtávacího políčka.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda nastaví pro zaškrtávací políčko data přístupnosti a vždy vrátí hodnotu TRUE. Přepsáním této metody nastavíte data přístupnosti a vrátíte hodnotu, která indikuje úspěch nebo neúspěch.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
