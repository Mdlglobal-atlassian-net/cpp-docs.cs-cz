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
ms.openlocfilehash: e2bb01e6acb9298b08fddc3117ec93dd7c0c2417
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212013"
---
# <a name="cdbpropset-class"></a>CDBPropSet – třída

Dědí ze struktury `DBPROPSET` a přidává konstruktor, který inicializuje klíčová pole a také metodu přístupu `AddProperty`.

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddProperty](#addproperty)|Přidá vlastnost do sady vlastností.|
|[CDBPropSet](#cdbpropset)|Konstruktor|
|[SetGUID](#setguid)|Nastaví pole `guidPropertySet` struktury `DBPROPSET`.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_equal)|Přiřadí obsah jedné vlastnosti nastavené na jinou.|

## <a name="remarks"></a>Poznámky

OLE DB poskytovatelé a spotřebitelé používají `DBPROPSET` struktury k předání polí `DBPROP` struktury. Každá struktura `DBPROP` představuje jednu vlastnost, kterou lze nastavit.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a>CDBPropSet:: AddProperty

Přidá vlastnost do sady vlastností.

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
pro ID vlastnosti, která se má přidat Slouží k inicializaci `dwPropertyID` struktury `DBPROP` přidané do sady vlastností.

*var*<br/>
pro Typ variant použitý k inicializaci hodnoty vlastnosti `DBPROP` struktury přidané do sady vlastností.

*szValue*<br/>
pro Řetězec použitý k inicializaci hodnoty vlastnosti `DBPROP` struktury přidané do sady vlastností.

*bValue*<br/>
pro `BYTE` nebo logická hodnota, která se používá k inicializaci hodnoty vlastnosti pro `DBPROP` strukturu přidanou do sady vlastností.

*nHodnota*<br/>
pro Celočíselná hodnota použitá pro inicializaci hodnoty vlastnosti `DBPROP` struktury přidané do sady vlastností.

*fltValue*<br/>
pro Hodnota s plovoucí desetinnou čárkou, která se používá k inicializaci hodnoty vlastnosti `DBPROP` struktury přidané do sady vlastností.

*dblValue*<br/>
pro Hodnota s plovoucí desetinnou čárkou s dvojitou přesností, která se používá k inicializaci hodnoty vlastnosti `DBPROP` struktury přidané do sady vlastností.

*cyValue*<br/>
pro Hodnota měny CY použitá pro inicializaci hodnoty vlastnosti `DBPROP` struktury přidané do sady vlastností.

### <a name="return-value"></a>Návratová hodnota

**hodnota true** , pokud byla vlastnost úspěšně přidána. V opačném případě **false**.

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a>CDBPropSet:: CDBPropSet

Konstruktor Inicializuje pole `rgProperties`, `cProperties`a `guidPropertySet` struktury [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID použitý k inicializaci pole `guidPropertySet`.

*propset*<br/>
pro Jiný objekt `CDBPropSet` pro konstrukci kopírování.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a>CDBPropSet:: SetGUID

Nastaví pole `guidPropertySet` ve struktuře `DBPROPSET`.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID, který slouží k nastavení `guidPropertySet` pole struktury [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))

### <a name="remarks"></a>Poznámky

Toto pole lze také nastavit pomocí [konstruktoru](../../data/oledb/cdbpropset-cdbpropset.md) .

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a>CDBPropSet:: operator =

Přiřadí obsah jedné vlastnosti nastavené na jinou sadu vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet – třída](../../data/oledb/cdbpropidset-class.md)<br/>
Struktura [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))
[struktury DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))
