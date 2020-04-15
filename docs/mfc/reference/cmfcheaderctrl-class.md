---
title: CMFCHeaderCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 0a6b0cf39861ba995acff71fc40cf44ae5114642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367451"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl – třída

Třída `CMFCHeaderCtrl` podporuje řazení více sloupců v ovládacím prvku záhlaví.

## <a name="syntax"></a>Syntaxe

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Vytvoří `CMFCHeaderCtrl` objekt.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Povolí nebo zakáže režim *řazení více sloupců* pro aktuální ovládací prvek záhlaví.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Označuje, zda sloupec není seřazen nebo zda je seřazen vzestupně nebo sestupně.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Načte index s nulovým základem prvního seřazeného sloupce v ovládacím prvku záhlaví.|
|`CMFCHeaderCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCHeaderCtrl::Vzestupně](#isascending)|Označuje, zda je libovolný sloupec v ovládacím prvku záhlaví seřazen vzestupně.|
|[CMFCHeaderCtrl::Ovládací prvek isdialogControl](#isdialogcontrol)|Označuje, zda je nadřazené okno aktuálního ovládacího prvku záhlaví dialogovým oknem.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Označuje, zda je aktuální ovládací prvek záhlaví v režimu *řazení více sloupců.*|
|[CMFCHeaderCtrl::Odstranitsloupec Sort](#removesortcolumn)|Odebere zadaný sloupec ze seznamu sloupců řazení.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Nastaví pořadí řazení zadaného sloupce v ovládacím prvku záhlaví.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Volat rámci nakreslit sloupec záhlaví ovládacího prvku.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Volat rámci k nakreslení šipky řazení.|
|[CMFCHeaderctrl::OnFillBackground](#onfillbackground)|Volat rámci vyplnit pozadí záhlaví řídicí sloupec.|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCHeaderCtrl` třídy a jak povolit *režim řazení více sloupců* pro aktuální ovládací prvek záhlaví.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Poznámky

Třída `CMFCHeaderCtrl` nakreslí šipku řazení na sloupci ovládacího prvku záhlaví, která označuje, že sloupec je seřazen. Režim *řazení více sloupců,* pokud lze současně seřadit sadu sloupců v ovládacím prvku nadřazeného seznamu [(třída CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CmFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl

Vytvoří `CMFCHeaderCtrl` objekt.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Poznámky

Tento konstruktor inicializuje následující členské proměnné na zadané hodnoty:

|Členská proměnná|Hodnota|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort

Povolí nebo zakáže režim *řazení více sloupců* pro aktuální ovládací prvek záhlaví.

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro povolení režimu řazení více sloupců; NEPRAVDA, chcete-li zakázat režim řazení více sloupců a odebrat všechny sloupce ze seznamu seřazených sloupců. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k povolení nebo zakázání režimu řazení více sloupců. Dva nebo více sloupců se může účastnit řazení, pokud je ovládací prvek záhlaví v režimu řazení více sloupců.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState

Označuje, zda je sloupec neseřazen nebo zda je seřazen vzestupně nebo sestupně.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[v] Nula na základě indexu sloupce.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která označuje stav řazení zadaného sloupce. V následující tabulce jsou uvedeny možné hodnoty:

|Hodnota|Popis|
|-----------|-----------------|
|-1|Seřazeno v sestupném pořadí.|
|0|Není seřazeno.|
|1|Seřazeno ve vzestupném pořadí.|

### <a name="remarks"></a>Poznámky

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn

Načte index s nulovým základem prvního seřazeného sloupce v ovládacím prvku záhlaví.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Návratová hodnota

Index seřazeného sloupce nebo -1, pokud není nalezen žádný seřazený sloupec.

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek záhlaví v režimu *řazení více sloupců* a zkompilovali jste aplikaci v režimu ladění, tato metoda uplatní a doporučuje použít metodu [CMFCHeaderCtrl::GetColumnState.](#getcolumnstate) Pokud je ovládací prvek záhlaví v režimu řazení více sloupců a zkompilovali jste aplikaci v maloobchodním režimu, vrátí tato metoda -1.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl::Vzestupně

Označuje, zda je libovolný sloupec v ovládacím prvku záhlaví seřazen vzestupně.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je libovolný sloupec v ovládacím prvku záhlaví seřazen vzestupně; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Hodnota, která vrací tuto metodu se používá k zobrazení příslušné šipky řazení na položku ovládacího prvku záhlaví. Pomocí metody [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) nastavte pořadí řazení.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCHeaderCtrl::Ovládací prvek isdialogControl

Označuje, zda je nadřazené okno aktuálního ovládacího prvku záhlaví dialogovým oknem.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je nadřazené okno aktuálního ovládacího prvku záhlaví dialogovým oknem; jinak NEPRAVDA.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort

Označuje, zda je aktuální ovládací prvek záhlaví v režimu *řazení více sloupců.*

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je povolen režim řazení více sloupců; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pomocí metody [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) povolte nebo zakažte režim řazení více sloupců. Dva nebo více sloupců se může účastnit řazení, pokud je ovládací prvek záhlaví v režimu řazení více sloupců.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem

Volat rámci nakreslit sloupec záhlaví ovládacího prvku.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*iPoložka*<br/>
[v] Nula na základě indexu položky k losování.

*Rect*<br/>
[v] Ohraničující obdélník položky k tomu.

*bIsPressed*<br/>
[v] TRUE pro nakreslení položky v stisknutém stavu; jinak NEPRAVDA.

*bIsZvýrazněno*<br/>
[v] TRUE nakreslit položku ve zvýrazněném stavu; jinak NEPRAVDA.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow

Volat rámci k nakreslení šipky řazení.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectArrow*<br/>
[v] Ohraničovací obdélník šipky řazení.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCHeaderctrl::OnFillBackground

Volat rámci vyplnit pozadí záhlaví řídicí sloupec.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderCtrl::Odstranitsloupec Sort

Odebere zadaný sloupec ze seznamu sloupců řazení.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[v] Index na základě nuly sloupce odebrat.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn

Nastaví pořadí řazení zadaného sloupce v ovládacím prvku záhlaví.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[v] Index ovládacího prvku záhlaví založený na nule. Pokud je tento parametr menší než nula, tato metoda odebere všechny sloupce ze seznamu sloupců řazení.

*bVzestupně*<br/>
[v] Určuje pořadí řazení sloupce, které určuje parametr *iColumn.* TRUE pro nastavení vzestupně; NEPRAVDA pro nastavení sestupného pořadí. Výchozí hodnota je TRUE.

*bPřidat*<br/>
[v] TRUE pro nastavení pořadí řazení sloupce, který určuje parametr *iColumn.*

Pokud je aktuální ovládací prvek záhlaví v režimu *řazení více sloupců,* tato metoda přidá zadaný sloupec do seznamu sloupců řazení. Pomocí [příkazu CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) nastavte režim řazení více sloupců.

Pokud není nastaven režim řazení více sloupců a tato metoda je zkompilována v režimu ladění, tato metoda uplatňuje. Pokud není nastaven režim řazení více sloupců a tato metoda je zkompilována v maloobchodním režimu, tato metoda nejprve odebere všechny sloupce ze seznamu sloupců řazení a přidá zadaný sloupec do seznamu.

Nepravda nejprve odeberete všechny sloupce ze seznamu sloupců řazení a pak přidáte zadaný sloupec do seznamu. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k nastavení pořadí řazení sloupce. V případě potřeby tato metoda přidá sloupec do seznamu sloupců řazení. Ovládací prvek záhlaví používá pořadí řazení k nakreslení šipky řazení, která ukazuje nahoru nebo dolů.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)
