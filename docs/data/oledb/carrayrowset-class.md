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
- CArrayRowset
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
ms.openlocfilehash: 0a867f80f3be685b3c45c8645d6441732acf5851
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330980"
---
# <a name="carrayrowset-class"></a>CArrayRowset – třída

Přístupy prvky sady řádků pomocí syntaxe pole.

## <a name="syntax"></a>Syntaxe

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Typ přístupového objektu třídy, která chcete v sadě řádků používat.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Konstruktor|
|[Snímek](#snapshot)|Celá sada řádků se načte do paměti.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[– operátor&#91;&#93;](#operator)|Přistupuje k elementu sady řádků.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|Počet řádků, které jsou již načten.|

## <a name="carrayrowset"></a> CArrayRowset::CArrayRowset

Vytvoří novou `CArrayRowset` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
[in] Maximální počet řádků v sadě řádků.

## <a name="snapshot"></a> CArrayRowset::Snapshot

Celá sada řádků se načte do paměti, vytváření bitové kopie nebo jeho snímek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Snapshot() throw();
```

## <a name="operator"></a> CArrayRowset::operator

Poskytuje syntaxi jako pole pro přistupování k řádku v sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Parametr bez vizuálního vzhledu, který určuje typ přístupového objektu uložená v dané sadě řádků.

*nRow*<br/>
[in] Číslo řádku (prvek pole), které chcete získat přístup.

### <a name="return-value"></a>Návratová hodnota

Obsah požadovaný řádek.

### <a name="remarks"></a>Poznámky

Pokud *nRow* překračuje počet řádků v sadě řádků, je vyvolána výjimka.

## <a name="nrowsread"></a> CArrayRowset::m_nRowsRead

Obsahuje počet řádků v sadě řádků, které již byly načteny.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset – třída](../../data/oledb/crowset-class.md)