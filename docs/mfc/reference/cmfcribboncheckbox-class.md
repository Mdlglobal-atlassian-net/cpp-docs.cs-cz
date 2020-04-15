---
title: Třída CMFCRIBBONCheckBox
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
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375256"
---
# <a name="cmfcribboncheckbox-class"></a>Třída CMFCRIBBONCheckBox

Třída `CMFCRibbonCheckBox` implementuje zaškrtávací políčko, které můžete přidat do panelu pásu karet, panelu nástrojů Rychlý přístup nebo místní nabídky.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonZaškrtací políčko](#cmfcribboncheckbox)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Přepíše [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonRibbonBox::GetIntermediateSize](#getintermediatesize)|(Přepíše [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonRibbonBox::GetRegularSize](#getregularsize)|(Přepíše [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepíše `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonCheckBox::Ondraw](#ondraw)|(Přepíše [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Přepíše [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OndrawOnList](#ondrawonlist)|(Přepíše `CMFCRibbonButton::OnDrawOnList`.)|
|[CmFCRibbonCheckBox::SetACCData](#setaccdata)|(Přepíše [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Poznámky

Chcete-li `CMFCRibbonCheckBox` použít ve vaší aplikaci, přidejte do kódu následující konstruktor:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

kde *nID* je zaškrtávací políčko ID příkazu a *lpszText* je textový popisek zaškrtávacího políčka.

Zaškrtávací políčko můžete přidat do panelu pásu karet pomocí [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CmFC](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonZaškrtací políčko

Zaškrtávací políčko Konstruktor objektu pásu karet

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Určuje ID příkazu.

*lpszText*<br/>
[v] Určuje popisek textu.

### <a name="return-value"></a>Návratová hodnota

Vytvoří zaškrtávací políčko pásu karet.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonCheckBox` třídy.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Po přepsání získá kompaktní velikost zaškrtávacího políčka.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na CDC přidružené k zaškrtávací políčko.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CSize` objekt, který obsahuje kompaktní velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud není přepsána, vrátí mezilehlou velikost zaškrtávacího políčka.

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonRibbonBox::GetIntermediateSize

Získá mezilehlou velikost zaškrtávacího políčka.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na cdc přidružené k tomuto zaškrtávacímu políčku.

### <a name="return-value"></a>Návratová hodnota

Objekt `CSize` obsahující mezilehlou velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud není přepsána, vypočítá mezilehlou velikost `AFX_CHECK_BOX_DEFAULT_SIZE`jako výchozí velikost zaškrtávacího políčka ( ) plus velikost textu a okraje.

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonRibbonBox::GetRegularSize

Získá pravidelné velikosti zaškrtávacího políčka.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na objekt CDC přidružený k tomuto zaškrtávacímu políčku.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CSize` objekt, který obsahuje běžnou velikost zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Pokud není přepsána, vrátí mezilehlou velikost zaškrtávacího políčka.

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Označuje, zda je k zaškrtávacímu poli přidružen obrázek popisku.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je k zaškrtávacímu políčku přidružen obrázek popisku, nebo nepravda, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::Ondraw

Volat rámci nakreslit zaškrtávací políčko pomocí kontextu zadaného zařízení.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na CDC, ve kterém chcete nakreslit zaškrtávací políčko.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Volat rámci nakreslit obrázek nabídky pro zaškrtávací políčko.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

[v] *CDC&#42;*<br/>
Ukazatel na CDC přidružené k zaškrtávací políčko.

*CRect*<br/>
[v] Objekt `CRect` určující obdélník, ve kterém chcete nakreslit obrázek nabídky.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl obrázek nakreslen, nebo nepravda, pokud ne.

### <a name="remarks"></a>Poznámky

Pokud není přepsána, vrátí hodnotu NEPRAVDA.

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OndrawOnList

Volat rámci nakreslit zaškrtávací políčko v seznamu příkazů.

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

*Pdc*<br/>
[v] Ukazatel na kontext zařízení, ve kterém chcete nakreslit zaškrtávací políčko.

*strText*<br/>
[v] Text zobrazení.

*nTextOffset*<br/>
[v] Vzdálenost v obrazových bodech od levé strany seznamu k zobrazenému textu.

*Rect*<br/>
[v] Obdélník zobrazení pro zaškrtávací políčko.

*bIsVybrané*<br/>
[v] TRUE, pokud je zaškrtnuto políčko, nebo NEPRAVDA, pokud ne.

*bZvýrazněno*<br/>
[v] TRUE, pokud je zaškrtávací políčko zvýrazněno, nebo NEPRAVDA, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CmFCRibbonCheckBox::SetACCData

Nastaví data usnadnění pro toto políčko.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Nadřazené okno zaškrtávacího políčka.

*Dat*<br/>
Data usnadnění pro zaškrtávací políčko.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda nastaví data usnadnění pro toto políčko a vždy vrátí hodnotu TRUE. Přepsat tuto metodu nastavit data usnadnění a vrátit hodnotu, která označuje úspěch nebo neúspěch.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
