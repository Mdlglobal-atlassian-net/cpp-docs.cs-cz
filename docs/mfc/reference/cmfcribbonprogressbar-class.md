---
title: Třída CMFCRibbonRibbonBar
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: b7cbddbd4fca8379562b762fadbb3d2bda44f166
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753528"
---
# <a name="cmfcribbonprogressbar-class"></a>Třída CMFCRibbonRibbonBar

Implementuje ovládací prvek, který vizuálně označuje průběh zdlouhavé operace.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Vytvoří a inicializuje `CMFCRibbonProgressBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|Vrátí aktuální průběh.|
|[CMFCRibbonRibbonProgressBar::GetRangeMax](#getrangemax)|Vrátí maximální hodnotu aktuálního rozsahu.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Vrátí minimální hodnotu aktuálního rozsahu.|
|[CMFCRibbonRibbonInterval::GetRegularSize](#getregularsize)|Vrátí běžnou velikost prvku pásu karet. (Přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Určuje, zda indikátor průběhu pracuje v nekonečném režimu.|
|[CMFCRibbonRibbonProgressBar::OnDraw](#ondraw)|Volat rámci k nakreslení prvku pásu karet. (Přepíše [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Nastaví indikátor průběhu tak, aby fungoval v nekonečném režimu.|
|[CMFCRibbonRibbonProgressBar::SetPos](#setpos)|Nastaví aktuální průběh.|
|[CMFCRibbonRibbonProgressBar::SetRange](#setrange)|Nastaví minimální a maximální hodnoty.|

## <a name="remarks"></a>Poznámky

A `CMFCRibbonProgressBar` může pracovat ve dvou režimech: pravidelné a nekonečné. V normálním režimu je indikátor průběhu vyplněn zleva doprava a zastaví se, když dosáhne maximální hodnoty. V nekonečném režimu je indikátor průběhu opakovaně vyplněn z minimální hodnoty na maximální hodnotu. Můžete použít nekonečný režim k označení, že operace probíhá, ale že doba dokončení není známa.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonProgressBar` metody ve třídě. Příklad ukazuje, jak nastavit indikátor průběhu pracovat v nekonečném režimu (kde doba dokončení operace není známa), nastavte minimální a maximální hodnoty pro indikátor průběhu a nastavte aktuální pozici indikátoru průběhu. Tento fragment kódu je součástí [ukázky ukázky ukázky ukázky ms office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonRibbonProgressBar::CMFCRibbonProgressBar

Vytvoří a inicializuje objekt [CMFCRibbonProgressBar.](../../mfc/reference/cmfcribbonprogressbar-class.md)

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Určuje ID příkazu pro indikátor průběhu pásu karet.

*nŠířka*<br/>
[v] Určuje šířku pruhu průběhu pásu karet v obrazových bodech.

*nVýška*<br/>
[v] Určuje výšku pruhu průběhu pásu karet v obrazových bodech.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos

Vrátí aktuální pozici indikátoru průběhu.

```
int GetPos () const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota představující aktuální pozici indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Nastavený rozsah musí být v rozsahu určeném metodou [CMFCRibbonProgressBar::SetRange.](#setrange)

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonRibbonProgressBar::GetRangeMax

Vrátí aktuální maximální hodnotu indikátoru průběhu.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální hodnota aktuálního rozsahu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin

Vrátí aktuální hodnotu minimálního rozsahu indikátoru průběhu.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální hodnota aktuálního rozsahu.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonRibbonInterval::GetRegularSize

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonRibbonProgressBar::IsInfiniteMode

Určuje, zda indikátor průběhu pracuje v nekonečném režimu.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je indikátor průběhu v nekonečném režimu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

V nekonečném režimu indikátor průběhu vyplňuje opakovaně z minimální hodnoty na maximální hodnotu. Můžete použít nekonečný režim k označení, že operace probíhá, ale že doba dokončení není známa.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonRibbonProgressBar::OnDraw

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonRibbonProgressBar::SetInfiniteMode

Nastaví indikátor průběhu tak, aby fungoval v nekonečném režimu.

```cpp
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
[v] TRUE určit, že indikátor průběhu je v nekonečném režimu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Obvykle pokud indikátor průběhu je v nekonečném režimu, je říkat uživateli, že operace probíhá, ale že doba dokončení není známa. Proto indikátor průběhu vyplňuje opakovaně z minimální hodnoty na maximální hodnotu.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonRibbonProgressBar::SetPos

Nastaví aktuální pozici indikátoru průběhu.

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
[v] Určuje polohu, na kterou je nastaven indikátor průběhu.

*bPřekreslit*<br/>
[v] Určuje, zda má být indikátor průběhu překreslen.

### <a name="remarks"></a>Poznámky

Nastavený rozsah musí být v rozsahu určeném metodou [CMFCRibbonProgressBar::SetRange.](#setrange)

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonRibbonProgressBar::SetRange

Nastaví minimální a maximální hodnoty indikátoru průběhu.

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
[v] Určuje minimální hodnotu rozsahu.

*nMax*<br/>
[v] Určuje maximální hodnotu rozsahu.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k definování rozsahu indikátoru průběhu nastavením minimálních a maximálních hodnot.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
