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
ms.openlocfilehash: 1fc60db6db341d0667e24a81ae0f1394f54497ff
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447370"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl – třída

Poskytuje implementaci rozhraní [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IDBInitializeImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|Konstruktor|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[Initialize](#initialize)|Spustí poskytovatele.|
|[Uninitialize](#uninitialize)|Zastaví poskytovatele.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_dwStatus](#dwstatus)|Příznaky zdroje dat.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Ukazatel na implementaci informací o vlastnostech databáze.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory.

## <a name="idbinitializeimpl"></a>IDBInitializeImpl:: IDBInitializeImpl

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Poznámky

Inicializuje všechny datové členy.

## <a name="initialize"></a>IDBInitializeImpl:: Initialize

Inicializuje objekt zdroje dat přípravou jeho podpory vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Poznámky

Viz [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="uninitialize"></a>IDBInitializeImpl:: Uninitialize

Umístí objekt zdroje dat do neinicializovaného stavu uvolněním interních prostředků, jako je například podpora vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Poznámky

Viz [IDBInitialize:: uninitializeed](/previous-versions/windows/desktop/ms719648(v=vs.85)) in *OLE DB Programmer 's Reference*.

## <a name="dwstatus"></a>IDBInitializeImpl:: m_dwStatus

Příznaky zdroje dat.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Poznámky

Tyto příznaky určují nebo označují stav různých atributů pro objekt zdroje dat. Obsahuje jednu nebo více následujících hodnot **výčtu** :

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Maska pro povolení obnovení neinicializovaného stavu.|
|`DSF_PERSIST_DIRTY`|Nastaví, zda objekt zdroje dat vyžaduje trvalost (tj. Pokud došlo ke změnám).|
|`DSF_INITIALIZED`|Nastavit, zda byl zdroj dat inicializován.|

## <a name="pcutlpropinfo"></a>IDBInitializeImpl:: m_pCUtlPropInfo

Ukazatel na objekt implementace pro informace o vlastnostech databáze.

### <a name="syntax"></a>Syntaxe

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)