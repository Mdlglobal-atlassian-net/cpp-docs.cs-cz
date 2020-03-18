---
title: IAccessorImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: f1865089100ac7f60e8c011e72eedb3d0a3f8470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447071"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl – třída

Poskytuje implementaci rozhraní [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída objektu sady řádků nebo příkazu.

*BindType*<br/>
Jednotka úložiště pro informace o vazbě. Výchozí hodnota je struktura `ATLBINDINGS` (viz Atldb. h).

*BindingVector*<br/>
Jednotka úložiště pro informace o sloupci Výchozí hodnota je [CAtlMap](../../atl/reference/catlmap-class.md) , kde je klíčovým prvkem hodnota HACCESSOR a element value je ukazatel na `BindType` strukturu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|Konstruktor|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Přidá počet odkazů do existujícího přístupového objektu.|
|[CreateAccessor](#createaccessor)|Vytvoří přistupující objekt ze sady vazeb.|
|[Getbindings](#getbindings)|Vrátí vazby v přístupovém objektu.|
|[ReleaseAccessor](#releaseaccessor)|Uvolňuje přistupující objekt.|

## <a name="remarks"></a>Poznámky

Toto je povinné pro sady řádků a příkazy. OLE DB vyžaduje, aby poskytovatelé implementovali HACCESSOR, což je značka pro pole [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) struktur. HACCESSORs, které poskytuje `IAccessorImpl`, jsou adresy `BindType` struktury. Ve výchozím nastavení je `BindType` definován jako `ATLBINDINGS` v definici šablony `IAccessorImpl`. `BindType` poskytuje mechanismus, který `IAccessorImpl` používá ke sledování počtu prvků v jeho poli `DBBINDING` a také počet odkazů a příznaky přistupujícího objektu.

## <a name="iaccessorimpl"></a>IAccessorImpl:: IAccessorImpl

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a>IAccessorImpl:: AddRefAccessor

Přidá počet odkazů do existujícího přístupového objektu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Viz [IAccessor:: AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="createaccessor"></a>IAccessorImpl:: CreateAccessor

Vytvoří přistupující objekt ze sady vazeb.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>Parametry

Viz [IAccessor:: CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="getbindings"></a>IAccessorImpl:: getbindings

Vrátí základní vazby sloupců od příjemce v přístupovém objektu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parametry

Viz [IAccessor:: Getbindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="releaseaccessor"></a>IAccessorImpl:: ReleaseAccessor

Uvolňuje přistupující objekt.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Viz [IAccessor:: ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)