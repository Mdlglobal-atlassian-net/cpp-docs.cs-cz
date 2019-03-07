---
title: IOpenRowsetImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 3d4f778f560b55f22c1c54185bea79af07949ceb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422745"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl – třída

Poskytuje implementaci pro `IOpenRowset` rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Vaše třída odvozena od `IOpenRowsetImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateRowset](#createrowset)|Vytvoří objekt sady řádků. Nebyla volána přímo uživatelem.|
|[OpenRowset](#openrowset)|Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu. (Není v ATLDB. H)|

## <a name="remarks"></a>Poznámky

[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) rozhraní je povinné pro objekt relace. Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu.

## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset

Vytvoří objekt sady řádků. Nebyla volána přímo uživatelem. Zobrazit [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *referenční informace pro OLE DB programátory.*

### <a name="syntax"></a>Syntaxe

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parametry

*RowsetClass*<br/>
Šablona člena třídy představující třídu sady řádků uživatele. Obvykle generované průvodcem knihovnou.

*pRowsetObj*<br/>
[out] Ukazatel na objektu sady řádků. Tento parametr se obvykle nepoužívá, ale lze použít, pokud před předáním objektu COM je nutné provést další práce na dané sadě řádků. Životnost *pRowsetObj* je svázaná s *ppRowset*.

Další parametry, naleznete v tématu [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *OLE DB referenční informace pro programátory.*

## <a name="openrowset"></a> IOpenRowsetImpl::OpenRowset

Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Tato metoda nebyla nalezena v ATLDB. H. Je vytvořen objekt Průvodcem knihovnou ATL při vytváření zprostředkovatele.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)