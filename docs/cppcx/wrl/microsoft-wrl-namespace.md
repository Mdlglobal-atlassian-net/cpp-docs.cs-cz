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
ms.openlocfilehash: 749469c7ae2acf3a0da92d24a51bbfca9b68971d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392021"
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
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[ActivationFactory – třída](activationfactory-class.md)|Umožňuje jednu nebo více tříd aktivováno modulu Windows Runtime.|
|[AsyncBase – třída](asyncbase-class.md)|Implementuje asynchronní stav počítače Windows Runtime.|
|[ClassFactory – třída](classfactory-class.md)|Implementuje základní funkce `IClassFactory` rozhraní.|
|[ComPtr – třída](comptr-class.md)|Vytvoří *inteligentního ukazatele* typ, který představuje rozhraní určené typem parametru šablony. Comptr – automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.|
|[DeferrableEventArgs – třída](deferrableeventargs-class.md)|Třída šablony použité pro typy argumentů událostí pro odložení.|
|[EventSource – třída](eventsource-class.md)|Představuje událost. `EventSource` Členské funkce přidání, odebrání a vyvolání obslužných rutin událostí.|
|[FtmBase – třída](ftmbase-class.md)|Představuje objekt s volným zařazováním vláken.|
|[Module – třída](module-class.md)|Představuje kolekci souvisejících objektů.|
|[RuntimeClass – třída](runtimeclass-class.md)|Představuje instance třídy, která dědí určený počet rozhraní a poskytuje zadaného modulu Windows Runtime, klasické rozhraní COM a slabou podporu odkazu.|
|[SimpleActivationFactory – třída](simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasického modelu COM základní třídy.|
|[SimpleClassFactory – třída](simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|
|[WeakRef – třída](weakref-class.md)|Představuje *nestálý odkaz* , který lze používat pouze modulu Windows Runtime, ne klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[ChainInterfaces – struktura](chaininterfaces-structure.md)|Určuje, ověřování a Inicializace funkce, které mohou být použity na sadu rozhraní ID.|
|[CloakedIid – struktura](cloakediid-structure.md)|Pozná, `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, že zadané rozhraní není v seznamu IID k dispozici.|
|[Implements – struktura](implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaných rozhraní.|
|[MixIn – struktura](mixin-structure.md)|Zajišťuje, že runtime třídy je odvozen z rozhraní Windows Runtime, pokud existuje a potom klasické rozhraní COM.|
|[RuntimeClassFlags – struktura](runtimeclassflags-structure.md)|Obsahuje typ pro instanci [RuntimeClass](runtimeclass-class.md).|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[AsyncResultType – výčet](asyncresulttype-enumeration.md)|Určuje typ výsledku vrácený `GetResults()` metody.|
|[ModuleType – výčet](moduletype-enumeration.md)|Určuje, zda modul by měl podporovat v procesový server nebo server mimo proces.|
|[RuntimeClassType – výčet](runtimeclasstype-enumeration.md)|Určuje typ [RuntimeClass](runtimeclass-class.md) instanci, která je podporována.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[AsWeak – funkce](asweak-function.md)|Získá nestálý odkaz pro zadanou instanci.|
|[Zpětné volání – funkce (WRL)](callback-function-wrl.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|
|[CreateActivationFactory – funkce](createactivationfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy, které mohou být aktivovány modulem Windows Runtime.|
|[CreateClassFactory – funkce](createclassfactory-function.md)|Vytvoří objekt factory, který vytvoří instance dané třídy.|
|[Make – funkce](make-function.md)|Inicializuje zadanou třídu Windows Runtime.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Wrappers – obor názvů](microsoft-wrl-wrappers-namespace.md)