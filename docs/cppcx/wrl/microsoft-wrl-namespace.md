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
ms.openlocfilehash: c92251dacbfa17e8f1ac0cbdc41aa9b06118ac91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213769"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL – obor názvů

Definuje základní typy, které tvoří knihovnu šablon prostředí Windows Runtime C++ .

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
|[ActivationFactory – třída](activationfactory-class.md)|Umožňuje aktivovat jednu nebo více tříd prostředí Windows Runtime.|
|[AsyncBase – třída](asyncbase-class.md)|Implementuje prostředí Windows Runtime asynchronní Stavový počítač.|
|[ClassFactory – třída](classfactory-class.md)|Implementuje základní funkce rozhraní `IClassFactory`.|
|[ComPtr – třída](comptr-class.md)|Vytvoří typ *inteligentního ukazatele* , který představuje rozhraní určené parametrem šablony. ComPtr automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, když počet odkazů překročí nulu.|
|[DeferrableEventArgs – třída](deferrableeventargs-class.md)|Třída šablony používaná pro typy argumentů události pro odložení.|
|[EventSource – třída](eventsource-class.md)|Představuje událost. `EventSource` členské funkce přidávají, odstraňují a vyvolávají obslužné rutiny událostí.|
|[FtmBase – třída](ftmbase-class.md)|Představuje objekt zařazovacího objektu s volnými vlákny.|
|[Module – třída](module-class.md)|Představuje kolekci souvisejících objektů.|
|[RuntimeClass – třída](runtimeclass-class.md)|Představuje instanci třídy, která dědí zadaný počet rozhraní, a poskytuje určený prostředí Windows Runtime, klasický model COM a podporu slabých odkazů.|
|[SimpleActivationFactory – třída](simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasické základní třídy modelu COM.|
|[SimpleClassFactory – třída](simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|
|[WeakRef – třída](weakref-class.md)|Představuje *slabý odkaz* , který může být použit pouze v prostředí Windows Runtime, nikoli v klasickém modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být přístupný.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[ChainInterfaces – struktura](chaininterfaces-structure.md)|Určuje funkce pro ověřování a inicializaci, které lze použít pro sadu identifikátorů rozhraní.|
|[CloakedIid – struktura](cloakediid-structure.md)|Označuje `RuntimeClass`a šablony `Implements` a `ChainInterfaces`, které zadané rozhraní není dostupné v seznamu IID.|
|[Implements – struktura](implements-structure.md)|Implementuje `QueryInterface` a `GetIid` pro zadaná rozhraní.|
|[MixIn – struktura](mixin-structure.md)|Zajišťuje, že třída modulu runtime je odvozena z prostředí Windows Runtime rozhraní, pokud existují, a pak rozhraní modelu COM Classic.|
|[RuntimeClassFlags – struktura](runtimeclassflags-structure.md)|Obsahuje typ pro instanci třídy [RuntimeClass](runtimeclass-class.md).|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[AsyncResultType – výčet](asyncresulttype-enumeration.md)|Určuje typ výsledku vrácený metodou `GetResults()`.|
|[ModuleType – výčet](moduletype-enumeration.md)|Určuje, jestli má modul podporovat server v rámci procesu nebo server mimo proces.|
|[RuntimeClassType – výčet](runtimeclasstype-enumeration.md)|Určuje typ instance [RuntimeClass](runtimeclass-class.md) , která je podporována.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[AsWeak – funkce](asweak-function.md)|Načte slabý odkaz na zadanou instanci.|
|[Zpětné volání – funkce (WRL)](callback-function-wrl.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|
|[CreateActivationFactory – funkce](createactivationfactory-function.md)|Vytvoří objekt pro vytváření, který vytváří instance zadané třídy, které mohou být aktivovány prostředí Windows Runtime.|
|[CreateClassFactory – funkce](createclassfactory-function.md)|Vytvoří objekt pro vytváření, který vytváří instance zadané třídy.|
|[Make – funkce](make-function.md)|Inicializuje určenou třídu prostředí Windows Runtime.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, Implements. h, Internal. h, Module. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](microsoft-wrl-wrappers-namespace.md)
