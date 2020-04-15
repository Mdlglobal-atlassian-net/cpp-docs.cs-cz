---
title: Makra mapování objektů
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326216"
---
# <a name="object-map-macros"></a>Makra mapování objektů

Tato makra definují mapy objektů a položky.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Umožňuje zadat textový popis objektu třídy, který bude zadán do mapy objektů.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Zadá objekt knihovny ATL do mapy objektů, aktualizuje registr a vytvoří instanci objektu.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Umožňuje určit, že objekt by měl být registrován a inicializován, `CoCreateInstance`ale neměl by být externě creatable přes .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Umožňuje zadat textový popis objektu třídy.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Popis objektu třídy.

### <a name="remarks"></a>Poznámky

Knihovna ATL zadá tento popis do mapy objektů prostřednictvím [OBJECT_ENTRY_AUTO](#object_entry_auto) makra.

DECLARE_OBJECT_DESCRIPTION implementuje `GetObjectDescription` funkci, kterou můžete použít k přepsání metody [CComCoClass::GetObjectDescription.](ccomcoclass-class.md#getobjectdescription)

Funkce `GetObjectDescription` je volána společností `IComponentRegistrar::GetComponents`. `IComponentRegistrar`je rozhraní automatizace, které umožňuje registrovat a odregistrovat jednotlivé součásti v knihovně DLL. Když vytvoříte objekt registrátora součástí pomocí Průvodce projektem knihovny ATL, průvodce automaticky implementuje `IComponentRegistrar` rozhraní. `IComponentRegistrar`obvykle používá Microsoft Transaction Server.

Další informace o Průvodci projektem atl naleznete v článku [Vytvoření projektu atl](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Zadá objekt knihovny ATL do mapy objektů, aktualizuje registr a vytvoří instanci objektu.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
[v] CLSID třídy COM implementované třídou C++ s názvem *class*.

*třída*<br/>
[v] Název třídy C++ implementující třídu COM reprezentovanou *clsid*.

### <a name="remarks"></a>Poznámky

Makra položky objektu jsou umístěna v globálním oboru v projektu, aby poskytovala podporu pro registraci, inicializaci a vytvoření třídy.

OBJECT_ENTRY_AUTO zadá ukazatele funkce třídy creator a třídy factory creator třídy `CreateInstance` funkce pro tento objekt do automaticky generované atl objektmapy. Při [volání CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) aktualizuje systémový registr pro každý objekt v mapě objektu.

Následující tabulka popisuje, jak jsou informace přidané do mapy objektů získány z třídy uvedené jako druhý parametr tohoto makra.

|Informace pro|Získané z|
|---------------------|-------------------|
|Registrace com|[Makra registru](../../atl/reference/registry-macros.md)|
|Vytvoření továrny třídy|[Makra factory třídy](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Vytvoření instance|[Agregační makra](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registrace kategorie komponent|[Makra kategorií](../../atl/reference/category-macros.md)|
|Inicializace a vyčištění na úrovni třídy|[ObjektMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Umožňuje určit, že objekt by měl být registrován a inicializován, `CoCreateInstance`ale neměl by být externě creatable přes .

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
[v] CLSID třídy COM implementované třídou C++ s názvem *class*.

*třída*<br/>
[v] Název třídy C++ implementující třídu COM reprezentovanou *clsid*.

### <a name="remarks"></a>Poznámky

Makra položky objektu jsou umístěna v globálním oboru v projektu, aby poskytovala podporu pro registraci, inicializaci a vytvoření třídy.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO umožňuje určit, že objekt by měl být [OBJECT_ENTRY_AUTO](#object_entry_auto) registrován a inicializován (viz OBJECT_ENTRY_AUTO `CoCreateInstance`další informace), ale neměl by být creatable přes .

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
