---
title: IOpenRowsetImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 66fce9d2ffe63798738be1658a5328e907395a54
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446326"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl – třída

Poskytuje implementaci pro rozhraní `IOpenRowset`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Vaše třída odvozená od `IOpenRowsetImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateRowset](#createrowset)|Vytvoří objekt sady řádků. Nevoláno přímo uživatelem.|
|[OpenRowset](#openrowset)|Otevře a vrátí sadu řádků, která obsahuje všechny řádky z jedné základní tabulky nebo indexu. (Ne v ATLDB. Y|

## <a name="remarks"></a>Poznámky

Rozhraní [IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) je pro objekt Session povinné. Otevře a vrátí sadu řádků, která obsahuje všechny řádky z jedné základní tabulky nebo indexu.

## <a name="createrowset"></a>IOpenRowsetImpl –:: CreateRowset

Vytvoří objekt sady řádků. Nevoláno přímo uživatelem. Viz [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *referenci programátora OLE DB.*

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
Člen třídy šablony představující třídu sady řádků uživatele. Obvykle generuje průvodcem.

*pRowsetObj*<br/>
mimo Ukazatel na objekt sady řádků. Tento parametr se obvykle nepoužívá, ale je možné jej použít, je-li nutné provést více práce na sadě řádků předtím, než je předáte objektu COM. Životnost *pRowsetObj* je vázána *ppRowset*.

Další parametry naleznete v tématu [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *referenci programátora OLE DB.*

## <a name="openrowset"></a>IOpenRowsetImpl –:: OpenRowset

Otevře a vrátí sadu řádků, která obsahuje všechny řádky z jedné základní tabulky nebo indexu.

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

Viz [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Tato metoda není v ATLDB nalezena. Y. Vytvoří se Průvodce objektem ATL při vytváření poskytovatele.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)