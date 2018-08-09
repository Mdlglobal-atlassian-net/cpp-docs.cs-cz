---
title: Třídy modulu | Dokumentace Microsoftu
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
ms.openlocfilehash: 2d097c5c1193b74aa3e4d6ecea755390b0885a8d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013057"
---
# <a name="module-class"></a>Modul – třída
Představuje kolekci souvisejících objektů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<ModuleType moduleType>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
### <a name="parameters"></a>Parametry  
 *Element moduleType*  
 Kombinace jedné nebo více [ModuleType](../windows/moduletype-enumeration.md) hodnot výčtu.  
  
## <a name="members"></a>Členové  
  
### <a name="protected-classes"></a>Chráněné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier – třída](../windows/module-genericreleasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný ve výrazu lambda, funktor nebo ukazatel na funkci.|  
|[Module::MethodReleaseNotifier – třída](../windows/module-methodreleasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.|  
|[Module::ReleaseNotifier – třída](../windows/module-releasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::~Module – destruktor](../windows/module-tilde-module-destructor.md)|Zruší inicializaci aktuální instance **modulu** třídy.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Module – konstruktor](../windows/module-module-constructor.md)|Inicializuje novou instanci třídy **modulu** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Create – metoda](../windows/module-create-method.md)|Vytvoří instanci modulu.|  
|[Module::DecrementObjectCount – metoda](../windows/module-decrementobjectcount-method.md)|Sníží počet objektů, které sledují modulem.|  
|[Module::GetActivationFactory – metoda](../windows/module-getactivationfactory-method.md)|Získá objekt factory pro aktivaci pro modul.|  
|[Module::GetClassObject – metoda](../windows/module-getclassobject-method.md)|Načte mezipaměť objekty pro vytváření tříd.|  
|[Module::GetModule – metoda](../windows/module-getmodule-method.md)|Vytvoří instanci modulu.|  
|[Module::GetObjectCount – metoda](../windows/module-getobjectcount-method.md)|Získá počet objektů, které spravuje tento modul.|  
|[Module::IncrementObjectCount – metoda](../windows/module-incrementobjectcount-method.md)|Zvýší počet objektů, které jsou sledovány v rámci modulu.|  
|[Module::RegisterCOMObject – metoda](../windows/module-registercomobject-method.md)|Zaregistruje jeden nebo více objektů modelu COM, takže k nim mohli připojit další aplikace.|  
|[Module::RegisterObjects – metoda](../windows/module-registerobjects-method.md)|Zaregistruje objekty COM nebo prostředí Windows Runtime, takže k nim mohli připojit další aplikace.|  
|[Module::RegisterWinRTObject – metoda](../windows/module-registerwinrtobject-method.md)|Zaregistruje jeden nebo více objektů prostředí Windows Runtime, takže k nim mohli připojit další aplikace.|  
|[Module::Terminate – metoda](../windows/module-terminate-method.md)|Způsobí, že všechny objekty pro vytváření vytvořit instanci modulu pro vypnutí.|  
|[Module::UnregisterCOMObject – metoda](../windows/module-unregistercomobject-method.md)|Zruší jeden nebo více objektů modelu COM, registraci což zabrání aplikacím bránily v připojení k nim.|  
|[Module::UnregisterObjects – metoda](../windows/module-unregisterobjects-method.md)|Zruší registraci objekty v zadaném modulu tak, aby k nim nelze připojit další aplikace.|  
|[Module::UnregisterWinRTObject – metoda](../windows/module-unregisterwinrtobject-method.md)|Zruší registraci jeden nebo více objektů prostředí Windows Runtime, tak, aby k nim nelze připojit další aplikace.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::Create – metoda](../windows/module-create-method.md)|Vytvoří instanci modulu.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::objectCount_ – datový člen](../windows/module-objectcount-data-member.md)|Uchovává informace o tom, kolik třídy byly vytvořeny s [zkontrolujte](../windows/make-function.md) funkce.|  
|[Module::releaseNotifier_ – datový člen](../windows/module-releasenotifier-data-member.md)|Uchovává ukazatel `ReleaseNotifier` objektu.|  
  
### <a name="macros"></a>Makra  
  
|||  
|-|-|  
|[Activatableclass –](../windows/activatableclass-macros.md)|Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy. Toto makro Určuje výchozí objekt pro vytváření a skupiny ID parametry.|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy. Toto makro umožňuje zadat parametr konkrétní objekt pro vytváření.|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy. Toto makro umožňuje určit konkrétní objekt pro vytváření a parametry ID skupiny.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)