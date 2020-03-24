---
title: CArrayRowset – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: 0c5159ac5b834c7c31d980a412f28f8129e15b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212261"
---
# <a name="carrayrowset-class"></a>CArrayRowset – třída

Přistupuje k prvkům sady řádků pomocí syntaxe pole.

## <a name="syntax"></a>Syntaxe

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Typ přístupové třídy, kterou chcete použít pro sadu řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Konstruktor|
|[Snímek](#snapshot)|Přečte celou sadu řádků do paměti.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Podnikatel&#91;&#93;](#operator)|Přistupuje k elementu sady řádků.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|Počet již přečtených řádků.|

## <a name="carrayrowsetcarrayrowset"></a><a name="carrayrowset"></a>CArrayRowset:: CArrayRowset

Vytvoří nový objekt `CArrayRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
pro Maximální počet řádků v sadě řádků.

## <a name="carrayrowsetsnapshot"></a><a name="snapshot"></a>CArrayRowset:: Snapshot

Přečte celou sadu řádků do paměti a vytvoří pro ni obrázek nebo snímek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Snapshot() throw();
```

## <a name="carrayrowsetoperator"></a><a name="operator"></a>CArrayRowset:: operator

Poskytuje syntaxi typu pole pro přístup k řádku v sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Parametr s šablonou, který určuje typ přístupového objektu uloženého v sadě řádků.

*nRow*<br/>
pro Číslo řádku (prvku pole), ke kterému chcete získat přístup.

### <a name="return-value"></a>Návratová hodnota

Obsah požadovaného řádku

### <a name="remarks"></a>Poznámky

Pokud *nRow* překračuje počet řádků v sadě řádků, je vyvolána výjimka.

## <a name="carrayrowsetm_nrowsread"></a><a name="nrowsread"></a>CArrayRowset:: m_nRowsRead

Obsahuje počet řádků v sadě řádků, které již byly přečteny.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset – třída](../../data/oledb/crowset-class.md)
