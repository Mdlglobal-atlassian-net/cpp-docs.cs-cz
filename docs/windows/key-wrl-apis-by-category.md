---
title: Klíč rozhraní API knihovny WRL podle kategorie | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b6d6bd580faf8c242ca5ac5e9b4b29ded9a7750a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612207"
---
# <a name="key-wrl-apis-by-category"></a>Nejdůležitější rozhraní API knihovny WRL podle kategorie
V následujících tabulkách jsou uvedeny primární knihovna šablon C++ Windows Runtime třídy, struktury, funkce a makra. Konstrukce v pomocné rutiny obory názvů a třídy jsou vynechány. Tyto seznamy rozšířit dokumentaci k rozhraní API, která jsou uspořádána podle oborů názvů.
  
### <a name="classes"></a>Třídy
  
|Název|Popis|
|-----------|-----------------|
|[ActivationFactory – třída](../windows/activationfactory-class.md)|Umožňuje jednu nebo více tříd aktivováno modulu Windows Runtime.|
|[AsyncBase – třída](../windows/asyncbase-class.md)|Implementuje asynchronní stav počítače Windows Runtime.|
|[ClassFactory – třída](../windows/classfactory-class.md)|Implementuje základní funkce `IClassFactory` rozhraní.|
|[ComPtr – třída](../windows/comptr-class.md)|Vytvoří *inteligentního ukazatele* typ, který představuje rozhraní určené typem parametru šablony. Comptr – automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.|
|[Event – třída (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-class-windows-runtime-cpp-template-library.md)|Představuje událost.|
|[EventSource – třída](../windows/eventsource-class.md)|Představuje událost. `EventSource` Členské funkce přidání, odebrání a vyvolání obslužných rutin událostí.|
|[FtmBase – třída](../windows/ftmbase-class.md)|Představuje objekt s volným zařazováním vláken.|
|[HandleT – třída](../windows/handlet-class.md)|Reprezentuje popisovač objektu.|
|[HString – třída](../windows/hstring-class.md)|Poskytuje podporu pro práci s popisovači HSTRING.|
|[HStringReference – třída](../windows/hstringreference-class.md)|Představuje HSTRING, který je vytvořený z existujícího řetězce.|
|[Module – třída](../windows/module-class.md)|Představuje kolekci souvisejících objektů.|
|[Module::GenericReleaseNotifier – třída](../windows/module-genericreleasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný ve výrazu lambda, funktor nebo ukazatel na funkci.|
|[Module::MethodReleaseNotifier – třída](../windows/module-methodreleasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.|
|[Module::ReleaseNotifier – třída](../windows/module-releasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.|
|[RoInitializeWrapper – třída](../windows/roinitializewrapper-class.md)|Inicializuje modul Windows Runtime.|
|[RuntimeClass – třída](../windows/runtimeclass-class.md)|Představuje instance třídy, která dědí určený počet rozhraní a poskytuje zadaného modulu Windows Runtime, klasické rozhraní COM a slabou podporu odkazu.|
|[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasického modelu COM základní třídy.|
|[SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|
|[WeakRef – třída](../windows/weakref-class.md)|Představuje *nestálý odkaz* , který lze používat pouze modulu Windows Runtime, ne klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.|
  
### <a name="structures"></a>Struktury
  
|Název|Popis|
|-----------|-----------------|
|[ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)|Určuje, ověřování a Inicializace funkce, které mohou být použity na sadu rozhraní ID.|
|[CloakedIid – struktura](../windows/cloakediid-structure.md)|Pozná, `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, že zadané rozhraní není v seznamu IID k dispozici.|
|[Implements – struktura](../windows/implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaných rozhraní.|
|[MixIn – struktura](../windows/mixin-structure.md)|Zajišťuje, že runtime třídy je odvozen z rozhraní Windows Runtime, pokud existuje a potom klasické rozhraní COM.|
  
### <a name="functions"></a>Funkce
  
|Název|Popis|
|-----------|-----------------|
|[ActivateInstance – funkce](../windows/activateinstance-function.md)|Zaregistruje a načte instanci zadaného typu definované v ID zadané třídy.|
|[AsWeak – funkce](../windows/asweak-function.md)|Získá nestálý odkaz pro zadanou instanci.|
|[Funkce zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|
|[CreateActivationFactory – funkce](../windows/createactivationfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy, které mohou být aktivovány modulem Windows Runtime.|
|[CreateClassFactory – funkce](../windows/createclassfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy.|
|[GetActivationFactory – funkce](../windows/getactivationfactory-function.md)|Načte objekt factory pro aktivaci pro typ zadaný v parametru šablony.|
|[Make – funkce](../windows/make-function.md)|Inicializuje zadanou třídu Windows Runtime.|
  
### <a name="macros"></a>Makra
  
|Název|Popis|
|-----------|-----------------|
|[ActivatableClass – makra](../windows/activatableclass-macros.md)|Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy.|
|[InspectableClass – makro](../windows/inspectableclass-macro.md)|Nastaví runtime název a vztah důvěryhodnosti na úrovni třídy.|
  
## <a name="see-also"></a>Viz také
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)