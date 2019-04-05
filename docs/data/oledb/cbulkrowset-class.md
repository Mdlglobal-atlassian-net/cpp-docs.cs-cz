---
title: CBulkRowset – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: ba6b41a708cd854e398cbaa80609472ebbe167e8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023227"
---
# <a name="cbulkrowset-class"></a>CBulkRowset – třída

Načítá a zpracovává řádků pro práci s daty hromadně načtením více popisovačů řádků pomocí jediného volání.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Třídu přistupujícího objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Addrefrows –](#addrefrows)|Zvýší počet odkazů.|
|[CBulkRowset](#cbulkrowset)|Konstruktor|
|[MoveFirst](#movefirst)|Načte první řádek dat, provádění nové hromadné načítání, v případě potřeby.|
|[MoveLast](#movelast)|Přejde na poslední řádek.|
|[Metoda MoveNext](#movenext)|Načte další řádek dat.|
|[MovePrev](#moveprev)|Přesune se na předchozí řádek.|
|[MoveToBookmark](#movetobookmark)|Načte řádek označený záložkou nebo řádek na zadaný posun z tuto záložku.|
|[MoveToRatio](#movetoratio)|Načte řádky začínající od desetinné pozice v dané sadě řádků.|
|[ReleaseRows](#releaserows)|Nastaví aktuální řádek (`m_nCurrentRow`) na nulu a verzích všechny řádky.|
|[SetRows](#setrows)|Nastaví počet popisovačů řádků, které se mají načíst jedním voláním.|

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `CBulkRowset` třídy.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="addrefrows"></a> CBulkRowset::AddRefRows

Volání [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) se zvýší počet odkazů pro všechny řádky, které jsou aktuálně získaných v hromadné sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="cbulkrowset"></a> CBulkRowset::CBulkRowset

Vytvoří novou `CBulkRowset` objekt a nastaví výchozí počet řádků na 10.

### <a name="syntax"></a>Syntaxe

```cpp
CBulkRowset();
```

## <a name="movefirst"></a> CBulkRowset::MoveFirst

Načte první řádek dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="movelast"></a> CBulkRowset::MoveLast

Přejde na poslední řádek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="movenext"></a> CBulkRowset::MoveNext

Načte další řádek dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT. Když se dosáhne konce řádků, vrátí DB_S_ENDOFROWSET.

## <a name="moveprev"></a> CBulkRowset::MovePrev

Přesune se na předchozí řádek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="movetobookmark"></a> CBulkRowset::MoveToBookmark

Načte řádek označený záložku nebo řádek na zadaný posun (*lSkip*) z tuto záložku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parametry

*záložky*<br/>
[in] Záložka označení umístění, ze kterého chcete načíst data.

*lSkip*<br/>
[in] Počtu řádků ze záložky pro cílový řádek. Pokud *lSkip* je nula, první řádek načtený je označenou záložkou a doplňujte řádek. Pokud *lSkip* 1, načíst první řádek je řádek po řádku označenou záložkou a doplňujte. Pokud *lSkip* se -1, načíst první řádek je řádek před označenou záložkou a doplňujte řádek.

### <a name="return-value"></a>Návratová hodnota

Zobrazit [IRowset::GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="movetoratio"></a> CBulkRowset::MoveToRatio

Načte řádky začínající od desetinné pozice v dané sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parametry

*nNumerator*<br/>
[in] Čítač použít k určení desetinné umístění, ze kterého se má načíst data.

*nDenominator*<br/>
[in] Jmenovatel používá k určení desetinné umístění, ze kterého se má načíst data.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

`MoveToRatio` načte řádky zhruba podle následující vzorec:

`(nNumerator *  RowsetSize ) / nDenominator`

Kde `RowsetSize` je velikost řádků, měřený v řádcích. Přesnost tohoto vzorce závisí na konkrétního zprostředkovatele. Podrobnosti najdete v tématu [IRowsetScroll::GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) v *OLE DB referenční informace pro programátory*.

## <a name="releaserows"></a> CBulkRowset::ReleaseRows

Volání [IRowset::ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) se sníží počet odkazů pro všechny řádky, které jsou aktuálně získaných v hromadné sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="setrows"></a> CBulkRowset::SetRows

Nastaví počet popisovačů řádků, které jsou načítána pro každé volání.

### <a name="syntax"></a>Syntaxe

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parametry

*nRows*<br/>
[in] Nová velikost řádků (počet řádků).

### <a name="remarks"></a>Poznámky

Při volání této funkce, musí být před otevřením v sadě řádků.

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)