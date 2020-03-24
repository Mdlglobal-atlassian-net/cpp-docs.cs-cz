---
title: IRowsetLocateImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
ms.openlocfilehash: 06e860425215d9fde268b780c001301b14a1caa1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210428"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl – třída

Implementuje rozhraní OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , které načte libovolné řádky ze sady řádků.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída odvozená od `IRowsetLocateImpl`.

*RowsetInterface*<br/>
Třída odvozená od `IRowsetImpl`.

*RowClass*<br/>
Jednotka úložiště pro `HROW`.

*MapClass*<br/>
Jednotka úložiště pro všechny obsluhy řádků držené zprostředkovatelem.

*BookmarkKeyType*<br/>
Typ záložky, například dlouhý nebo řetězec. Běžné záložky musí mít délku alespoň dvou bajtů. (Délka jednobajtových bajtů je vyhrazená pro OLE DB [Standardní záložky](/previous-versions/windows/desktop/ms712954(v=vs.85))`DBBMK_FIRST`, `DBBMK_LAST`a `DBBMK_INVALID`.)

*BookmarkType*<br/>
Mechanismus mapování pro udržování vztahů mezi daty z Bookmark na data.

*BookmarkMapClass*<br/>
Jednotka úložiště pro všechny obsluhy řádků držené záložkou.

## <a name="requirements"></a>Požadavky

**Záhlaví**: Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[Compare](#compare)|Porovná dvě záložky.|
|[GetRowsAt](#getrowsat)|Načte řádky začínající posunem od záložky od řádku zadaného posunutím.|
|[GetRowsByBookmark](#getrowsbybookmark)|Načte řádky, které odpovídají zadaným záložkám.|
|[Kontrole](#hash)|Vrátí hodnoty hash pro zadané záložky.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Pole záložek.|

## <a name="remarks"></a>Poznámky

`IRowsetLocateImpl` je implementace OLE DB šablon rozhraní [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) . `IRowsetLocate` slouží k načtení libovolných řádků ze sady řádků. Sada řádků, která neimplementuje toto rozhraní, je `sequential` sada řádků. Pokud je v sadě řádků `IRowsetLocate`, sloupec 0 je záložkou pro řádky; Při čtení tohoto sloupce se získá hodnota záložky, kterou lze použít k přemístění na stejný řádek.

`IRowsetLocateImpl` slouží k implementaci podpory záložky ve zprostředkovatelích. Záložky jsou zástupné symboly (indexy pro sadu řádků), které umožňují příjemci rychle se vrátit na řádek a umožnit tak vysokorychlostní přístup k datům. Poskytovatel určuje, které záložky mohou jednoznačně identifikovat řádek. Pomocí metod `IRowsetLocateImpl` můžete porovnat záložky, načíst řádky podle posunu, načíst řádky podle záložky a vracet hodnoty hash pro záložky.

Chcete-li podporovat OLE DB záložky v sadě řádků, nastavte sadu řádků z této třídy jako děděnou.

Informace o implementaci podpory záložky najdete v tématu [Podpora poskytovatelů pro záložky](../../data/oledb/provider-support-for-bookmarks.md) v příručce a [záložkách](/previous-versions/windows/desktop/ms709728(v=vs.85)) *vizuálního C++ programátora* v *referenci OLE DB programátora* v sadě SDK platformy.

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a>IRowsetLocateImpl:: Compare

Porovná dvě záložky.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetLocate:: Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Kteroukoli z těchto záložek může být standardní OLE DB definovaná [standardní záložkou](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST`, `DBBMK_LAST`nebo `DBBMK_INVALID`). Hodnota vrácená v `pComparison` označuje vztah mezi dvěma záložekmi:

- DBCOMPARE_LT (`cbBookmark1` je před `cbBookmark2`.)

- DBCOMPARE_EQ (`cbBookmark1` se rovná `cbBookmark2`.)

- DBCOMPARE_GT (`cbBookmark1` je po `cbBookmark2`.)

- DBCOMPARE_NE (záložky jsou stejné a nejsou seřazené.)

- DBCOMPARE_NOTCOMPARABLE (záložky nelze porovnat.)

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a>IRowsetLocateImpl:: GetRowsAt

Načte řádky začínající posunem od záložky od řádku zadaného posunutím.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetLocate:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Chcete-li místo toho načíst ze pozice kurzoru, použijte [IRowset:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` nemění pozici kurzoru.

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a>IRowsetLocateImpl:: GetRowsByBookmark

Načte jeden nebo více řádků, které odpovídají zadaným záložkám.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
pro Odpovídá parametru *hChapter* na [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

Další parametry naleznete v tématu [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Záložka může být definovaná hodnota nebo OLE DB [Standardní záložky](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` nebo `DBBMK_LAST`). Nemění pozici kurzoru.

## <a name="irowsetlocateimplhash"></a><a name="hash"></a>IRowsetLocateImpl:: hash

Vrátí hodnoty hash pro zadané záložky.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
pro Odpovídá parametru *hChapter* k [IRowsetLocate:: hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Další parametry naleznete v tématu [IRowsetLocate:: hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a>IRowsetLocateImpl:: m_rgBookmarks

Pole záložek.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:](/previous-versions/windows/desktop/ms721190(v=vs.85)) [Podpora poskytovatele
IRowset pro záložky](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Záložky](/previous-versions/windows/desktop/ms709728(v=vs.85))
