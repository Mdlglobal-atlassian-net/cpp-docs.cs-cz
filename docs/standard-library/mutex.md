---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 4655278e312647f4e69cf48cb772df854260ce57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224074"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Zahrnout standardní hlavička \<vzájemně vyloučený přístup > k definování třídy `mutex`, `recursive_mutex`, `timed_mutex`, a `recursive_timed_mutex`; šablony `lock_guard` a `unique_lock`; a podporuje typy a funkce, které definují oblasti vyloučeného kódu.

> [!WARNING]
> Synchronizace typy standardní knihovny C++ od v sadě Visual Studio 2015, jsou založené na Windows synchronizací primitiv a již nebudete používat ConcRT (s výjimkou případu, kdy Cílová platforma Windows XP). Typy definované v \<vzájemně vyloučený přístup > se nemá používat s všechny typy ConcRT nebo funkce.

## <a name="syntax"></a>Syntaxe

```cpp
#include <mutex>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován s použitím **/CLR**, tato hlavička se zablokuje.

Třídy `mutex` a `recursive_mutex` jsou *mutex typy*. Typ mutex má výchozí konstruktor a destruktor, který nevrací výjimky. Tyto objekty mají metody, které poskytují vzájemné vyloučení při více vláken pokusí Uzamknout na stejný objekt. Konkrétně typ mutex obsahuje metody `lock`, `try_lock`, a `unlock`:

- `lock` Metoda blokuje volající vlákno, dokud vlákno nezíská vlastnictví objektu mutex. Vrácená hodnota je ignorována.

- `try_lock` Metoda se pokusí získat vlastnictví objektu mutex bez blokování. Její typ vrácené hodnoty je převést na **bool** a je **true** Pokud metoda získává vlastnictví, ale jinak **false**.

- `unlock` Metoda uvolní vlastnictví objektu mutex z volajícího vlákna.

Mutex – typy jako argumenty typu můžete použít k vytvoření instance šablony `lock_guard` a `unique_lock`. Můžete použít objekty těchto typů, jako `Lock` argument pro členské funkce čekání v šabloně [condition_variable_any –](../standard-library/condition-variable-any-class.md).

A *vypršel časový limit typ mutex* splňuje požadavky pro typ mutex. Kromě toho má `try_lock_for` a `try_lock_until` metody, které musí být možné volat pomocí jeden argument a musí vrátit typ, který lze převést na **bool**. Vypršel časový limit vzájemně vyloučený přístup typu můžete definovat tyto funkce pomocí další argumenty za předpokladu, že tyto další všechny argumenty mají výchozí hodnoty.

- `try_lock_for` Metoda musí být možné volat pomocí jednoho argumentu `Rel_time`, jehož typ je instance [chrono::duration](../standard-library/duration-class.md). Metoda se pokusí získat vlastnictví objektu mutex, ale vrátí v čase, které je určeno `Rel_time`, bez ohledu na úspěch. Návratová hodnota převede na **true** Pokud metoda získává vlastnictví; v opačném případě návratovou hodnotu převede **false**.

- `try_lock_until` Metoda musí být možné volat pomocí jednoho argumentu `Abs_time`, jehož typ je instance [chrono::time_point](../standard-library/time-point-class.md). Metoda se pokusí získat vlastnictví objektu mutex, ale vrátí pozdější než čas, který je stanovena podle prvku `Abs_time`, bez ohledu na úspěch. Návratová hodnota převede na **true** Pokud metoda získává vlastnictví; v opačném případě návratovou hodnotu převede **false**.

Typ mutex je také označován jako *možno zablokovat typ*. Pokud ho neposkytne členskou funkci `try_lock`, je *základní typ možno zablokovat*. Vypršel časový limit vzájemně vyloučený přístup typu se taky říká *vypršel časový limit možno zablokovat typ*.

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[lock_guard – třída](../standard-library/lock-guard-class.md)|Reprezentuje šablonu, která se dá vytvořit instance pro vytvoření objektu, jehož destruktor odemkne `mutex`.|
|[mutex – třída (standardní knihovna C++)](../standard-library/mutex-class-stl.md)|Představuje typ mutex. Použití objektů tohoto typu k zajištění vzájemného vyloučení v rámci programu.|
|[recursive_mutex – třída](../standard-library/recursive-mutex-class.md)|Představuje typ mutex. V constrast k `mutex` třídy, volání metod zamykání pro objekty, které již jsou zamčeny chování je dobře definovaný.|
|[recursive_timed_mutex – třída](../standard-library/recursive-timed-mutex-class.md)|Představuje typ mutex vypršel časový limit. Použití objektů tohoto typu k zajištění vzájemného vyloučení, který má časově omezenou blokování v rámci programu. Na rozdíl od objektů typu `timed_mutex`, efekt volání pro uzamčení metod `recursive_timed_mutex` objekty je dobře definovaný.|
|[timed_mutex – třída](../standard-library/timed-mutex-class.md)|Představuje typ mutex vypršel časový limit. Použití objektů tohoto typu k zajištění vzájemného vyloučení, který má časově omezenou blokování v rámci programu.|
|[unique_lock – třída](../standard-library/unique-lock-class.md)|Reprezentuje šablonu, která se dá vytvořit instance vytvořit objekty, které spravují zamykání a odemykání `mutex`.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[call_once](../standard-library/mutex-functions.md#call_once)|Poskytuje mechanismus pro volání zadané volatelný objekt právě jednou během provádění.|
|[lock](../standard-library/mutex-functions.md#lock)|Se pokusí uzamknout všechny argumenty bez zablokování.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[adopt_lock_t – struktura](../standard-library/adopt-lock-t-structure.md)|Představuje typ, který se používá k definování `adopt_lock`.|
|[defer_lock_t – struktura](../standard-library/defer-lock-t-structure.md)|Představuje typ, který definuje `defer_lock` objekt, který se používá k vyberte jednu z přetížených konstruktorů z `unique_lock`.|
|[once_flag – struktura](../standard-library/once-flag-structure.md)|Představuje **struktura** , který se používá funkce šablony `call_once` zajistit, že inicializace kód je volán pouze jednou, i v případě výskytu více vláken provádění.|
|[try_to_lock_t – struktura](../standard-library/try-to-lock-t-structure.md)|Představuje **struktura** , který definuje `try_to_lock` objektu a umožňuje vybrat jednu z přetížených konstruktorů z `unique_lock`.|

### <a name="variables"></a>Proměnné

|Název|Popis|
|----------|-----------------|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Představuje objekt, který může být předán konstruktory pro `lock_guard` a `unique_lock` k označení, že objekt mutex také předávaný do konstruktoru je uzamčen.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Představuje objekt, který může být předán konstruktoru pro `unique_lock`, pro indikaci, že by neměl konstruktor zamknout objekt mutex také předávaný do něj.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Představuje objekt, který může být předán konstruktoru pro `unique_lock` k označení, že by měl konstruktoru pokusu o odemknutí `mutex` , který je také funkci ji bez blokování.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
