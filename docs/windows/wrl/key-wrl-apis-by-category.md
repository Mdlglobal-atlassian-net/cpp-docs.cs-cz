---
title: Nejdůležitější rozhraní API knihovny WRL podle kategorie
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: fd4bebf9c823079c3bdb4c4182bf3f30cdf105a7
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334735"
---
# <a name="key-wrl-apis-by-category"></a>Nejdůležitější rozhraní API knihovny WRL podle kategorie

V následujících tabulkách jsou uvedeny primární knihovna šablon C++ Windows Runtime třídy, struktury, funkce a makra. Konstrukce v pomocné rutiny obory názvů a třídy jsou vynechány. Tyto seznamy rozšířit dokumentaci k rozhraní API, která jsou uspořádána podle oborů názvů.

## <a name="classes"></a>Třídy

|Název|Popis|
|-----------|-----------------|
|[ActivationFactory – třída](activationfactory-class.md)|Umožňuje jednu nebo více tříd aktivováno modulu Windows Runtime.|
|[AsyncBase – třída](asyncbase-class.md)|Implementuje asynchronní stav počítače Windows Runtime.|
|[ClassFactory – třída](classfactory-class.md)|Implementuje základní funkce `IClassFactory` rozhraní.|
|[ComPtr – třída](comptr-class.md)|Vytvoří *inteligentního ukazatele* typ, který představuje rozhraní určené typem parametru šablony. Comptr – automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.|
|[Event – třída (knihovna šablon C++ prostředí Windows Runtime)](event-class-wrl.md)|Představuje událost.|
|[EventSource – třída](eventsource-class.md)|Představuje událost. `EventSource` Členské funkce přidání, odebrání a vyvolání obslužných rutin událostí.|
|[FtmBase – třída](ftmbase-class.md)|Představuje objekt s volným zařazováním vláken.|
|[HandleT – třída](handlet-class.md)|Reprezentuje popisovač objektu.|
|[HString – třída](hstring-class.md)|Poskytuje podporu pro práci s popisovači HSTRING.|
|[HStringReference – třída](hstringreference-class.md)|Představuje HSTRING, který je vytvořený z existujícího řetězce.|
|[Module – třída](module-class.md)|Představuje kolekci souvisejících objektů.|
|[Module::GenericReleaseNotifier – třída](module-genericreleasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný ve výrazu lambda, funktor nebo ukazatel na funkci.|
|[Module::MethodReleaseNotifier – třída](module-methodreleasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.|
|[Module::ReleaseNotifier – třída](module-releasenotifier-class.md)|Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.|
|[RoInitializeWrapper – třída](roinitializewrapper-class.md)|Inicializuje modul Windows Runtime.|
|[RuntimeClass – třída](runtimeclass-class.md)|Představuje instance třídy, která dědí určený počet rozhraní a poskytuje zadaného modulu Windows Runtime, klasické rozhraní COM a slabou podporu odkazu.|
|[SimpleActivationFactory – třída](simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasického modelu COM základní třídy.|
|[SimpleClassFactory – třída](simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|
|[WeakRef – třída](weakref-class.md)|Představuje *nestálý odkaz* , který lze používat pouze modulu Windows Runtime, ne klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.|

## <a name="structures"></a>Struktury

|Název|Popis|
|-----------|-----------------|
|[ChainInterfaces – struktura](chaininterfaces-structure.md)|Určuje, ověřování a Inicializace funkce, které mohou být použity na sadu rozhraní ID.|
|[CloakedIid – struktura](cloakediid-structure.md)|Pozná, `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, že zadané rozhraní není v seznamu IID k dispozici.|
|[Implements – struktura](implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaných rozhraní.|
|[MixIn – struktura](mixin-structure.md)|Zajišťuje, že runtime třídy je odvozen z rozhraní Windows Runtime, pokud existuje a potom klasické rozhraní COM.|

## <a name="functions"></a>Funkce

|Název|Popis|
|-----------|-----------------|
|[ActivateInstance – funkce](activateinstance-function.md)|Zaregistruje a načte instanci zadaného typu definované v ID zadané třídy.|
|[AsWeak – funkce](asweak-function.md)|Získá nestálý odkaz pro zadanou instanci.|
|[Funkce zpětného volání](callback-function-wrl.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|
|[CreateActivationFactory – funkce](createactivationfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy, které mohou být aktivovány modulem Windows Runtime.|
|[CreateClassFactory – funkce](createclassfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy.|
|[GetActivationFactory – funkce](getactivationfactory-function.md)|Načte objekt factory pro aktivaci pro typ zadaný v parametru šablony.|
|[Make – funkce](make-function.md)|Inicializuje zadanou třídu Windows Runtime.|

## <a name="macros"></a>Makra

|Název|Popis|
|-----------|-----------------|
|[ActivatableClass – makra](activatableclass-macros.md)|Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy.|
|[InspectableClass – makro](inspectableclass-macro.md)|Nastaví runtime název a vztah důvěryhodnosti na úrovni třídy.|

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)