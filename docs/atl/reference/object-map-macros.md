---
title: Makra Map objektu | Microsoft Docs
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
ms.openlocfilehash: 671fd80bc2c4ad320efb282fd659899756c2ecbc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362940"
---
# <a name="object-map-macros"></a>Makra Map objektu
Tyto makra definovat objekt mapy a položky.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Umožňuje zadat textový popis objektu třídy, který bude zadán do mapování objektu.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Zadá objekt knihovny ATL do mapování objektu, aktualizuje registr a vytvoří instanci objektu.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Umožňuje zadat, že objekt zaregistrované a inicializován, ale nesmí být externě vytvořitelné prostřednictvím `CoCreateInstance`.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
   
##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION  
 Umožňuje zadat textový popis pro třídu objektu.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Popis objektu třídy.  
  
### <a name="remarks"></a>Poznámky  
 ATL zadá do mapování objektu prostřednictvím tento popis [OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) makro.  
  
 `DECLARE_OBJECT_DESCRIPTION` implementuje `GetObjectDescription` funkce, které můžete použít k přepsání [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) metoda.  

  
 `GetObjectDescription` Funkce volá **IComponentRegistrar::GetComponents**. **IComponentRegistrar** je automatizace rozhraní, které vám umožní zaregistrovat a zrušit registraci jednotlivých součástí v nástroji knihovny DLL. Když vytvoříte objekt součást registrátora s Průvodce projektem ATL, průvodce bude automaticky provádět **IComponentRegistrar** rozhraní. **IComponentRegistrar** se obvykle používá server Microsoft transakce.  
  
 Další informace o Průvodci projektu knihovny ATL, najdete v článku [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO  
 Zadá objekt knihovny ATL do mapování objektu, aktualizuje registr a vytvoří instanci objektu.  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] CLSID implementované C++ třída s názvem třídy COM `class`.  
  
 `class`  
 [v] Název třídy C++ implementace třídy COM reprezentována `clsid`.  
  
### <a name="remarks"></a>Poznámky  
 Makra položky objektu jsou umístěny v globálním oboru v projektu kvůli zajištění podpory pro registraci, inicializace a vytvoření třídy.  
  
 `OBJECT_ENTRY_AUTO` zadá ukazatele funkce creator třídy a třídy creator zdroj tříd `CreateInstance` funkce pro tento objekt do mapování automaticky generovaný ATL objektu. Když [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) je volána, aktualizace systémového registru pro každý objekt v mapování objektu.  

  
 Následující tabulka popisuje, jak informace o přidaných do mapování objektu se získávají z třídy zadané jako druhý parametr toto makro.  
  
|Informace o|Získané z|  
|---------------------|-------------------|  
|Registrace modelu COM|[Makra registru](../../atl/reference/registry-macros.md)|  
|Vytvoření objektu pro vytváření tříd|[Makra pro vytváření – třída](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Vytvoření instance|[Makra agregace](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Součást kategorie registrace|[Makra kategorií](../../atl/reference/category-macros.md)|  
|Inicializace úrovni třídy a čištění|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 Umožňuje zadat, že objekt zaregistrované a inicializován, ale nesmí být externě vytvořitelné prostřednictvím `CoCreateInstance`.  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] CLSID implementované C++ třída s názvem třídy COM `class`.  
  
 `class`  
 [v] Název třídy C++ implementace třídy COM reprezentována `clsid`.  
  
### <a name="remarks"></a>Poznámky  
 Makra položky objektu jsou umístěny v globálním oboru v projektu kvůli zajištění podpory pro registraci, inicializace a vytvoření třídy.  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO` Umožňuje určit, že objekt zaregistrované a inicializovat (najdete v části [OBJECT_ENTRY_AUTO](#object_entry_auto) informace), ale nesmí být vytvořitelné prostřednictvím `CoCreateInstance`.  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
