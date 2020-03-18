---
title: Makra map objektů
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 73dc924527bac8499adefab3d0d6b51afa500a5a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417577"
---
# <a name="object-map-macros"></a>Makra map objektů

Tato makra definují mapování objektů a položky.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Umožňuje zadat textový popis objektu třídy, který bude zadán do mapy objektů.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Vloží objekt ATL do mapy objektů, aktualizuje registr a vytvoří instanci objektu.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Umožňuje určit, že by měl být objekt zaregistrován a inicializován, ale nesmí být externě vypsaný prostřednictvím `CoCreateInstance`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Umožňuje zadat textový popis objektu třídy.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Popis objektu třídy.

### <a name="remarks"></a>Poznámky

ATL vloží tento popis do mapy objektů pomocí makra [OBJECT_ENTRY_AUTO](#object_entry_auto) .

DECLARE_OBJECT_DESCRIPTION implementuje funkci `GetObjectDescription`, kterou lze použít k přepsání metody [CComCoClass:: GetObjectDescription](ccomcoclass-class.md#getobjectdescription) .

Funkce `GetObjectDescription` je volána `IComponentRegistrar::GetComponents`. `IComponentRegistrar` je automatizační rozhraní, které umožňuje registrovat a odregistrovat jednotlivé komponenty v knihovně DLL. Když vytvoříte objekt registrátora komponent pomocí Průvodce projektem ATL, průvodce automaticky implementuje rozhraní `IComponentRegistrar`. `IComponentRegistrar` obvykle používá Microsoft Transaction Server.

Další informace o Průvodci projektem ATL naleznete v článku [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Vloží objekt ATL do mapy objektů, aktualizuje registr a vytvoří instanci objektu.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
pro Identifikátor CLSID třídy COM implementované C++ třídou s názvem *Class*.

*class*<br/>
pro Název C++ třídy implementující třídu modelu COM reprezentovanou *identifikátorem CLSID*.

### <a name="remarks"></a>Poznámky

Makra položky objektu jsou umístěna v globálním oboru v projektu za účelem poskytnutí podpory pro registraci, inicializaci a vytváření třídy.

OBJECT_ENTRY_AUTO vstoupí ukazatelé na funkce třídy Creator a třídy Creator třídy Creator `CreateInstance` funkce pro tento objekt na automaticky generované mapování objektů ATL. Při volání metody [CAtlComModule:: RegisterServer](catlcommodule-class.md#registerserver) aktualizuje systémový registr pro každý objekt v mapě objektů.

Následující tabulka popisuje, jak se informace přidané do mapy objektů získávají z třídy zadané jako druhý parametr pro toto makro.

|Informace pro|Získáno z|
|---------------------|-------------------|
|Registrace COM|[Makra registru](../../atl/reference/registry-macros.md)|
|Vytvoření objektu pro vytváření tříd|[Makra továrny tříd](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Vytvoření instance|[Makra agregace](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registrace kategorie součásti|[Makra kategorií](../../atl/reference/category-macros.md)|
|Inicializace a vyčištění na úrovni třídy|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Umožňuje určit, že by měl být objekt zaregistrován a inicializován, ale nesmí být externě vypsaný prostřednictvím `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
pro Identifikátor CLSID třídy COM implementované C++ třídou s názvem *Class*.

*class*<br/>
pro Název C++ třídy implementující třídu modelu COM reprezentovanou *identifikátorem CLSID*.

### <a name="remarks"></a>Poznámky

Makra položky objektu jsou umístěna v globálním oboru v projektu za účelem poskytnutí podpory pro registraci, inicializaci a vytváření třídy.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO umožňuje určit, že se má objekt registrovat a inicializovat (Další informace najdete v [OBJECT_ENTRY_AUTO](#object_entry_auto) ), ale nemělo by být možné ho vytvořit prostřednictvím `CoCreateInstance`.

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)
