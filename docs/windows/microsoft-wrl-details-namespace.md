---
title: 'Microsoft::WRL:: details – Namespace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3dd07ead0608657597a81b239732347f67455273
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436881"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details – obor názvů

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[ComPtrRef – třída](../windows/comptrref-class.md)|Představuje odkaz na objekt typu ComPtr\<T >.|
|[ComPtrRefBase – třída](../windows/comptrrefbase-class.md)|Představuje základní třídu pro [comptrref –](../windows/comptrref-class.md) třídy.|
|[DontUseNewUseMake – třída](../windows/dontusenewusemake-class.md)|Brání použití operátoru **nové** v `RuntimeClass`. V důsledku toho je nutné použít [Make – funkce](../windows/make-function.md) místo.|
|[EventTargetArray – třída](../windows/eventtargetarray-class.md)|Reprezentuje pole prvků obslužných rutin událostí.|
|[MakeAllocator – třída](../windows/makeallocator-class.md)|Přiděluje paměť pro aktivovatelné třídy s nebo bez něj slabou podporu odkazu.|
|[ModuleBase – třída](../windows/modulebase-class.md)|Představuje základní třídu [modulu](../windows/module-class.md) třídy.|
|[RemoveIUnknown – třída](../windows/removeiunknown-class.md)|Vytvoří typ, který je ekvivalentní `IUnknown`– podle typu, ale má nevirtuální `QueryInterface`, `AddRef`, a `Release` metody.|
|[Weakreference – třída](../windows/weakreference-class1.md)|Představuje *nestálý odkaz* , který je možné pomocí prostředí Windows Runtime nebo klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[ArgTraits – struktura](../windows/argtraits-structure.md)|Deklaruje zadaného delegáta, rozhraní a anonymní členskou funkci, která má zadaný počet parametrů.|
|[ArgTraitsHelper – struktura](../windows/argtraitshelper-structure.md)|Pomáhá definovat běžné vlastnosti argumenty delegátů.|
|[BoolStruct – struktura](../windows/boolstruct-structure.md)|Definuje, jestli `ComPtr` spravuje doba života objektu rozhraní. `BoolStruct` se používá interně pomocí [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operátor.|
|[CreatorMap – struktura](../windows/creatormap-structure.md)|Obsahuje informace o tom, jak inicializovat, vytvářet a rušit registraci objektů.|
|[DerefHelper – struktura](../windows/derefhelper-structure.md)|Představuje ukazatel přes ukazatel `T*` parametr šablony.|
|[EnableIf – struktura](../windows/enableif-structure.md)|Datový člen typu určené druhý parametr šablony, pokud je vyhodnocen jako první parametr šablony definuje **true**.|
|[FactoryCache – struktura](../windows/factorycache-structure.md)|Obsahuje umístění objektu pro vytváření tříd a hodnotu, která identifikuje registrovaného objektu třídy Windows Runtime nebo modelu COM.|
|[ImplementsBase – struktura](../windows/implementsbase-structure.md)|Používá se k ověření typy parametrů šablony v [Implements – struktura](../windows/implements-structure.md).|
|[ImplementsHelper – struktura](../windows/implementshelper-structure.md)|Pomáhá implementovat [implementuje](../windows/implements-structure.md) struktury.|
|[InterfaceList – struktura](../windows/interfacelist-structure.md)|Umožňuje vytvořit seznam rekurzivní rozhraní.|
|[InterfaceListHelper – struktura](../windows/interfacelisthelper-structure.md)|Sestavení `InterfaceList` typ podle rekurzivně použití určené šablony parametr argumentů.|
|[InterfaceTraits – struktura](../windows/interfacetraits-structure.md)|Implementuje běžné vlastnosti rozhraní.|
|[InvokeHelper – struktura](../windows/invokehelper-structure.md)|Poskytuje implementaci `Invoke()` metoda na základě zadané číslo a typ argumentů.|
|[IsBaseOfStrict – struktura](../windows/isbaseofstrict-structure.md)|Ověřuje, zda je jeden typ základ jiného.|
|[IsSame – struktura](../windows/issame-structure.md)|Testy, zda jeden zadaný typ je stejný jako jiný určený typ.|
|[Nil – struktura](../windows/nil-structure.md)|Slouží k označení parametrem šablony nespecifikovaná, volitelné.|
|[RemoveReference – struktura](../windows/removereference-structure.md)|Odebere odkaz nebo odkaz na r-hodnoty vlastností z dané třídy parametru šablony.|
|[RuntimeClassBase – struktura](../windows/runtimeclassbase-structure.md)|Slouží ke zjištění `RuntimeClass` v [zkontrolujte](../windows/make-function.md) funkce.|
|[RuntimeClassBaseT – struktura](../windows/runtimeclassbaset-structure.md)|Poskytuje pomocné metody pro `QueryInterface` operace a získat ID rozhraní.|
|[VerifyInheritanceHelper – struktura](../windows/verifyinheritancehelper-structure.md)|Ověřuje, zda jedno rozhraní je odvozena od jiného rozhraní.|
|[VerifyInterfaceHelper – struktura](../windows/verifyinterfacehelper-structure.md)|Ověřuje, že rozhraní určené parametrem šablony splňuje určité požadavky.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[AsyncStatusInternal – výčet](../windows/asyncstatusinternal-enumeration.md)|Určuje mapování mezi interní výčty pro stav asynchronní operace a `Windows::Foundation::AsyncStatus` výčtu.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[ActivationFactoryCallback – funkce](../windows/activationfactorycallback-function.md)|Získá objekt factory aktivace pro ID zadaná aktivace.|
|[Move – funkce](../windows/move-function.md)|Zadaný argument přesune z jednoho umístění do druhého.|
|[RaiseException – funkce](../windows/raiseexception-function.md)|Vyvolá výjimku v volajícího vlákna.|
|[Swap – funkce (knihovna šablon C++ prostředí Windows Runtime)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Vymění hodnoty dvou zadaných argumentů.|
|[TerminateMap – funkce](../windows/terminatemap-function.md)|Třída továrny v zadaném modulu vypne.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)