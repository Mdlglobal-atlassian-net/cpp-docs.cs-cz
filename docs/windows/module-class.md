---
title: Module – třídy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
dev_langs:
- C++
helpviewer_keywords:
- Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af8fa5bbafa76ab13f14d1a10e040a38bc6e2fb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880579"
---
# <a name="module-class"></a>Modul – třída
Představuje kolekci související objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<ModuleType moduleType>  
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
|[Module::~Module – destruktor](../windows/module-tilde-module-destructor.md)|Deinitializes aktuální instance třídy modulu.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Module – konstruktor](../windows/module-module-constructor.md)|Inicializuje novou instanci třídy modulu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Create – metoda](../windows/module-create-method.md)|Vytvoří instanci modulu.|  
|[Module::DecrementObjectCount – metoda](../windows/module-decrementobjectcount-method.md)|Snižuje počet objektů, které sledují modulem.|  
|[Module::GetActivationFactory – metoda](../windows/module-getactivationfactory-method.md)|Získá objekt pro vytváření aktivace pro modul.|  
|[Module::GetClassObject – metoda](../windows/module-getclassobject-method.md)|Retreives mezipaměť pro vytváření tříd.|  
|[Module::GetModule – metoda](../windows/module-getmodule-method.md)|Vytvoří instanci modulu.|  
|[Module::GetObjectCount – metoda](../windows/module-getobjectcount-method.md)|Načte počet objektů, které spravuje tento modul.|  
|[Module::IncrementObjectCount – metoda](../windows/module-incrementobjectcount-method.md)|Zvýší počet objektů, které sledují modulem.|  
|[Module::RegisterCOMObject – metoda](../windows/module-registercomobject-method.md)|Zaregistruje jeden nebo více objektů COM, můžete k nim připojit jiné aplikace.|  
|[Module::RegisterObjects – metoda](../windows/module-registerobjects-method.md)|Zaregistruje objekty modelu COM nebo prostředí Windows Runtime, můžete k nim připojit jiné aplikace.|  
|[Module::RegisterWinRTObject – metoda](../windows/module-registerwinrtobject-method.md)|Jeden nebo více objektů prostředí Windows Runtime zaregistruje, takže k nim můžou připojit jiné aplikace.|  
|[Module::Terminate – metoda](../windows/module-terminate-method.md)|Způsobí, že všechny objekty Factory mohl vytvořit jeho instanci modulu vypnout.|  
|[Module::UnregisterCOMObject – metoda](../windows/module-unregistercomobject-method.md)|Odregistruje jeden nebo více objektů COM, což zabraňuje dalších aplikací v připojení k nim.|  
|[Module::UnregisterObjects – metoda](../windows/module-unregisterobjects-method.md)|Zruší registraci objekty v zadaný modul tak, aby ostatní aplikace se nemůže připojit k nim.|  
|[Module::UnregisterWinRTObject – metoda](../windows/module-unregisterwinrtobject-method.md)|Zruší registraci jeden nebo více objektů prostředí Windows Runtime tak, aby ostatní aplikace se nemůže připojit k nim.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Create – metoda](../windows/module-create-method.md)|Vytvoří instanci modulu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::objectCount_ – datový člen](../windows/module-objectcount-data-member.md)|Uchovává informace o tom, kolik třídy byla vytvořena [zkontrolujte](../windows/make-function.md) funkce.|  
|[Module::releaseNotifier_ – datový člen](../windows/module-releasenotifier-data-member.md)|Obsahuje ukazatele na objekt ReleaseNotifier.|  
  
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
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)