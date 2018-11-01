---
title: Cmfclistctrl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 7d289dc25dfdb07ae581c4669154517882867f2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642261"
---
# <a name="cmfclistctrl-class"></a>Cmfclistctrl – třída

`CMFCListCtrl` Třída rozšiřuje funkce [třídě CListCtrl](../../mfc/reference/clistctrl-class.md) třídy díky podpoře funkcionality kontroly rozšířené hlavičky z [cmfcheaderctrl – třída](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umožňuje označit seřazený sloupec s jinou barvu pozadí.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Umožňuje více režim řazení.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Vrátí odkaz na podtrženou záhlaví ovládacího prvku.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Ověří, zda ovládací prvek seznam v několika režim řazení.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Volá se rozhraním, když ho musí porovnat dvě položky ovládacího prvku seznamu.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Volá se rozhraním, když ho musíte určit barvu pozadí jednotlivé buňky.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Volá se rozhraním, když ho musíte získat písmo pro buňky, které je cílem vykreslování.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Volá se rozhraním, když ho musíte určit barva textu jednotlivé buňky.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Odebere řazení sloupce v seznamu seřazené sloupce.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Nastaví aktuální seřazený sloupec a pořadí řazení.|
|[CMFCListCtrl::Sort](#sort)|Seřadí seznam ovládacího prvku.|

## <a name="remarks"></a>Poznámky

`CMFCListCtrl` nabízí dvě vylepšení [třídě CListCtrl](../../mfc/reference/clistctrl-class.md) třídy. Nejprve označuje řazení sloupců je k dispozici možnost automaticky kreslením šipku řazení v hlavičce. Za druhé podporuje řazení více sloupců ve stejnou dobu data.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCListCtrl` třídy. Tento příklad ukazuje, jak vytvořit ovládací prvek seznamu, Vložit sloupce, vložit položky, nastavit text položky a nastavit písmo ovládacího prvku seznam. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[Cmfclistctrl –](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlistctrl.h

##  <a name="enablemarksortedcolumn"></a>  CMFCListCtrl::EnableMarkSortedColumn

Označí seřazené sloupce s jinou barvu pozadí.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*bMark*<br/>
[in] Parametr logické hodnoty, která určuje, jestli se má povolit jinou barvu pozadí.

*bRedraw*<br/>
[in] Parametr logické hodnoty, který určuje, zda překreslení ovládacího prvku okamžitě.

### <a name="remarks"></a>Poznámky

`EnableMarkSortedColumn` používá metodu `CDrawingManager::PixelAlpha` k výpočtu barvu, která má použít pro seřazené sloupce. Barva výběru je založena na barvu pozadí pravidelně.

##  <a name="enablemultiplesort"></a>  CMFCListCtrl::EnableMultipleSort

Umožňuje řazení podle sloupce řádky dat v ovládacím prvku seznamu.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Logická hodnota určující, zda chcete povolit režim řazení více sloupců.

### <a name="remarks"></a>Poznámky

Když povolíte řazení podle více sloupců, sloupci mít hierarchii. Řádky dat, budou seřazeny nejprve podle primární sloupce. Žádné odpovídající hodnoty jsou potom seřazeno podle jednotlivých následující sloupce na základě priority.

##  <a name="getheaderctrl"></a>  CMFCListCtrl::GetHeaderCtrl

Vrátí odkaz na ovládacím prvku záhlaví.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na základní [cmfcheaderctrl –](../../mfc/reference/cmfcheaderctrl-class.md) objektu.

### <a name="remarks"></a>Poznámky

Ovládací prvek záhlaví pro ovládací prvek seznamu je okno, které obsahuje názvy sloupců. Obvykle je umístěný přímo nad sloupce.

##  <a name="ismultiplesort"></a>  CMFCListCtrl::IsMultipleSort

Kontroluje, zda seznam aktuálně podporuje řazení více sloupců.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ovládací prvek seznamu podporuje řazení více; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Když [cmfclistctrl – třída](../../mfc/reference/cmfclistctrl-class.md) podporuje řazení více, uživatel může řadit dat v ovládacím prvku seznamu více sloupců. Chcete-li povolit více řazení, zavolejte [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>  CMFCListCtrl::OnCompareItems

Rozhraní volá tuto metodu při porovná dvě položky.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

*lParam1*<br/>
[in] První položka určená k porovnání.

*lParam2*<br/>
[in] Druhá položka určená k porovnání.

*iColumn*<br/>
[in] Index sloupce, který tato metoda je řazení.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které označuje relativní polohu dvě položky. Záporná hodnota naznačuje, že první položky by měl předcházet druhý, kladná hodnota označuje, že první položky by měly dodržovat druhé a nula znamená, že jsou ekvivalentní dvě položky.

### <a name="remarks"></a>Poznámky

Výchozí implementace vždy vrátí hodnotu 0. Tato funkce se algoritmus řazení musí přepsat.

##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor

Rozhraní volá tuto metodu, když ho musíte určit barvu pozadí jednotlivé buňky.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
[in] Řádek dotyčný buňky.

*nColumn*<br/>
[in] Sloupec dotyčný buňky.

### <a name="return-value"></a>Návratová hodnota

COLOREF hodnotu, která určuje barvu pozadí buňky.

### <a name="remarks"></a>Poznámky

Výchozí implementace `OnGetCellBkColor` nepoužívá zadaných vstupních parametrů a místo toho jednoduše volá `GetBkColor`. Proto ve výchozím nastavení, bude mít ovládací prvek celý seznam stejnou barvu pozadí. Můžete přepsat `OnGetCellBkColor` v odvozené třídě označit jednotlivé buňky s barvou pozadí samostatné.

##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont

Rozhraní volá tuto metodu, když obdrží písmo pro jednotlivé buňky.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
[in] Řádek dotyčný buňky.

*nColumn*<br/>
[in] Sloupec dotyčný buňky.

*dwData*<br/>
[in] Data definovaná uživatelem. Výchozí implementace nepoužívá tento parametr.

### <a name="return-value"></a>Návratová hodnota

Popisovač písma, která se používá pro aktuální buňku.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vrátí hodnotu NULL. Všechny buňky v ovládacím prvku seznamu mají stejný písma. Potlačí tuto metodu, aby bylo možné poskytnout různá písma pro různé buňky.

##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor

Rozhraní volá tuto metodu, když ho musíte určit barva textu jednotlivé buňky.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
[in] Řádek dotyčný buňky.

*nColumn*<br/>
[in] Sloupec dotyčný buňky.

### <a name="return-value"></a>Návratová hodnota

COLOREF hodnotu, která určuje barvu textu buňky.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, tato metoda volá `GetTextColor` bez ohledu na vstupní parametry. Ovládací prvek celý seznam bude mít stejnou barvu textu. Můžete přepsat `OnGetCellTextColor` v odvozené třídě označit jednotlivé buňky pomocí samostatného textového barvu.

##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn

Odebere řazení sloupce v seznamu seřazené sloupce.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[in] Sloupec, který chcete odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda odebere řazení sloupců z ovládacího prvku záhlaví. Volá [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>  CMFCListCtrl::SetSortColumn

Nastaví aktuální seřazený sloupec a pořadí řazení.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[in] Tento sloupec seřadit.

*bAscending*<br/>
[in] Logická hodnota, která určuje pořadí řazení.

*bAdd*<br/>
[in] Logická hodnota, která určuje, zda metoda přidá sloupec označen *iColumn* do seznamu sloupců seřadit.

### <a name="remarks"></a>Poznámky

Tato metoda předává vstupních parametrů do ovládacího prvku záhlaví pomocí metody [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>  CMFCListCtrl::Sort

Seřadí seznam ovládacího prvku.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[in] Tento sloupec seřadit.

*bAscending*<br/>
[in] Logická hodnota, která určuje pořadí řazení.

*bAdd*<br/>
[in] Logická hodnota, která určuje, zda tato metoda přidá sloupec označen *iColumn* do seznamu sloupců seřadit.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)
