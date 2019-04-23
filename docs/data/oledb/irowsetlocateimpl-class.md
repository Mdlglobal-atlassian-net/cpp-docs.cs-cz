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
ms.openlocfilehash: e3513084697a60a33b9fa2ab02222a9b332cce79
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039816"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl – třída

Implementuje rozhraní OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) rozhraní, která načte libovolné řádky ze sady řádků.

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

*T*<br/>
Třída odvozená z `IRowsetLocateImpl`.

*RowsetInterface*<br/>
Třída odvozená z `IRowsetImpl`.

*RowClass*<br/>
Jednotka pro ukládání `HROW`.

*MapClass*<br/>
Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.

*BookmarkKeyType*<br/>
Typ záložky, jako je například DLOUHO nebo řetězec. Běžné záložky musí mít délku minimálně o dva bajty. (Single bajty délka je vyhrazený pro OLE DB [standardní záložky](/previous-versions/windows/desktop/ms712954(v=vs.85))`DBBMK_FIRST`, `DBBMK_LAST`, a `DBBMK_INVALID`.)

*BookmarkType*<br/>
Mechanismu mapování za údržbu relací mezi záložku daty.

*BookmarkMapClass*<br/>
Jednotky úložiště pro všechny popisovačů řádků uchovávat záložkou.

## <a name="requirements"></a>Požadavky

**Hlavička**: atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[Compare](#compare)|Porovná dva záložky.|
|[GetRowsAt](#getrowsat)|Načte řádky od řádku určený posun od záložku.|
|[GetRowsByBookmark](#getrowsbybookmark)|Načte řádky, které odpovídají zadaným záložky.|
|[Hash](#hash)|Vrátí hodnotu hash hodnoty pro zadaný záložky.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Pole záložky.|

## <a name="remarks"></a>Poznámky

`IRowsetLocateImpl` představuje implementaci šablony technologie OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) rozhraní. `IRowsetLocate` slouží k načtení libovolného řádků ze sady řádků. Sada řádků, který neimplementuje toto rozhraní je `sequential` sady řádků. Když `IRowsetLocate` je k dispozici pro sadu řádků sloupců 0 je záložka pro řádky; čtení v tomto sloupci se získat hodnotu záložku, která je možné změnit umístění na stejný řádek.

`IRowsetLocateImpl` slouží k implementaci podpory záložky u zprostředkovatelů. Záložky jsou zástupné symboly (indexy pro sadu řádků), které umožňují příjemce na řádek, rychle vrátit umožňuje vysokorychlostní přístup k datům. Zprostředkovatel určí, co záložky lze jedinečně identifikovat řádek. Pomocí `IRowsetLocateImpl` metody, můžete porovnat záložky, načítání řádků tím, že odsazení, načítání řádků záložkou a návratové hodnoty hash pro záložky.

Pro podporu technologie OLE DB záložky v sadě řádků, ujistěte se, v sadě řádků z této třídy dědit.

Informace o implementaci podpora záložek, naleznete v tématu [podporu zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md) v *průvodce Visual C++ programátor* a [záložky](/previous-versions/windows/desktop/ms709728(v=vs.85)) v *Referenční informace pro OLE DB programátory* v sadu SDK platformy.

## <a name="compare"></a> IRowsetLocateImpl::Compare

Porovná dva záložky.

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

Zobrazit [IRowsetLocate::Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Některé z záložky může být standardní definované technologie OLE DB [standardní záložku](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST`, `DBBMK_LAST`, nebo `DBBMK_INVALID`). Hodnota vrácená v `pComparison` označuje vztah mezi dvěma záložek:

- DBCOMPARE_LT (`cbBookmark1` před `cbBookmark2`.)

- DBCOMPARE_EQ (`cbBookmark1` rovná `cbBookmark2`.)

- DBCOMPARE_GT (`cbBookmark1` po `cbBookmark2`.)

- DBCOMPARE_NE (záložky se stejná hodnota jako a nejsou seřazené.)

- DBCOMPARE_NOTCOMPARABLE (záložky nelze porovnat.)

## <a name="getrowsat"></a> IRowsetLocateImpl::GetRowsAt

Načte řádky od řádku určený posun od záložku.

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

Zobrazit [IRowsetLocate::GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Chcete-li místo toho načtěte z pozice kurzoru, použijte [IRowset::GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` nedojde ke změně pozice kurzoru.

## <a name="getrowsbybookmark"></a> IRowsetLocateImpl::GetRowsByBookmark

Načte jeden nebo více řádků, které odpovídají zadaným záložky.

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
[in] Odpovídá *hChapter* parametr [IRowsetLocate::GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

Další parametry, naleznete v tématu [IRowsetLocate::GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) v *OLE DB referenční informace pro programátory*.

### <a name="remarks"></a>Poznámky

Záložky lze hodnotu definujete nebo OLE DB [standardní záložky](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` nebo `DBBMK_LAST`). nedojde ke změně pozice kurzoru.

## <a name="hash"></a> IRowsetLocateImpl::Hash

Vrátí hodnotu hash hodnoty pro zadaný záložky.

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
[in] Odpovídá *hChapter* parametr [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Další parametry, naleznete v tématu [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) v *OLE DB referenční informace pro programátory*.

## <a name="rgbookmarks"></a> IRowsetLocateImpl::m_rgBookmarks

Pole záložky.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85))
[Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Záložky](/previous-versions/windows/desktop/ms709728(v=vs.85))