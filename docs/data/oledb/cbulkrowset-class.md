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
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
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
ms.openlocfilehash: e66a183c7bbafa16b3aefea8da1472255b507468
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212120"
---
# <a name="cbulkrowset-class"></a>CBulkRowset – třída

Načítá a zpracovává řádky pro hromadnou práci s daty, a to načítáním více popisovačů řádků s jedním voláním.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Přístupová třída.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRefRows](#addrefrows)|Zvýší počet odkazů.|
|[CBulkRowset](#cbulkrowset)|Konstruktor|
|[MoveFirst](#movefirst)|Načte první řádek dat a v případě potřeby provede nové hromadné načtení.|
|[MoveLast](#movelast)|Přesune se na poslední řádek.|
|[Metoda](#movenext)|Načte další řádek dat.|
|[MovePrev](#moveprev)|Přesune se na předchozí řádek.|
|[MoveToBookmark](#movetobookmark)|Načte řádek označený záložkou nebo řádkem na zadaném posunu z této záložky.|
|[MoveToRatio](#movetoratio)|Načte řádky začínající ze zlomkové pozice v sadě řádků.|
|[ReleaseRows](#releaserows)|Nastaví aktuální řádek (`m_nCurrentRow`) na hodnotu nula a uvolní všechny řádky.|
|[SetRows](#setrows)|Nastaví počet obslužných rutin řádků, které mají být načteny jedním voláním.|

## <a name="example"></a>Příklad

Následující příklad ukazuje použití třídy `CBulkRowset`.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a>CBulkRowset:: AddRefRows

Volá [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) pro zvýšení počtu odkazů pro všechny řádky, které jsou aktuálně načteny ze sady řádků Bulk.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a>CBulkRowset:: CBulkRowset

Vytvoří nový objekt `CBulkRowset` a nastaví výchozí počet řádků na 10.

### <a name="syntax"></a>Syntaxe

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a>CBulkRowset:: MoveFirst

Načte první řádek dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a>CBulkRowset:: MoveLast

Přesune se na poslední řádek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a>CBulkRowset:: MoveNext

Načte další řádek dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Po dosažení konce sady řádků vrátí DB_S_ENDOFROWSET.

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a>CBulkRowset:: MovePrev

Přesune se na předchozí řádek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a>CBulkRowset:: MoveToBookmark

Načte řádek označený záložkou nebo řádku v zadaném posunu (*lSkip*) z této záložky.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parametry

*záložku*<br/>
pro Záložka označující umístění, ze kterého chcete načíst data.

*lSkip*<br/>
pro Počet řádků z záložky na cílový řádek. Pokud je *lSkip* nula, první načtený řádek je řádek s záložkou. Pokud je *lSkip* 1, první načtený řádek je řádek za řádkem s záložkou. Pokud je *lSkip* -1, první načtený řádek je řádek před řádkem s záložkou.

### <a name="return-value"></a>Návratová hodnota

Viz [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a>CBulkRowset:: MoveToRatio

Načte řádky začínající ze zlomkové pozice v sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parametry

*nNumerator*<br/>
pro Čitatel použitý k určení zlomkové pozice, ze které se mají načíst data

*nDenominator*<br/>
pro Jmenovatel použitý k určení zlomkové pozice, ze které se mají načíst data

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`MoveToRatio` načte řádky přibližně podle následujícího vzorce:

`(nNumerator *  RowsetSize ) / nDenominator`

Kde `RowsetSize` je velikost sady řádků měřenou v řádcích. Přesnost tohoto vzorce závisí na konkrétním zprostředkovateli. Podrobnosti najdete v tématu [IRowsetScroll:: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a>CBulkRowset:: ReleaseRows

Volá [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) pro snížení počtu odkazů pro všechny řádky, které jsou aktuálně načteny ze sady řádků Bulk.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a>CBulkRowset:: SetRows

Nastaví počet obslužných rutin, které jednotlivé hovory načítají.

### <a name="syntax"></a>Syntaxe

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parametry

*Hodnota nRows*<br/>
pro Nová velikost sady řádků (počet řádků).

### <a name="remarks"></a>Poznámky

Pokud zavoláte tuto funkci, musí být před otevřením sady řádků.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
