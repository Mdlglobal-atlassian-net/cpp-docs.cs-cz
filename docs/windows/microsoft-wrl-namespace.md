---
title: Microsoft::WRL – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: a615e77c96901f2cdf211b9646b2b7b0512b99de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487448"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL – obor názvů

Definuje základní typy, které tvoří knihovna šablon C++ Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[ActivationFactory – třída](../windows/activationfactory-class.md)|Umožňuje jednu nebo více tříd aktivováno modulu Windows Runtime.|
|[AsyncBase – třída](../windows/asyncbase-class.md)|Implementuje asynchronní stav počítače Windows Runtime.|
|[ClassFactory – třída](../windows/classfactory-class.md)|Implementuje základní funkce `IClassFactory` rozhraní.|
|[ComPtr – třída](../windows/comptr-class.md)|Vytvoří *inteligentního ukazatele* typ, který představuje rozhraní určené typem parametru šablony. Comptr – automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.|
|[DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md)|Třída šablony použité pro typy argumentů událostí pro odložení.|
|[EventSource – třída](../windows/eventsource-class.md)|Představuje událost. `EventSource` Členské funkce přidání, odebrání a vyvolání obslužných rutin událostí.|
|[FtmBase – třída](../windows/ftmbase-class.md)|Představuje objekt s volným zařazováním vláken.|
|[Module – třída](../windows/module-class.md)|Představuje kolekci souvisejících objektů.|
|[RuntimeClass – třída](../windows/runtimeclass-class.md)|Představuje instance třídy, která dědí určený počet rozhraní a poskytuje zadaného modulu Windows Runtime, klasické rozhraní COM a slabou podporu odkazu.|
|[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasického modelu COM základní třídy.|
|[SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|
|[WeakRef – třída](../windows/weakref-class.md)|Představuje *nestálý odkaz* , který lze používat pouze modulu Windows Runtime, ne klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)|Určuje, ověřování a Inicializace funkce, které mohou být použity na sadu rozhraní ID.|
|[CloakedIid – struktura](../windows/cloakediid-structure.md)|Pozná, `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, že zadané rozhraní není v seznamu IID k dispozici.|
|[Implements – struktura](../windows/implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaných rozhraní.|
|[MixIn – struktura](../windows/mixin-structure.md)|Zajišťuje, že runtime třídy je odvozen z rozhraní Windows Runtime, pokud existuje a potom klasické rozhraní COM.|
|[RuntimeClassFlags – struktura](../windows/runtimeclassflags-structure.md)|Obsahuje typ pro instanci [RuntimeClass](../windows/runtimeclass-class.md).|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[AsyncResultType – výčet](../windows/asyncresulttype-enumeration.md)|Určuje typ výsledku vrácený `GetResults()` metody.|
|[ModuleType – výčet](../windows/moduletype-enumeration.md)|Určuje, zda modul by měl podporovat v procesový server nebo server mimo proces.|
|[RuntimeClassType – výčet](../windows/runtimeclasstype-enumeration.md)|Určuje typ [RuntimeClass](../windows/runtimeclass-class.md) instanci, která je podporována.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[AsWeak – funkce](../windows/asweak-function.md)|Získá nestálý odkaz pro zadanou instanci.|
|[Zpětné volání – funkce (WRL)](../windows/callback-function-wrl.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|
|[CreateActivationFactory – funkce](../windows/createactivationfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy, které mohou být aktivovány modulem Windows Runtime.|
|[CreateClassFactory – funkce](../windows/createclassfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy.|
|[Make – funkce](../windows/make-function.md)|Inicializuje zadanou třídu Windows Runtime.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)