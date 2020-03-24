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
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
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
ms.openlocfilehash: a52d7443ab335e8546a4bcce03cf68c3b1d60e3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212011"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet – třída

Dědí ze struktury `DBPROPIDSET` a přidává konstruktor, který inicializuje klíčová pole a také metodu přístupu [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Přidá vlastnost do sady ID vlastnosti.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor|
|[SetGUID](#setguid)|Nastaví identifikátor GUID nastaveného ID vlastnosti.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_equal)|Přiřadí obsah jednoho ID vlastnosti nastaven na jiný.|

## <a name="remarks"></a>Poznámky

OLE DB spotřebitelé používají `DBPROPIDSET` struktury k předání pole ID vlastností, pro které chce příjemce získat informace o vlastnostech. Vlastnosti identifikované v jedné struktuře [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) patří do jedné sady vlastností.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a>CDBPropIDSet:: AddPropertyID

Přidá ID vlastnosti do nastaveného ID vlastnosti.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parametry

*propid*<br/>
pro ID vlastnosti, která se má přidat do nastaveného ID vlastnosti

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a>CDBPropIDSet:: CDBPropIDSet

Konstruktor Inicializuje pole `rgProperties`, `cProperties`a (volitelně) `guidPropertySet` struktuře struktury [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID použitý k inicializaci pole `guidPropertySet`.

*propidset*<br/>
pro Jiný objekt `CDBPropIDSet` pro konstrukci kopírování.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a>CDBPropIDSet:: SetGUID

Nastaví pole GUID ve struktuře `DBPROPIDSET`.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID, který slouží k nastavení `guidPropertySet` pole struktury [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85))

### <a name="remarks"></a>Poznámky

Toto pole lze také nastavit pomocí [konstruktoru](../../data/oledb/cdbpropidset-cdbpropidset.md) . Tuto funkci volejte, pokud použijete výchozí konstruktor pro tuto třídu.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a>CDBPropIDSet:: operator =

Přiřadí obsah jednoho ID vlastnosti nastaven na jinou nastavenou vlastnost ID.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
