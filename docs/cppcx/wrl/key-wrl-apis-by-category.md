---
title: Nejdůležitější rozhraní API knihovny WRL podle kategorie
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: 8ac89f3286866ac61bac5ae256bdb448fe88f07d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213821"
---
# <a name="key-wrl-apis-by-category"></a>Nejdůležitější rozhraní API knihovny WRL podle kategorie

V následujících tabulkách jsou uvedeny primární C++ třídy, struktury, funkce a makra knihovny šablon prostředí Windows Runtime. Konstrukce v oborech názvů a třídách pomocníka jsou vynechány. Tyto seznamy rozšiřují dokumentaci rozhraní API, která je uspořádána podle oboru názvů.

## <a name="classes"></a>Třídy

|Název|Popis|
|-----------|-----------------|
|[ActivationFactory – třída](activationfactory-class.md)|Umožňuje aktivovat jednu nebo více tříd prostředí Windows Runtime.|
|[AsyncBase – třída](asyncbase-class.md)|Implementuje prostředí Windows Runtime asynchronní Stavový počítač.|
|[ClassFactory – třída](classfactory-class.md)|Implementuje základní funkce rozhraní `IClassFactory`.|
|[ComPtr – třída](comptr-class.md)|Vytvoří typ *inteligentního ukazatele* , který představuje rozhraní určené parametrem šablony. ComPtr automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, když počet odkazů překročí nulu.|
|[Event – třída (knihovna šablon C++ prostředí Windows Runtime)](event-class-wrl.md)|Představuje událost.|
|[EventSource – třída](eventsource-class.md)|Představuje událost. `EventSource` členské funkce přidávají, odstraňují a vyvolávají obslužné rutiny událostí.|
|[FtmBase – třída](ftmbase-class.md)|Představuje objekt zařazovacího objektu s volnými vlákny.|
|[HandleT – třída](handlet-class.md)|Představuje popisovač objektu.|
|[HString – třída](hstring-class.md)|Poskytuje podporu pro manipulaci s HSTRING popisovači.|
|[HStringReference – třída](hstringreference-class.md)|Představuje HSTRING, který je vytvořen z existujícího řetězce.|
|[Module – třída](module-class.md)|Představuje kolekci souvisejících objektů.|
|[Module::GenericReleaseNotifier – třída](module-genericreleasenotifier-class.md)|Vyvolá obslužnou rutinu události při uvolnění posledního objektu v aktuálním modulu. Obslužná rutina události je určena výrazem lambda, funktor nebo ukazatelem na funkci.|
|[Module::MethodReleaseNotifier – třída](module-methodreleasenotifier-class.md)|Vyvolá obslužnou rutinu události při uvolnění posledního objektu v aktuálním modulu. Obslužná rutina události je určena objektem a jeho členem ukazatel na metodu.|
|[Module::ReleaseNotifier – třída](module-releasenotifier-class.md)|Vyvolá obslužnou rutinu události při uvolnění posledního objektu v modulu.|
|[RoInitializeWrapper – třída](roinitializewrapper-class.md)|Inicializuje prostředí Windows Runtime.|
|[RuntimeClass – třída](runtimeclass-class.md)|Představuje instanci třídy, která dědí zadaný počet rozhraní, a poskytuje určený prostředí Windows Runtime, klasický model COM a podporu slabých odkazů.|
|[SimpleActivationFactory – třída](simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasické základní třídy modelu COM.|
|[SimpleClassFactory – třída](simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|
|[WeakRef – třída](weakref-class.md)|Představuje *slabý odkaz* , který může být použit pouze v prostředí Windows Runtime, nikoli v klasickém modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být přístupný.|

## <a name="structures"></a>Struktury

|Název|Popis|
|-----------|-----------------|
|[ChainInterfaces – struktura](chaininterfaces-structure.md)|Určuje funkce pro ověřování a inicializaci, které lze použít pro sadu identifikátorů rozhraní.|
|[CloakedIid – struktura](cloakediid-structure.md)|Označuje `RuntimeClass`a šablony `Implements` a `ChainInterfaces`, které zadané rozhraní není dostupné v seznamu IID.|
|[Implements – struktura](implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaná rozhraní.|
|[MixIn – struktura](mixin-structure.md)|Zajišťuje, že třída modulu runtime je odvozena z prostředí Windows Runtime rozhraní, pokud existují, a pak rozhraní modelu COM Classic.|

## <a name="functions"></a>Funkce

|Název|Popis|
|-----------|-----------------|
|[ActivateInstance – funkce](activateinstance-function.md)|Zaregistruje a načte instanci zadaného typu definovaného v zadaném ID třídy.|
|[AsWeak – funkce](asweak-function.md)|Načte slabý odkaz na zadanou instanci.|
|[Funkce zpětného volání](callback-function-wrl.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|
|[CreateActivationFactory – funkce](createactivationfactory-function.md)|Vytvoří objekt pro vytváření, který vytváří instance zadané třídy, které mohou být aktivovány prostředí Windows Runtime.|
|[CreateClassFactory – funkce](createclassfactory-function.md)|Vytvoří objekt pro vytváření, který vytváří instance zadané třídy.|
|[GetActivationFactory – funkce](getactivationfactory-function.md)|Načte objekt pro vytváření aktivace pro typ určený parametrem šablony.|
|[Make – funkce](make-function.md)|Inicializuje určenou třídu prostředí Windows Runtime.|

## <a name="macros"></a>Makra

|Název|Popis|
|-----------|-----------------|
|[ActivatableClass – makra](activatableclass-macros.md)|Naplní interní mezipaměť, která obsahuje objekt pro vytváření, který může vytvořit instanci zadané třídy.|
|[InspectableClass – makro](inspectableclass-macro.md)|Nastaví název třídy modulu runtime a úroveň důvěryhodnosti.|

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)
