---
title: CSimpleRow – třída
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: 2b08e0e8f3b5b43f79019c70e3fe32ae9064dee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211117"
---
# <a name="csimplerow-class"></a>CSimpleRow – třída

Poskytuje výchozí implementaci pro popisovač řádku, který se používá ve třídě [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRefRow](#addrefrow)|Přidá počet odkazů do existujícího popisovače řádku.|
|[Compare](#compare)|Porovná dva řádky a zjistí, zda odkazují na stejnou instanci řádku.|
|[CSimpleRow](#csimplerow)|Konstruktor|
|[ReleaseRow](#releaserow)|Uvolní řádky.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_dwRef](#dwref)|Počet odkazů na existující popisovač řádku|
|[m_iRowset](#irowset)|Index sady řádků reprezentující kurzor|

## <a name="remarks"></a>Poznámky

Popisovač řádku je logicky jedinečný tag pro řádek výsledku. `IRowsetImpl` vytvoří nový `CSimpleRow` pro každý řádek požadovaný v [IRowsetImpl:: GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` lze také nahradit vlastní implementací popisovače řádku, protože se jedná o výchozí argument šablony pro `IRowsetImpl`. Jediným požadavkem nahrazení této třídy je, aby třída nahrazení poskytovala konstruktor, který přijímá jeden parametr typu **Long**.

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a>CSimpleRow:: AddRefRow

Přidá počet odkazů na existující popisovač řádku způsobem bezpečným pro přístup z více vláken.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a>CSimpleRow:: Compare

Porovná dva řádky a zjistí, zda odkazují na stejnou instanci řádku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parametry

*pRow*<br/>
Ukazatel na objekt `CSimpleRow`.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT, obvykle S_OK, což znamená, že dva řádky jsou stejné jako instance řádku nebo S_FALSE, což značí, že se dva řádky liší. Další možné návratové hodnoty naleznete v tématu [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) v *referenci programátora OLE DB* .

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a>CSimpleRow:: CSimpleRow

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parametry

*iRowsetCur*<br/>
pro Index na aktuální sadu řádků.

### <a name="remarks"></a>Poznámky

Nastaví [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) na *iRowsetCur*.

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a>CSimpleRow:: ReleaseRow

Uvolní řádky způsobem bezpečným pro přístup z více vláken.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a>CSimpleRow:: m_dwRef

Počet odkazů na existující popisovač řádku

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a>CSimpleRow:: m_iRowset

Index sady řádků reprezentující kurzor

### <a name="syntax"></a>Syntaxe

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)
