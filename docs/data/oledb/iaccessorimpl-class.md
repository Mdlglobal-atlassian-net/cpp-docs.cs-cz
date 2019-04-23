---
title: IAccessorImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
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
ms.openlocfilehash: a4f98cdfea9ea1e82ec0a3de09e292604a6c199f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032112"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl – třída

Poskytuje implementaci [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída objektu sady řádků nebo příkaz.

*BindType*<br/>
Jednotky úložiště pro informace o vazbě. Výchozí hodnota je `ATLBINDINGS` struktury (viz atldb.h).

*BindingVector*<br/>
Jednotky úložiště pro informace o sloupci. Výchozí hodnota je [catlmap –](../../atl/reference/catlmap-class.md) kde HACCESSOR hodnota je klíčovým prvkem a hodnota elementu je ukazatel `BindType` struktury.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|Konstruktor|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Přidá počet odkazů na existující přistupující objekt.|
|[CreateAccessor](#createaccessor)|Vytvoří ze sady vazby přistupující objekt.|
|[Getbindings –](#getbindings)|Vrátí vazby přistupující objekt.|
|[ReleaseAccessor](#releaseaccessor)|Uvolní přistupující objekt.|

## <a name="remarks"></a>Poznámky

Toto je povinná na příkazy a sady řádků. OLE DB vyžaduje poskytovatele, jak implementovat HACCESSOR, což je značka na pole [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) struktury. HACCESSORs poskytované `IAccessorImpl` jsou adresy `BindType` struktury. Ve výchozím nastavení `BindType` je definován jako `ATLBINDINGS` v `IAccessorImpl`vaší definice šablony. `BindType` poskytuje mechanismus používaný `IAccessorImpl` ke sledování počtu prvků v jeho `DBBINDING` pole a také odkaz na počtu a přístupový objekt příznaky.

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor

Přidá počet odkazů na existující přistupující objekt.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor

Vytvoří ze sady vazby přistupující objekt.

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

Zobrazit [IAccessor::CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="getbindings"></a> IAccessorImpl::GetBindings

Vrátí základní sloupce vazby od uživatele v přistupujícím objektu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor

Uvolní přistupující objekt.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IAccessor::ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)