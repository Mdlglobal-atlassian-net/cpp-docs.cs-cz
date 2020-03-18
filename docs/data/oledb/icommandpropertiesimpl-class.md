---
title: ICommandPropertiesImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: 165f7124657cbaf0c0f94171eaf9394011796aea
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447047"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl – třída

Poskytuje implementaci rozhraní [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída, která je odvozena z

*PropClass*<br/>
Vaše třída vlastnosti.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetProperties](#getproperties)|Vrátí seznam vlastností ve skupině vlastností sady řádků, které jsou aktuálně požadovány pro sadu řádků.|
|[SetProperties](#setproperties)|Nastaví vlastnosti ve skupině vlastností sady řádků.|

## <a name="remarks"></a>Poznámky

Toto je povinné pro příkazy. Implementace je poskytnuta statickou funkcí definovanou pomocí makra [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) .

## <a name="getproperties"></a>ICommandPropertiesImpl –:: GetProperties

Vrátí všechny požadované sady vlastností pomocí mapy vlastností příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Viz [ICommandProperties:: GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="setproperties"></a>ICommandPropertiesImpl –:: SetProperties

Nastaví vlastnosti pro objekt Command.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Viz [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)