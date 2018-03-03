---
title: "Klíč rozhraní API knihovny WRL podle kategorie | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ad38d1b24ca40b6209295f873bd44c54c3f6148
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="key-wrl-apis-by-category"></a>Nejdůležitější rozhraní API knihovny WRL podle kategorie
V následujících tabulkách jsou uvedeny primární třídy, struktury, funkcemi a makry v knihovna šablon C++ prostředí Windows Runtime. Konstrukce v pomocná obory názvů a třídy byly vynechány. Tyto seznamy posílení dokumentaci rozhraní API, která jsou uspořádána podle oboru názvů.  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|-----------|-----------------|  
|[ActivationFactory – třída](../windows/activationfactory-class.md)|Umožňuje jednu nebo více tříd, které chcete aktivovat pomocí prostředí Windows Runtime.|  
|[AsyncBase – třída](../windows/asyncbase-class.md)|Implementuje počítač asynchronní stavu prostředí Windows Runtime.|  
|[ClassFactory – třída](../windows/classfactory-class.md)|Implementuje základních funkcí `IClassFactory` rozhraní.|  
|[ComPtr – třída](../windows/comptr-class.md)|Vytvoří *chytré ukazatele* typ, který reprezentuje rozhraní zadané parametr šablony. ComPtr automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, kdy přestane počet odkazů na nulu.|  
|[Event – třída (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-class-windows-runtime-cpp-template-library.md)|Představuje událost.|  
|[EventSource – třída](../windows/eventsource-class.md)|Představuje událost. `EventSource`Členské funkce přidání, odebrání a vyvolání obslužné rutiny událostí.|  
|[FtmBase – třída](../windows/ftmbase-class.md)|Představuje objekt volné zařazování vláken.|  
|[HandleT – třída](../windows/handlet-class.md)|Představuje popisovač objektu.|  
|[HString – třída](../windows/hstring-class.md)|Poskytuje podporu pro manipulaci s HSTRING obslužné rutiny.|  
|[HStringReference – třída](../windows/hstringreference-class.md)|Představuje HSTRING, který je vytvořený z existujícího řetězce.|  
|[Module – třída](../windows/module-class.md)|Představuje kolekci související objekty.|  
|[Module::GenericReleaseNotifier – třída](../windows/module-genericreleasenotifier-class.md)|Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je určena na lambda, functor nebo ukazatel funkce.|  
|[Module::MethodReleaseNotifier – třída](../windows/module-methodreleasenotifier-class.md)|Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je zadaný objekt a jejího člena ukazatel na metodu.|  
|[Module::ReleaseNotifier – třída](../windows/module-releasenotifier-class.md)|Vyvolá obslužnou rutinu události, až bude vydaná poslední objekt v modulu.|  
|[RoInitializeWrapper – třída](../windows/roinitializewrapper-class.md)|Inicializuje prostředí Windows Runtime.|  
|[RuntimeClass – třída](../windows/runtimeclass-class.md)|Představuje instancí třídu, která dědí zadaný počet rozhraní a obsahuje zadané prostředí Windows Runtime, classic COM a slabé odkaz na podporu.|  
|[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření klasického základní třídy COM nebo prostředí Windows Runtime.|  
|[SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|  
|[WeakRef – třída](../windows/weakref-class.md)|Představuje *slabé odkaz* které lze použít pouze prostředí Windows Runtime, není klasického modelu COM. Slabé odkazy představuje objekt, který může nebo nemusí být dostupné.|  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|-----------|-----------------|  
|[ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)|Určuje ověření a Inicializace funkce, které mohou být použity pro sadu rozhraní ID.|  
|[CloakedIid – struktura](../windows/cloakediid-structure.md)|Ukazuje `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, není dostupný v seznamu IID specifikované rozhraní.|  
|[Implements – struktura](../windows/implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaná rozhraní.|  
|[MixIn – struktura](../windows/mixin-structure.md)|Zajišťuje třídu runtime, pochází z prostředí Windows Runtime rozhraní, pokud existuje a pak classic COM – rozhraní.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|-----------|-----------------|  
|[ActivateInstance – funkce](../windows/activateinstance-function.md)|Zaregistruje a načte instanci zadaného typu definované v zadané třídy ID.|  
|[AsWeak – funkce](../windows/asweak-function.md)|Načte slabé odkaz na zadané instanci.|  
|[Funkce zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|  
|[CreateActivationFactory – funkce](../windows/createactivationfactory-function.md)|Vytvoří objekt factory, který vytváří instance pro zadanou třídu, která může být aktivovaný pomocí prostředí Windows Runtime.|  
|[CreateClassFactory – funkce](../windows/createclassfactory-function.md)|Vytvoří objekt factory, který vytváří instance pro zadanou třídu.|  
|[GetActivationFactory – funkce](../windows/getactivationfactory-function.md)|Načte objekt pro vytváření aktivace pro typ zadaný v parametru šablony.|  
|[Make – funkce](../windows/make-function.md)|Inicializuje pro zadanou třídu prostředí Windows Runtime.|  
  
### <a name="macros"></a>Makra  
  
|Název|Popis|  
|-----------|-----------------|  
|[ActivatableClass – makra](../windows/activatableclass-macros.md)|Naplní vnitřní mezipaměti, která obsahuje objekt factory, který můžete vytvořit instanci zadané třídy.|  
|[InspectableClass – makro](../windows/inspectableclass-macro.md)|Nastaví úroveň runtime třídy název a vztah důvěryhodnosti.|  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)