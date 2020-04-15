---
title: CMFCRibbonSlider – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: f2a05ca1433ca3a44b0459360e3f09fe7a274c68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368835"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider – třída

Třída `CMFCRibbonSlider` implementuje ovládací prvek posuvníku, který můžete přidat na panel pásu karet nebo na stavový řádek pásu karet. Ovládací prvek posuvníku pásu karet se podobá jezdcům lupy, které se zobrazují v aplikacích sady Office 2007.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Vytvoří a inicializuje ovládací prvek jezdce pásu karet.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Vrátí aktuální pozici ovládacího prvku posuvníku.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Vrátí maximální hodnotu jezdce.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Vrátí minimální hodnotu jezdce.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Vrátí běžnou velikost prvku pásu karet. (Přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Vrátí velikost přírůstku zvětšení pro ovládací prvek posuvníku.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Určuje, zda má posuvník tlačítka lupy.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Volat rámci k nakreslení prvku pásu karet. (Přepíše [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Nastaví aktuální polohu ovládacího prvku posuvníku.|
|[CMFCRibbonSlider::SetRange](#setrange)|Určuje rozsah ovládacího prvku posuvníku nastavením minimálních a maximálních hodnot.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Zobrazí nebo skryje tlačítka lupy.|
|[CMFCRibbonSlider::NastavitIninzvýšení](#setzoomincrement)|Nastaví velikost přírůstku zvětšení pro ovládací prvek posuvníku.|

## <a name="remarks"></a>Poznámky

`SetRange` Pomocí této metody můžete nakonfigurovat rozsah přírůstků zvětšení pro posuvník. Aktuální polohu jezdce můžete nastavit pomocí `SetPos` metody.

Pomocí metody můžete zobrazit kruhová tlačítka lupy na levé `SetZoomButtons` a pravé straně ovládacího prvku posuvníku. Ve výchozím nastavení je posuvník vodorovný, levé tlačítko lupy zobrazuje znaménko mínus a pravé tlačítko lupy zobrazuje znaménko plus.

Metoda `SetZoomIncrement` definuje přírůstek, který má být připojován nebo odečítán od aktuální pozice, když uživatel klepne na tlačítka lupy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonSlider` metody ve třídě nastavit vlastnosti jezdce. Příklad ukazuje, jak `CMFCRibbonSlider` vytvořit objekt, zobrazit tlačítka lupy, nastavit aktuální polohu ovládacího prvku posuvníku a nastavit rozsah hodnot pro ovládací prvek posuvníku.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonslider.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider

Vytvořte jezdec pásu karet.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] ID jezdce.

[v]. *nŠířka* Šířka jezdce v obrazových bodech.

### <a name="remarks"></a>Poznámky

Vytvoří jezdec pásu karet, který je *nWidth* pixelů široký v kategorii panelu, kde je přidán jezdec. Ve výchozím nastavení je jezdec vodorovný.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFCRibbonSlider::GetPos

Vrátí aktuální pozici ovládacího prvku posuvníku.

```
int GetPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální poloha ovládacího prvku posuvníku, což je poloha vzhledem k začátku jezdce.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax

Získá maximální přírůstek jezdce, který může jezdec cestovat na ovládacím prvku jezdce.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální přírůstek jezdce, který může jezdec projet na ovládacím prvku jezdce.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin

Vrátí minimální přírůstek, který může jezdec u jezdce projet.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální přírůstek, který může jezdec projet na ovládacím prvku posuvníku.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement

Získejte přírůstek zvětšení pro ovládací prvek posuvníku.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Návratová hodnota

Přírůstek zvětšení pro ovládací prvek posuvníku.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFCRibbonSlider::HasZoomButtons

Určuje, zda má posuvník tlačítka lupy.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud má posuvník tlačítka lupy; FALSE jinak.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFCRibbonSlider::OnDraw

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFCRibbonSlider::SetPos

Nastavte aktuální polohu ovládacího prvku posuvníku.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
[v] Určuje polohu, kterou chcete nastavit pro jezdec. Poloha je relativní vzhledem k začátku jezdce.

*bPřekreslit*<br/>
[v] Pokud true, jezdec bude překreslen.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFCRibbonSlider::SetRange

Nastavte rozsah hodnot pro ovládací prvek posuvníku.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
[v] Určuje minimální hodnotu ovládacího prvku posuvníku.

*nMax*<br/>
[v] Určuje maximální hodnotu ovládacího prvku posuvníku.

### <a name="remarks"></a>Poznámky

Určuje rozsah hodnot pro ovládací prvek posuvníku nastavením minimálních a maximálních hodnot.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFCRibbonSlider::SetZoomButtons

Zobrazení nebo skrytí tlačítek lupy.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parametry

[v]. *bSet* TRUE pro zobrazení tlačítek lupy; FALSE skrýt.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFCRibbonSlider::NastavitIninzvýšení

Nastavte přírůstek zvětšení pro ovládací prvek posuvníku.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parametry

*nZoomIncrement*<br/>
[v] Určuje přírůstek zvětšení ovládacího prvku posuvníku.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)
