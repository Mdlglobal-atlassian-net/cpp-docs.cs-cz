---
title: CDBPropIDSet – třída
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: 9e878af3acf4c4d3a6ca785454c4bb072f17cf09
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022408"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet – třída

Dědí z `DBPROPIDSET` struktury a přidá konstruktor, který inicializuje pole klíče i na [addpropertyid –](../../data/oledb/cdbpropidset-addpropertyid.md) přístup k metodě.

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Přidá vlastnost ID sady vlastností.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor|
|[SetGUID](#setguid)|Nastaví nastavení GUID ID vlastnosti.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_equal)|Přiřadí obsah jedno ID vlastnosti nastavit na jiný.|

## <a name="remarks"></a>Poznámky

Použití příjemců OLE DB `DBPROPIDSET` struktury předat pole ID vlastnost, pro které chce příjemce se získat informace o vlastnosti. Vlastnosti identifikované v jediném [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) struktura patří do sady jednu vlastnost.

## <a name="addpropertyid"></a> CDBPropIDSet::AddPropertyID

Přidá ID vlastnosti ID sady vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parametry

*propid*<br/>
[in] Nastavte vlastnost ID se má přidat do ID vlastnosti.

## <a name="cdbpropidset"></a> CDBPropIDSet::CDBPropIDSet

Konstruktor Inicializuje `rgProperties`, `cProperties`a (volitelně) `guidPropertySet` pole [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) struktury.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
[in] Identifikátor GUID použitý k inicializaci `guidPropertySet` pole.

*propidset*<br/>
[in] Jiné `CDBPropIDSet` objekt pro konstrukci kopie.

## <a name="setguid"></a> CDBPropIDSet::SetGUID

Nastaví pole identifikátoru GUID v `DBPROPIDSET` struktury.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
[in] Identifikátor GUID lze nastavit `guidPropertySet` pole [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) struktury.

### <a name="remarks"></a>Poznámky

Toto pole lze nastavit [konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) také. Voláním této funkce, pokud použijete výchozí konstruktor pro tuto třídu.

## <a name="op_equal"></a> CDBPropIDSet::operator =

Přiřadí obsah jedno ID vlastnosti nastavena na jinou sadu vlastnost ID.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)