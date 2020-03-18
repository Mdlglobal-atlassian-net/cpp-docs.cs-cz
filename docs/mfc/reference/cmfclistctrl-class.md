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
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420314"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl – třída

Třída `CMFCListCtrl` rozšiřuje funkčnost třídy [třídy CListCtrl](../../mfc/reference/clistctrl-class.md) podporou rozšířených funkcí ovládacího prvku záhlaví [třídy CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Povoluje možnost označit seřazený sloupec jinou barvou pozadí.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Povoluje vícenásobný režim řazení.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Vrátí odkaz na podtržené ovládací prvky záhlaví.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Kontroluje, zda je ovládací prvek seznamu v režimu více řazení.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Volá se rozhraním, když musí porovnat dvě položky ovládacího prvku seznamu.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Volá se rozhraním, když se musí určit barva pozadí jednotlivé buňky.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Volá se rozhraním, když musí získat písmo pro vykreslenou buňku.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Volá se rozhraním, když se musí určit barva textu pro jednotlivou buňku.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Odebere sloupec řazení ze seznamu seřazených sloupců.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Nastaví aktuální seřazený sloupec a pořadí řazení.|
|[CMFCListCtrl:: Sort](#sort)|Seřadí ovládací prvek seznam.|

## <a name="remarks"></a>Poznámky

`CMFCListCtrl` nabízí dvě vylepšení třídy [třídy CListCtrl](../../mfc/reference/clistctrl-class.md) . Nejprve indikuje, že řazení sloupce je k dispozici možnost automatického kreslení šipky řazení v hlavičce. Za druhé podporuje řazení dat na více sloupcích současně.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCListCtrl` třídy. Tento příklad ukazuje, jak vytvořit ovládací prvek seznamu, Vložit sloupce, vložit položky, nastavit text položky a nastavit písmo ovládacího prvku seznam. Tento fragment kódu je součástí [ukázkového vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlistctrl. h

##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Označí seřazené sloupce jinou barvou pozadí.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*bMark*<br/>
pro Logický parametr, který určuje, zda má být povolena jiná barva pozadí.

*bRedraw*<br/>
pro Logický parametr, který určuje, zda má být ovládací prvek okamžitě vykreslován.

### <a name="remarks"></a>Poznámky

`EnableMarkSortedColumn` používá `CDrawingManager::PixelAlpha` metody k výpočtu barvy, která se má použít pro seřazené sloupce. Vyzvednutá barva je založená na běžné barvě pozadí.

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Povoluje řazení řádků dat v ovládacím prvku seznam více sloupci.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Logická hodnota, která určuje, zda má být povolen více režimů řazení sloupců.

### <a name="remarks"></a>Poznámky

Pokud povolíte řazení založené na více sloupcích, mají sloupce hierarchii. Řádky dat budou nejprve seřazeny podle primárního sloupce. Jakékoli ekvivalentní hodnoty jsou následně seřazeny podle každého následujícího sloupce podle priority.

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Vrátí odkaz na ovládací prvek záhlaví.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na podkladový objekt [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) .

### <a name="remarks"></a>Poznámky

Ovládací prvek záhlaví pro ovládací prvek seznam je okno, které obsahuje názvy sloupců. Obvykle je umístěn přímo nad sloupci.

##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Kontroluje, zda ovládací prvek seznam aktuálně podporuje řazení více sloupců.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud ovládací prvek seznam podporuje vícenásobné řazení; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud [Třída CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) podporuje vícenásobné řazení, může uživatel data seřadit v ovládacím prvku seznam podle více sloupců. Chcete-li povolit vícenásobné řazení, zavolejte [CMFCListCtrl:: EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

Rozhraní volá tuto metodu, když porovná dvě položky.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

*lParam1*<br/>
pro První položka, která se má porovnat

*lParam2*<br/>
pro Druhá položka, která se má porovnat.

*iColumn*<br/>
pro Index sloupce, který je touto metodou řazení.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které označuje relativní pozici dvou položek. Záporná hodnota znamená, že první položka by měla předcházet druhé, kladná hodnota označuje, že první položka by měla následovat za sekundu a nula znamená, že dvě položky jsou ekvivalentní.

### <a name="remarks"></a>Poznámky

Výchozí implementace vždy vrátí hodnotu 0. Tuto funkci můžete přepsat tak, aby poskytovala vlastní algoritmus řazení.

##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

Rozhraní volá tuto metodu, když musí určit barvu pozadí jednotlivé buňky.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
pro Řádek dané buňky

*nColumn*<br/>
pro Sloupec daného buňky

### <a name="return-value"></a>Návratová hodnota

Hodnota COLOREF, která určuje barvu pozadí buňky.

### <a name="remarks"></a>Poznámky

Výchozí implementace `OnGetCellBkColor` nepoužívá zadané vstupní parametry a místo toho jednoduše volá `GetBkColor`. Proto ve výchozím nastavení bude mít celý ovládací prvek seznam stejnou barvu pozadí. Můžete přepsat `OnGetCellBkColor` v odvozené třídě a označit jednotlivé buňky samostatnou barvou pozadí.

##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

Rozhraní volá tuto metodu, když získá písmo pro jednotlivou buňku.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
pro Řádek dané buňky

*nColumn*<br/>
pro Sloupec daného buňky

*dwData*<br/>
pro Data definovaná uživatelem. Výchozí implementace nepoužívá tento parametr.

### <a name="return-value"></a>Návratová hodnota

Popisovač písma, který se používá pro aktuální buňku.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vrací hodnotu NULL. Všechny buňky v ovládacím prvku seznam mají stejné písmo. Tuto metodu přepište, pokud chcete pro různé buňky zadat různá písma.

##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

Rozhraní volá tuto metodu, když musí určit barvu textu jednotlivé buňky.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
pro Řádek dané buňky

*nColumn*<br/>
pro Sloupec daného buňky

### <a name="return-value"></a>Návratová hodnota

Hodnota COLOREF, která určuje barvu textu buňky.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda volá `GetTextColor` bez ohledu na vstupní parametry. Celý ovládací prvek seznamu bude mít stejnou barvu textu. Můžete přepsat `OnGetCellTextColor` v odvozené třídě a označit jednotlivé buňky samostatnou barvou textu.

##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Odebere sloupec řazení ze seznamu seřazených sloupců.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
pro Sloupec, který se má odebrat

### <a name="remarks"></a>Poznámky

Tato metoda odebere sloupec řazení z ovládacího prvku záhlaví. Volá [CMFCHeaderCtrl:: RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Nastaví aktuální seřazený sloupec a pořadí řazení.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
pro Sloupec, který se má seřadit

*bAscending*<br/>
pro Logická hodnota, která určuje pořadí řazení.

*bAdd*<br/>
pro Logická hodnota určující, zda metoda přidá sloupec uvedený v *iColumn* do seznamu sloupců řazení.

### <a name="remarks"></a>Poznámky

Tato metoda předá vstupní parametry ovládacímu prvku Header pomocí metody [CMFCHeaderCtrl:: SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>CMFCListCtrl:: Sort

Seřadí ovládací prvek seznam.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
pro Sloupec, který se má seřadit

*bAscending*<br/>
pro Logická hodnota, která určuje pořadí řazení.

*bAdd*<br/>
pro Logická hodnota, která určuje, zda tato metoda přidá sloupec uvedený v *iColumn* do seznamu sloupců řazení.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)
