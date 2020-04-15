---
title: CMFCListCtrl – třída
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 63fbfd236ed98eee3b90f4a20b191817026903c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370775"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl – třída

Třída `CMFCListCtrl` rozšiřuje funkce třídy [CListCtrl](../../mfc/reference/clistctrl-class.md) tím, že podporuje rozšířené funkce řízení záhlaví [třídy CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umožňuje označit seřazený sloupec jinou barvou pozadí.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Povolí více režim řazení.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Vrátí odkaz na podtržený ovládací prvek záhlaví.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Zkontroluje, zda je ovládací prvek seznamu v režimu více řazení.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Volat rámci, když musí porovnat dvě položky ovládacího prvku seznamu.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Volat rámci, když musí určit barvu pozadí jednotlivé buňky.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Volat rámci, když musí získat písmo pro buňku nakreslené.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Volat rámci, když musí určit barvu textu jednotlivé buňky.|
|[CMFCListCtrl::Odstranitsloupec Sort](#removesortcolumn)|Odebere sloupec řazení ze seznamu seřazených sloupců.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Nastaví aktuální seřazený sloupec a pořadí řazení.|
|[CMFCListCtrl::Řazení](#sort)|Seřadí ovládací prvek seznamu.|

## <a name="remarks"></a>Poznámky

`CMFCListCtrl`nabízí dvě vylepšení třídy [CListCtrl.](../../mfc/reference/clistctrl-class.md) Nejprve to znamená, že řazení sloupců je dostupnou možností automatickým kreslením šipky řazení na záhlaví. Za druhé podporuje řazení dat na více sloupcích současně.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCListCtrl` metody ve třídě. Příklad ukazuje, jak vytvořit ovládací prvek seznamu, vložit sloupce, vložit položky, nastavit text položky a nastavit písmo ovládacího prvku seznamu. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlistctrl.h

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Označí seřazené sloupce jinou barvou pozadí.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*bOznačit*<br/>
[v] Logický parametr, který určuje, zda má být povolena jiná barva pozadí.

*bPřekreslit*<br/>
[v] Logický parametr, který určuje, zda má být ovládací prvek okamžitě překreslovat.

### <a name="remarks"></a>Poznámky

`EnableMarkSortedColumn`používá metodu `CDrawingManager::PixelAlpha` k výpočtu barvy, která se má použít pro seřazené sloupce. Vybraná barva je založena na běžné barvě pozadí.

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Umožňuje řazení řádků dat v ovládacím prvku seznamu podle více sloupců.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Logická hodnota, která určuje, zda má být povolen režim řazení více sloupců.

### <a name="remarks"></a>Poznámky

Pokud povolíte řazení na základě více sloupců, sloupce mají hierarchii. Řádky dat budou nejprve seřazeny podle primárního sloupce. Všechny ekvivalentní hodnoty jsou pak seřazeny podle každého následujícího sloupce na základě priority.

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Vrátí odkaz na ovládací prvek záhlaví.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na základní objekt [CMFCHeaderCtrl.](../../mfc/reference/cmfcheaderctrl-class.md)

### <a name="remarks"></a>Poznámky

Ovládací prvek záhlaví pro ovládací prvek seznamu je okno, které obsahuje názvy sloupců. Obvykle je umístěn přímo nad sloupy.

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Zkontroluje, zda ovládací prvek seznamu aktuálně podporuje řazení ve více sloupcích.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud ovládací prvek seznamu podporuje více řazení; FALSE jinak.

### <a name="remarks"></a>Poznámky

Pokud [třída CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) podporuje více řazení, uživatel může seřadit data v ovládacím prvku seznamu podle více sloupců. Chcete-li povolit více řazení, zavolejte [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

Rozhraní Framework volá tuto metodu při porovnávání dvě položky.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

*lParam1*<br/>
[v] První položka porovnat.

*lParam2*<br/>
[v] Druhá položka porovnat.

*iColumn*<br/>
[v] Index sloupce, který tato metoda je řazení.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které označuje relativní pozici dvou položek. Záporná hodnota označuje, že první položka by měla předcházet druhé, kladná hodnota označuje, že první položka by měla následovat druhou a nula znamená, že dvě položky jsou ekvivalentní.

### <a name="remarks"></a>Poznámky

Výchozí implementace vždy vrátí 0. Přepsat tuto funkci poskytnout vlastní algoritmus řazení.

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

Rozhraní Framework volá tuto metodu, když musí určit barvu pozadí jednotlivé buňky.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nŘádek*<br/>
[v] Řádek dotyčné buňky.

*nSloupec*<br/>
[v] Sloupec dotyčné buňky.

### <a name="return-value"></a>Návratová hodnota

Hodnota COLOREF, která určuje barvu pozadí buňky.

### <a name="remarks"></a>Poznámky

Výchozí implementace `OnGetCellBkColor` nepoužívá zadané vstupní parametry a místo `GetBkColor`toho jednoduše volá . Proto ve výchozím nastavení celý seznam ovládací prvek bude mít stejnou barvu pozadí. V odvozené `OnGetCellBkColor` třídě můžete přepsat a označit jednotlivé buňky samostatnou barvou pozadí.

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

Framework volá tuto metodu, když získá písmo pro jednotlivé buňky.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parametry

*nŘádek*<br/>
[v] Řádek dotyčné buňky.

*nSloupec*<br/>
[v] Sloupec dotyčné buňky.

*dwData*<br/>
[v] Uživatelem definovaná data. Výchozí implementace nepoužívá tento parametr.

### <a name="return-value"></a>Návratová hodnota

Úchyt k písmu, který se používá pro aktuální buňku.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vrátí hodnotu NULL. Všechny buňky v ovládacím prvku seznamu mají stejné písmo. Přepsat tuto metodu poskytnout různá písma pro různé buňky.

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

Rámec volá tuto metodu, když musí určit barvu textu jednotlivé buňky.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nŘádek*<br/>
[v] Řádek dotyčné buňky.

*nSloupec*<br/>
[v] Sloupec dotyčné buňky.

### <a name="return-value"></a>Návratová hodnota

Hodnota COLOREF, která určuje barvu textu buňky.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `GetTextColor` tato metoda volá bez ohledu na vstupní parametry. Celý ovládací prvek seznamu bude mít stejnou barvu textu. V odvozené `OnGetCellTextColor` třídě můžete přepsat a označit jednotlivé buňky samostatnou barvou textu.

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCListCtrl::Odstranitsloupec Sort

Odebere sloupec řazení ze seznamu seřazených sloupců.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[v] Sloupec odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda odebere sloupec řazení z ovládacího prvku záhlaví. Volá [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Nastaví aktuální seřazený sloupec a pořadí řazení.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[v] Sloupec, který chcete seřadit.

*bVzestupně*<br/>
[v] Logická hodnota, která určuje pořadí řazení.

*bPřidat*<br/>
[v] Logická hodnota, která určuje, zda metoda přidá sloupec označený *iColumn* do seznamu sloupců řazení.

### <a name="remarks"></a>Poznámky

Tato metoda předá vstupní parametry ovládacímu prvku záhlaví pomocí metody [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

## <a name="cmfclistctrlsort"></a><a name="sort"></a>CMFCListCtrl::Řazení

Seřadí ovládací prvek seznamu.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[v] Sloupec, který chcete seřadit.

*bVzestupně*<br/>
[v] Logická hodnota, která určuje pořadí řazení.

*bPřidat*<br/>
[v] Logická hodnota, která určuje, zda tato metoda přidá sloupec označený *iColumn* do seznamu sloupců řazení.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CListCtrl](../../mfc/reference/clistctrl-class.md)
