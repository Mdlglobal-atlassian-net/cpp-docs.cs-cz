---
title: ISessionPropertiesImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: c1a3539ea4ea705ad8bd1e40acda965ef66e2051
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077716"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl – třída

Poskytuje implementaci rozhraní [ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `ISessionPropertiesImpl`.

*PropClass*<br/>
Uživatelsky definované třídy vlastností, které mají výchozí hodnotu *T*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetProperties](#getproperties)|Vrátí seznam vlastností ve skupině vlastností Session, které jsou aktuálně nastaveny v relaci.|
|[SetProperties](#setproperties)|Nastaví vlastnosti ve skupině vlastností Session.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní v relacích. Tato třída implementuje vlastnosti relace voláním statické funkce definované [mapou sady vlastností](../../data/oledb/begin-propset-map.md). V třídě relace by měla být zadána mapa sady vlastností.

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a>ISessionPropertiesImpl –:: GetProperties

Vrátí seznam vlastností ve skupině vlastností `DBPROPSET_SESSION`, které jsou aktuálně nastaveny v relaci.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Viz [ISessionProperties:: GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a>ISessionPropertiesImpl –:: SetProperties

Nastaví vlastnosti ve skupině vlastností `DBPROPSET_SESSION`.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Viz [ISessionProperties:: SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)