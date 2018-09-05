---
title: Makra Map objektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1061b105b7fd1e344223da3850275910c164774b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761849"
---
# <a name="object-map-macros"></a>Makra Map objektů

Tato makra definují objekt map a položky.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Můžete zadat objekt třídy textový popis, který zadá do objektu map.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Zadá objekt knihovny ATL do objektu map, aktualizuje registr a vytvoří instanci objektu.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Umožňuje určit, že objekt zaregistrované a inicializován, ale neměl by být externě vytvořitelný prostřednictvím `CoCreateInstance`.|  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION

Můžete zadat popis pro svůj objekt třídy.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parametry

*x*  
[in] Popis objektu třídy.

### <a name="remarks"></a>Poznámky

ATL zadá do mapy objektu prostřednictvím tento popis [OBJECT_ENTRY_AUTO](#object_entry_auto) – makro.

Implementuje DECLARE_OBJECT_DESCRIPTION `GetObjectDescription` funkci, kterou můžete použít k přepsání [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) metody.  

`GetObjectDescription` Funkce je volána `IComponentRegistrar::GetComponents`. `IComponentRegistrar` je rozhraní automatizace, která umožňuje vytvářet a rušit registraci jednotlivých komponent v knihovně DLL. Při vytváření objektu registrátora komponent pomocí Průvodce projektem ATL, průvodce automaticky provede `IComponentRegistrar` rozhraní. `IComponentRegistrar` se obvykle používá Microsoft Transaction Server.

Další informace o Průvodce projektem ATL naleznete v článku [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO

Zadá objekt knihovny ATL do objektu map, aktualizuje registr a vytvoří instanci objektu.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*  
[in] Identifikátor CLSID implementované třídy C++ s názvem třídy modelu COM *třídy*.

*class*  
[in] Název třídy C++ COM třída představovaná typem implementace *clsid*.

### <a name="remarks"></a>Poznámky

Makra položky objektu jsou umístěny v globálním oboru v projektu k poskytování podpory pro registraci, inicializace a vytvoření třídy.

OBJECT_ENTRY_AUTO přejde do ukazatele na Funkce Tvůrce třídy a třídy tvůrce objektu pro vytváření tříd `CreateInstance` funkce pro tento objekt do objektu map automaticky generovaný objekt knihovny ATL. Když [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) je volána, aktualizace systémového registru pro jednotlivé objekty v mapě objektů.  

Následující tabulka popisuje, jak je informace o přidávají do mapy objektu získat z třídy zadané jako druhý parametr na toto makro.

|Informace o|Získané z|
|---------------------|-------------------|
|Registrace modelu COM|[Makra registru](../../atl/reference/registry-macros.md)|
|Vytvoření objektu factory třídy|[Makra objektu pro vytváření tříd](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Vytvoření instance|[Makra agregace](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registrace kategorie funkcí|[Makra kategorií](../../atl/reference/category-macros.md)|
|Úroveň třídy inicializace a vyčištění|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Umožňuje určit, že objekt zaregistrované a inicializován, ale neměl by být externě vytvořitelný prostřednictvím `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*  
[in] Identifikátor CLSID implementované třídy C++ s názvem třídy modelu COM *třídy*.

*class*  
[in] Název třídy C++ COM třída představovaná typem implementace *clsid*.

### <a name="remarks"></a>Poznámky

Makra položky objektu jsou umístěny v globálním oboru v projektu k poskytování podpory pro registraci, inicializace a vytvoření třídy.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO umožňuje určit, že objekt zaregistrované a inicializován (naleznete v tématu [OBJECT_ENTRY_AUTO](#object_entry_auto) Další informace), ale neměly by být vytvořitelný prostřednictvím `CoCreateInstance`.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
