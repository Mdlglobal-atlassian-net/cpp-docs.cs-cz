---
title: IDBInitializeImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 3418ce11e1a607d66fee593b32fd3a4b7d197407
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033979"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl – třída

Poskytuje implementaci pro [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IDBInitializeImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|Konstruktor|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[Initialize](#initialize)|Spustí zprostředkovatele.|
|[Neinicializovaný](#uninitialize)|Zastaví zprostředkovatele.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_dwStatus](#dwstatus)|Zdroje dat příznaky.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Ukazatel na implementaci informace o vlastnostech DB.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory.

## <a name="idbinitializeimpl"></a> IDBInitializeImpl::IDBInitializeImpl

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Poznámky

Inicializuje všechny datové členy.

## <a name="initialize"></a> IDBInitializeImpl::Initialize

Inicializuje objekt zdroje dat připravuje se podpora jeho vlastnosti.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDBInitialize::Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="uninitialize"></a> IDBInitializeImpl::Uninitialize

Místa data objektu v neinicializovaném stavu zdroje uvolněním interním prostředkům, jako je například podpora vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDBInitialize::Uninitialize](/previous-versions/windows/desktop/ms719648(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="dwstatus"></a> IDBInitializeImpl::m_dwStatus

Zdroje dat příznaky.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Poznámky

Tyto příznaky zadat nebo informací o stavu různých atributů pro objekt zdroje dat. Obsahuje jeden nebo více z následujících **výčtu** hodnoty:

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Maska pro povolení obnovení neinicializovaném stavu.|
|`DSF_PERSIST_DIRTY`|Nastavte, pokud objekt zdroje dat vyžaduje trvalost (tj. Pokud byly provedeny změny).|
|`DSF_INITIALIZED`|Nastaví, zda zdroj dat byl inicializován.|

## <a name="pcutlpropinfo"></a> IDBInitializeImpl::m_pCUtlPropInfo

Ukazatel na objekt implementace pro informace o vlastnostech DB.

### <a name="syntax"></a>Syntaxe

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)