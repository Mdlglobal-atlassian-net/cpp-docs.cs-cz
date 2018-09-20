---
title: Cmfcribbonslider – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d53f1911073312b6ff8f5b9b2a1772205108244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386209"
---
# <a name="cmfcribbonslider-class"></a>Cmfcribbonslider – třída

`CMFCRibbonSlider` Třída implementuje posuvník, který můžete přidat na stavový panel pásu karet nebo panel pásu karet. V ovládacím prvku posuvník pásu karet se podobá posuvníkům pro zvětšení, které se zobrazují v aplikacích sady Office 2007.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Vytvoří a inicializuje ovládací prvek posuvník pásu karet.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Vrátí aktuální pozici v ovládacím prvku posuvník.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Vrátí maximální hodnotu jezdce.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Vrátí minimální hodnotu posuvníku.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Vrátí regulární velikost elementu pásu karet. (Přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Vrátí velikost položky přírůstek zvětšení pro ovládací prvek posuvník.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Určuje, zda posuvník má tlačítka lupy.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit prvek pásu karet. (Přepíše [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Nastaví aktuální umístění v ovládacím prvku posuvník.|
|[CMFCRibbonSlider::SetRange](#setrange)|Určuje oblast v ovládacím prvku posuvník tak, že nastavíte minimální a maximální hodnoty.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Zobrazí nebo skryje tlačítka lupy.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Nastaví velikost přírůstek zvětšení pro ovládací prvek posuvník.|

## <a name="remarks"></a>Poznámky

Můžete použít `SetRange` metoda konfiguraci rozsahu přiblížení navyšuje pro posuvník. Aktuální pozice posuvníku můžete nastavit pomocí `SetPos` metody.

Tlačítka cyklické přiblížení na levé a pravé straně ovládacího prvku posuvník, můžete zobrazit pomocí `SetZoomButtons` metody. Ve výchozím nastavení, je vodorovný posuvník, tlačítko vlevo přiblížení zobrazí znaménko minus a tlačítko vpravo přiblížení znaménko plus.

`SetZoomIncrement` Metoda definuje přírůstek přidat k nebo odečíst od aktuální pozice po kliknutí tlačítka lupy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonSlider` třídy můžete nastavit vlastnosti posuvníku. Tento příklad ukazuje, jak vytvořit `CMFCRibbonSlider` objektu, zobrazení tlačítka lupy, nastaví aktuální pozici v ovládacím prvku posuvník a nastavte rozsah hodnot pro ovládací prvek posuvník.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Cmfcribbonslider –](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonslider.h

##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider

Vytvořte ovládací prvek posuvník pásu karet.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] ID posuvníku.

[in]. *nWidth* posuvník šířka v pixelech.

### <a name="remarks"></a>Poznámky

Vytvoří ovládací prvek posuvník pásu karet je *nWidth* pixelů na šířku v kategorii panelu ve kterém se přidá posuvníku. Ve výchozím nastavení je vodorovný posuvník.

##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos

Vrátí aktuální pozici v ovládacím prvku posuvník.

```
int GetPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice posuvníku, což je pozice vzhledem k začátku posuvníku.

##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax

Získá maximální přírůstek posuvníku, která jezdce můžete projít v ovládacím prvku posuvník.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální přírůstek posuvníku, která jezdce můžete projít v ovládacím prvku posuvník.

##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin

Vrátí minimální přírůstek, která jezdce můžete projít v ovládacím prvku posuvník.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální přírůstek, která jezdce můžete projít v ovládacím prvku posuvník.

##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *primárního řadiče domény*

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement

Získáte přírůstek zvětšení pro ovládací prvek posuvník.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Návratová hodnota

Přírůstek zvětšení pro ovládací prvek posuvník.

##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons

Určuje, zda posuvník má tlačítka lupy.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud má posuvník přiblížení tlačítka; FALSE v opačném případě.

##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *primárního řadiče domény*

### <a name="remarks"></a>Poznámky

##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos

Nastavte aktuální pozici v ovládacím prvku posuvník.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*nPos –*<br/>
[in] Určuje pozici pro posuvník. Pozice je relativní vzhledem k začátku posuvníku.

*bRedraw*<br/>
[in] Pokud je hodnota TRUE, bude se měl překreslit posuvníku.

##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange

Nastavte rozsah hodnot pro ovládací prvek posuvník.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*Nminimum*<br/>
[in] Určuje minimální hodnotu v ovládacím prvku posuvník.

*Nmaximum*<br/>
[in] Určuje maximální hodnotu v ovládacím prvku posuvník.

### <a name="remarks"></a>Poznámky

Určuje rozsah hodnot pro ovládací prvek posuvník tak, že nastavíte minimální a maximální hodnoty.

##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons

Zobrazení nebo skrytí tlačítka lupy.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parametry

[in]. *bSet* true tlačítka pro přiblížení zobrazení; FALSE, pokud chcete skrýt.

##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement

Nastavte přírůstek zvětšení pro ovládací prvek posuvník.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parametry

*nZoomIncrement*<br/>
[in] Určuje přírůstek zvětšení v ovládacím prvku posuvník.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)
