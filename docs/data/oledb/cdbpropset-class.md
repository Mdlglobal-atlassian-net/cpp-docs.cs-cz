---
title: CDBPropSet – třída
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: b58c0262d361ede37bc3db68784177ec4c29f3a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034232"
---
# <a name="cdbpropset-class"></a>CDBPropSet – třída

Dědí z `DBPROPSET` struktury a přidá konstruktor, který inicializuje pole klíče i na `AddProperty` přístup k metodě.

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddProperty](#addproperty)|Přidá vlastnost sady vlastností.|
|[CDBPropSet](#cdbpropset)|Konstruktor|
|[SetGUID](#setguid)|Nastaví `guidPropertySet` pole `DBPROPSET` struktury.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_equal)|Přiřadí obsah jednu vlastnost nastavena na jiný.|

## <a name="remarks"></a>Poznámky

Použití poskytovatelů a příjemců OLE DB `DBPROPSET` struktury předat pole `DBPROP` struktury. Každý `DBPROP` struktura představuje jedinou vlastností, které je možné nastavit.

## <a name="addproperty"></a> CDBPropSet::AddProperty

Přidá vlastnost sady vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>Parametry

*dwPropertyID*<br/>
[in] ID vlastnosti mají být přidány. Použitý k inicializaci `dwPropertyID` z `DBPROP` struktury přidána do sady vlastností.

*var*<br/>
[in] Hodnotu typu variant použitý k inicializaci hodnoty vlastnosti pro `DBPROP` struktury přidána do sady vlastností.

*szValue*<br/>
[in] Řetězec použitý k inicializaci hodnoty vlastnosti pro `DBPROP` struktury přidána do sady vlastností.

*bValue*<br/>
[in] A `BYTE` nebo logická hodnota, které se používají k inicializaci hodnoty vlastnosti pro `DBPROP` struktury přidána do sady vlastností.

*nHodnota*<br/>
[in] Celočíselná hodnota použitý k inicializaci hodnoty vlastnosti pro `DBPROP` struktury přidána do sady vlastností.

*fltValue*<br/>
[in] Použitý k inicializaci hodnoty vlastnosti pro hodnotu s plovoucí desetinnou čárkou `DBPROP` struktury přidána do sady vlastností.

*dblValue*<br/>
[in] Dvojité přesnosti s plovoucí desetinnou čárkou hodnota použitý k inicializaci hodnoty vlastnosti pro `DBPROP` struktury přidána do sady vlastností.

*cyValue*<br/>
[in] Hodnota měny CY použitý k inicializaci hodnoty vlastnosti pro `DBPROP` struktury přidána do sady vlastností.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** vlastnost úspěšně přidal. V opačném případě **false**.

## <a name="cdbpropset"></a> CDBPropSet::CDBPropSet

Konstruktor Inicializuje `rgProperties`, `cProperties`, a `guidPropertySet` pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
[in] Identifikátor GUID použitý k inicializaci `guidPropertySet` pole.

*Sada vlastností*<br/>
[in] Jiné `CDBPropSet` objekt pro konstrukci kopie.

## <a name="setguid"></a> CDBPropSet::SetGUID

Nastaví `guidPropertySet` pole `DBPROPSET` struktury.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
[in] Identifikátor GUID lze nastavit `guidPropertySet` pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury.

### <a name="remarks"></a>Poznámky

Toto pole lze nastavit [konstruktor](../../data/oledb/cdbpropset-cdbpropset.md) také.

## <a name="op_equal"></a> CDBPropSet::operator =

Přiřadí obsah jednu vlastnost nastavena na jinou sadu vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet – třída](../../data/oledb/cdbpropidset-class.md)<br/>
[Struktura DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))
[DBPROP struktura](/previous-versions/windows/desktop/ms717970(v=vs.85))