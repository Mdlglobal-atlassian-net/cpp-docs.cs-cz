---
title: "Module – třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module
dev_langs: C++
helpviewer_keywords: Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b2536d406293d84db2ce5d5bd3e0292e0e57920e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="module-class"></a>Modul – třída
Představuje kolekci související objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<  
   ModuleType moduleType  
>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleType`  
 Kombinace jednoho nebo více [ModuleType](../windows/moduletype-enumeration.md) hodnot výčtu.  
  
## <a name="members"></a>Členové  
  
### <a name="protected-classes"></a>Chráněné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier – třída](../windows/module-genericreleasenotifier-class.md)|Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je určena na lambda, functor nebo ukazatel funkce.|  
|[Module::MethodReleaseNotifier – třída](../windows/module-methodreleasenotifier-class.md)|Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je zadaný objekt a jejího člena ukazatel na metodu.|  
|[Module::ReleaseNotifier – třída](../windows/module-releasenotifier-class.md)|Vyvolá obslužnou rutinu události, až bude vydaná poslední objekt v modulu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Modul:: ~ Module – destruktor](../windows/module-tilde-module-destructor.md)|Deinitializes aktuální instance třídy modulu.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::module – konstruktor](../windows/module-module-constructor.md)|Inicializuje novou instanci třídy modulu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Create – metoda](../windows/module-create-method.md)|Vytvoří instanci modulu.|  
|[Module::decrementobjectcount – metoda](../windows/module-decrementobjectcount-method.md)|Snižuje počet objektů, které sledují modulem.|  
|[Module::getactivationfactory – metoda](../windows/module-getactivationfactory-method.md)|Získá objekt pro vytváření aktivace pro modul.|  
|[Module::GetClassObject – metoda](../windows/module-getclassobject-method.md)|Retreives mezipaměť pro vytváření tříd.|  
|[Module::getmodule – metoda](../windows/module-getmodule-method.md)|Vytvoří instanci modulu.|  
|[Module::getobjectcount – metoda](../windows/module-getobjectcount-method.md)|Načte počet objektů, které spravuje tento modul.|  
|[Module::incrementobjectcount – metoda](../windows/module-incrementobjectcount-method.md)|Zvýší počet objektů, které sledují modulem.|  
|[Module::registercomobject – metoda](../windows/module-registercomobject-method.md)|Zaregistruje jeden nebo více objektů COM, můžete k nim připojit jiné aplikace.|  
|[Module::registerobjects – metoda](../windows/module-registerobjects-method.md)|Zaregistruje objekty modelu COM nebo prostředí Windows Runtime, můžete k nim připojit jiné aplikace.|  
|[Module::registerwinrtobject – metoda](../windows/module-registerwinrtobject-method.md)|Jeden nebo více objektů prostředí Windows Runtime zaregistruje, takže k nim můžou připojit jiné aplikace.|  
|[Module::Terminate – metoda](../windows/module-terminate-method.md)|Způsobí, že všechny objekty Factory mohl vytvořit jeho instanci modulu vypnout.|  
|[Module::unregistercomobject – metoda](../windows/module-unregistercomobject-method.md)|Odregistruje jeden nebo více objektů COM, což zabraňuje dalších aplikací v připojení k nim.|  
|[Module::unregisterobjects – metoda](../windows/module-unregisterobjects-method.md)|Zruší registraci objekty v zadaný modul tak, aby ostatní aplikace se nemůže připojit k nim.|  
|[Module::unregisterwinrtobject – metoda](../windows/module-unregisterwinrtobject-method.md)|Zruší registraci jeden nebo více objektů prostředí Windows Runtime tak, aby ostatní aplikace se nemůže připojit k nim.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Create – metoda](../windows/module-create-method.md)|Vytvoří instanci modulu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::objectcount_ – datový člen](../windows/module-objectcount-data-member.md)|Uchovává informace o tom, kolik třídy byla vytvořena [zkontrolujte](../windows/make-function.md) funkce.|  
|[Module::releasenotifier_ – datový člen](../windows/module-releasenotifier-data-member.md)|Obsahuje ukazatele na objekt ReleaseNotifier.|  
  
### <a name="macros"></a>Makra  
  
|||  
|-|-|  
|[Activatableclass –](../windows/activatableclass-macros.md)|Naplní vnitřní mezipaměti, která obsahuje objekt factory, který můžete vytvořit instanci zadané třídy. Toto makro Určuje výchozí tovární nastavení a skupiny ID parametry.|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|Naplní vnitřní mezipaměti, která obsahuje objekt factory, který můžete vytvořit instanci zadané třídy. Toto makro umožňuje zadat parametr konkrétní objekt pro vytváření.|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|Naplní vnitřní mezipaměti, která obsahuje objekt factory, který můžete vytvořit instanci zadané třídy. Toto makro umožňuje určit konkrétní objekt pro vytváření a parametry ID skupiny.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)