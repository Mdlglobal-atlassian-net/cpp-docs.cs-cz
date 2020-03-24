---
title: Microsoft::WRL::Details – obor názvů
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 4e8d2e5a2c7e6655674c4e965cd7222d930dff9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213782"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details – obor názvů

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[ComPtrRef – třída](comptrref-class.md)|Představuje odkaz na objekt typu ComPtr\<T >.|
|[ComPtrRefBase – třída](comptrrefbase-class.md)|Představuje základní třídu pro třídu [ComPtrRef](comptrref-class.md) .|
|[DontUseNewUseMake – třída](dontusenewusemake-class.md)|Zabraňuje použití `new` operátoru v `RuntimeClass`. V důsledku toho je nutné použít [funkci make](make-function.md) .|
|[EventTargetArray – třída](eventtargetarray-class.md)|Představuje pole obslužných rutin událostí.|
|[MakeAllocator – třída](makeallocator-class.md)|Přiděluje paměť pro třídu aktivovatelné s nebo bez slabé referenční podpory.|
|[ModuleBase – třída](modulebase-class.md)|Představuje základní třídu tříd [modulů](module-class.md) .|
|[RemoveIUnknown – třída](removeiunknown-class.md)|Vytvoří typ, který je ekvivalentní typu `IUnknown`, ale má nevirtuální `QueryInterface`, `AddRef`a metody `Release`.|
|[WeakReference – třída](weakreference-class.md)|Představuje *slabý odkaz* , který lze použít s prostředí Windows Runtime nebo klasickým com. Slabý odkaz představuje objekt, který může nebo nemusí být přístupný.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[ArgTraits – struktura](argtraits-structure.md)|Deklaruje zadané rozhraní delegáta a anonymní členskou funkci, která má zadaný počet parametrů.|
|[ArgTraitsHelper – struktura](argtraitshelper-structure.md)|Pomáhá definovat společné charakteristiky argumentů delegátů.|
|[BoolStruct – struktura](boolstruct-structure.md)|Definuje, zda `ComPtr` spravuje dobu života objektu rozhraní. `BoolStruct` se interně používá pomocí operátoru [BoolType – ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .|
|[CreatorMap – struktura](creatormap-structure.md)|Obsahuje informace o tom, jak inicializovat, registrovat a rušit registraci objektů.|
|[DerefHelper – struktura](derefhelper-structure.md)|Reprezentuje ukazatel s odkazem na `T*` parametr šablony.|
|[EnableIf – struktura](enableif-structure.md)|Definuje datový člen typu určeného druhým parametrem šablony, pokud je první parametr šablony vyhodnocen jako `true`.|
|[FactoryCache – struktura](factorycache-structure.md)|Obsahuje umístění objektu pro vytváření tříd a hodnotu, která identifikuje registrovaný prostředí Windows Runtime nebo objekt třídy COM.|
|[ImplementsBase – struktura](implementsbase-structure.md)|Slouží k ověření typů parametrů šablony v [implementaci struktury](implements-structure.md).|
|[ImplementsHelper – struktura](implementshelper-structure.md)|Pomáhá implementovat strukturu [implementací](implements-structure.md) .|
|[InterfaceList – struktura](interfacelist-structure.md)|Slouží k vytvoření rekurzivního seznamu rozhraní.|
|[InterfaceListHelper – struktura](interfacelisthelper-structure.md)|Vytvoří `InterfaceList` typ rekurzivním aplikováním zadaných argumentů parametrů šablony.|
|[InterfaceTraits – struktura](interfacetraits-structure.md)|Implementuje běžné charakteristiky rozhraní.|
|[InvokeHelper – struktura](invokehelper-structure.md)|Poskytuje implementaci metody `Invoke()` na základě zadaného počtu a typu argumentů.|
|[IsBaseOfStrict – struktura](isbaseofstrict-structure.md)|Testuje, zda je jeden typ základem jiného typu.|
|[IsSame – struktura](issame-structure.md)|Testuje, zda je jeden zadaný typ stejný jako jiný zadaný typ.|
|[Nil – struktura](nil-structure.md)|Slouží k označení neurčeného volitelného parametru šablony.|
|[RemoveReference – struktura](removereference-structure.md)|Odstraní odkaz nebo vlastnost rvalue-reference ze zadaného parametru šablony třídy.|
|[RuntimeClassBase – struktura](runtimeclassbase-structure.md)|Slouží k detekci `RuntimeClass` ve funkci [make](make-function.md) .|
|[RuntimeClassBaseT – struktura](runtimeclassbaset-structure.md)|Poskytuje podpůrné metody pro operace `QueryInterface` a získávání ID rozhraní.|
|[VerifyInheritanceHelper – struktura](verifyinheritancehelper-structure.md)|Testuje, zda je jedno rozhraní odvozeno z jiného rozhraní.|
|[VerifyInterfaceHelper – struktura](verifyinterfacehelper-structure.md)|Ověřuje, že rozhraní určené parametrem šablony splňuje určité požadavky.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[AsyncStatusInternal – výčet](asyncstatusinternal-enumeration.md)|Určuje mapování mezi interními výčty pro stav asynchronních operací a výčet `Windows::Foundation::AsyncStatus`.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[ActivationFactoryCallback – funkce](activationfactorycallback-function.md)|Získá továrnu aktivace pro zadané ID aktivace.|
|[Move – funkce](move-function.md)|Přesune zadaný argument z jednoho umístění do druhého.|
|[RaiseException – funkce](raiseexception-function.md)|Vyvolá výjimku ve volajícím vlákně.|
|[Swap – funkce (WRL)](swap-function-wrl.md)|Vyměňuje hodnoty dvou zadaných argumentů.|
|[TerminateMap – funkce](terminatemap-function.md)|Vypne továrny tříd v zadaném modulu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, Implements. h, Internal. h, Module. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers – obor názvů](microsoft-wrl-wrappers-namespace.md)
