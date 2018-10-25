---
title: Icommandpropertiesimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 40c1648131db04ed1629da453a16112debf6e6be
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053594"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl – třída

Poskytuje implementaci [ICommandProperties](/previous-versions/windows/desktop/ms723044) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaši třídu odvozenou z

*PropClass*<br/>
Vaše vlastnosti třídy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetProperties](#getproperties)|Vrátí seznam vlastností ve skupině vlastností sady řádků, které jsou aktuálně požadovány v sadě řádků.|
|[SetProperties –](#setproperties)|Nastaví vlastnosti ve skupině vlastností sady řádků.|

## <a name="remarks"></a>Poznámky

Toto je povinná na příkazy. Implementace poskytuje statické funkce definované [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) – makro.

## <a name="getproperties"></a> ICommandPropertiesImpl::GetProperties

Vrátí všechny požadované vlastnosti sady pomocí příkazu Vlastnosti mapy.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets, 
   const DBPROPIDSET rgPropertyIDSets[], 
   ULONG * pcPropertySets, 
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Zobrazit [ICommandProperties::GetProperties](/previous-versions/windows/desktop/ms723119) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="setproperties"></a> ICommandPropertiesImpl::SetProperties

Nastaví vlastnosti pro objekt příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets, 
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Zobrazit [ICommandProperties::SetProperties](/previous-versions/windows/desktop/ms711497) v *referenční informace pro OLE DB programátory*.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)