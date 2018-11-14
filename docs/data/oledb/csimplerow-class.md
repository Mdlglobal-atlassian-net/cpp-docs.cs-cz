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
- CSimpleRow
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
ms.openlocfilehash: dba86b310dcd9b89026d95732f9ca542e6995146
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556631"
---
# <a name="csimplerow-class"></a>CSimpleRow – třída

Poskytuje výchozí implementaci pro popisovač řádku, který je používán [IRowsetImpl –](../../data/oledb/irowsetimpl-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Addrefrow –](#addrefrow)|Přidá počet odkazů na existující popisovač řádku.|
|[Compare](#compare)|Porovná dva řádky, které chcete zobrazit, pokud se odkazují na stejnou instanci řádek.|
|[CSimpleRow](#csimplerow)|Konstruktor|
|[Releaserow –](#releaserow)|Verze řádků.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_dwRef](#dwref)|Počet odkazů na existující popisovač řádku.|
|[m_iRowset](#irowset)|Index tak, aby v sadě řádků reprezentující kurzor.|

## <a name="remarks"></a>Poznámky

Popisovač řádku jsou logicky jedinečný klíčová slova pro řádek výsledek. `IRowsetImpl` Vytvoří novou `CSimpleRow` pro každý řádek požaduje v [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` také se dá nahradit výrazem vlastní implementaci popisovač řádku, jako je výchozí argument šablony pro `IRowsetImpl`. Jediným požadavkem na nahrazení Tato třída má mít náhradní třída konstruktor, který přijímá jeden parametr typu zadat **dlouhé**.

## <a name="addrefrow"></a> CSimpleRow::AddRefRow

Přidá počet odkazů na existující popisovač řádku způsobem bezpečným pro vlákno.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a> CSimpleRow::Compare

Porovná dva řádky, které chcete zobrazit, pokud se odkazují na stejnou instanci řádek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parametry

*pRow*<br/>
Ukazatel `CSimpleRow` objektu.

### <a name="return-value"></a>Návratová hodnota

Hodnotu HRESULT, obvykle S_OK označující dvěma řádky se stejnou instanci řádek nebo S_FALSE označující dvěma řádky se liší. Zobrazit [IRowsetIdentity::IsSameRow](https://docs.microsoft.com/previous-versions/windows/desktop/ms719629(v=vs.85)) v *OLE DB referenční informace pro programátory* pro ostatní možných vrácených hodnot.

## <a name="csimplerow"></a> CSimpleRow::CSimpleRow

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parametry

*iRowsetCur*<br/>
[in] Index aktuální sady řádků.

### <a name="remarks"></a>Poznámky

Nastaví [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) k *iRowsetCur*.

## <a name="releaserow"></a> CSimpleRow::ReleaseRow

Verze řádků způsobem bezpečným pro vlákno.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a> CSimpleRow::m_dwRef

Počet odkazů na existující popisovač řádku.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a> CSimpleRow::m_iRowset

Index řádků reprezentující kurzor.

### <a name="syntax"></a>Syntaxe

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)