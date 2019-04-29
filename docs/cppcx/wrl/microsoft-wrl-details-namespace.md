---
title: Microsoft::WRL::Details – obor názvů
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: fce6e620600164e73d3708d98d8a7fa979e8ab42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392034"
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
|[ComPtrRef – třída](comptrref-class.md)|Představuje odkaz na objekt typu ComPtr\<T >.|
|[ComPtrRefBase – třída](comptrrefbase-class.md)|Představuje základní třídu pro [comptrref –](comptrref-class.md) třídy.|
|[DontUseNewUseMake – třída](dontusenewusemake-class.md)|Brání použití operátoru `new` v `RuntimeClass`. V důsledku toho je nutné použít [Make – funkce](make-function.md) místo.|
|[EventTargetArray – třída](eventtargetarray-class.md)|Reprezentuje pole prvků obslužných rutin událostí.|
|[MakeAllocator – třída](makeallocator-class.md)|Přiděluje paměť pro aktivovatelné třídy s nebo bez něj slabou podporu odkazu.|
|[ModuleBase – třída](modulebase-class.md)|Představuje základní třídu [modulu](module-class.md) třídy.|
|[RemoveIUnknown – třída](removeiunknown-class.md)|Vytvoří typ, který je ekvivalentní `IUnknown`– podle typu, ale má nevirtuální `QueryInterface`, `AddRef`, a `Release` metody.|
|[WeakReference – třída](weakreference-class.md)|Představuje *nestálý odkaz* , který je možné pomocí prostředí Windows Runtime nebo klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[ArgTraits – struktura](argtraits-structure.md)|Deklaruje zadaného delegáta, rozhraní a anonymní členskou funkci, která má zadaný počet parametrů.|
|[ArgTraitsHelper – struktura](argtraitshelper-structure.md)|Pomáhá definovat běžné vlastnosti argumenty delegátů.|
|[BoolStruct – struktura](boolstruct-structure.md)|Definuje, jestli `ComPtr` spravuje doba života objektu rozhraní. `BoolStruct` se používá interně pomocí [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operátor.|
|[CreatorMap – struktura](creatormap-structure.md)|Obsahuje informace o tom, jak inicializovat, vytvářet a rušit registraci objektů.|
|[DerefHelper – struktura](derefhelper-structure.md)|Představuje ukazatel přes ukazatel `T*` parametr šablony.|
|[EnableIf – struktura](enableif-structure.md)|Datový člen typu určené druhý parametr šablony, pokud je vyhodnocen jako první parametr šablony definuje `true`.|
|[FactoryCache – struktura](factorycache-structure.md)|Obsahuje umístění objektu pro vytváření tříd a hodnotu, která identifikuje registrovaného objektu třídy Windows Runtime nebo modelu COM.|
|[ImplementsBase – struktura](implementsbase-structure.md)|Používá se k ověření typy parametrů šablony v [Implements – struktura](implements-structure.md).|
|[ImplementsHelper – struktura](implementshelper-structure.md)|Pomáhá implementovat [implementuje](implements-structure.md) struktury.|
|[InterfaceList – struktura](interfacelist-structure.md)|Umožňuje vytvořit seznam rekurzivní rozhraní.|
|[InterfaceListHelper – struktura](interfacelisthelper-structure.md)|Sestavení `InterfaceList` typ podle rekurzivně použití určené šablony parametr argumentů.|
|[InterfaceTraits – struktura](interfacetraits-structure.md)|Implementuje běžné vlastnosti rozhraní.|
|[InvokeHelper – struktura](invokehelper-structure.md)|Poskytuje implementaci `Invoke()` metoda na základě zadané číslo a typ argumentů.|
|[IsBaseOfStrict – struktura](isbaseofstrict-structure.md)|Ověřuje, zda je jeden typ základ jiného.|
|[IsSame – struktura](issame-structure.md)|Testy, zda jeden zadaný typ je stejný jako jiný určený typ.|
|[Nil – struktura](nil-structure.md)|Slouží k označení parametrem šablony nespecifikovaná, volitelné.|
|[RemoveReference – struktura](removereference-structure.md)|Odebere odkaz nebo odkaz na r-hodnoty vlastností z dané třídy parametru šablony.|
|[RuntimeClassBase – struktura](runtimeclassbase-structure.md)|Slouží ke zjištění `RuntimeClass` v [zkontrolujte](make-function.md) funkce.|
|[RuntimeClassBaseT – struktura](runtimeclassbaset-structure.md)|Poskytuje pomocné metody pro `QueryInterface` operace a získat ID rozhraní.|
|[VerifyInheritanceHelper – struktura](verifyinheritancehelper-structure.md)|Ověřuje, zda jedno rozhraní je odvozena od jiného rozhraní.|
|[VerifyInterfaceHelper – struktura](verifyinterfacehelper-structure.md)|Ověřuje, že rozhraní určené parametrem šablony splňuje určité požadavky.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[AsyncStatusInternal – výčet](asyncstatusinternal-enumeration.md)|Určuje mapování mezi interní výčty pro stav asynchronní operace a `Windows::Foundation::AsyncStatus` výčtu.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[ActivationFactoryCallback – funkce](activationfactorycallback-function.md)|Získá objekt factory aktivace pro ID zadaná aktivace.|
|[Move – funkce](move-function.md)|Zadaný argument přesune z jednoho umístění do druhého.|
|[RaiseException – funkce](raiseexception-function.md)|Vyvolá výjimku v volajícího vlákna.|
|[Swap – funkce (WRL)](swap-function-wrl.md)|Vymění hodnoty dvou zadaných argumentů.|
|[TerminateMap – funkce](terminatemap-function.md)|Třída továrny v zadaném modulu vypne.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers – obor názvů](microsoft-wrl-wrappers-namespace.md)