---
title: '&lt;mutex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <mutex>
dev_langs:
- C++
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2c58f32847084407d19afea8f2946f8b3041efa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861516"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Zahrnují standardní hlavičku \<mutex > k definování tříd `mutex`, `recursive_mutex`, `timed_mutex`, a `recursive_timed_mutex`; šablony `lock_guard` a `unique_lock`; a podpůrné typy a funkce, které definují vzájemné vyloučení kód oblasti.

> [!WARNING]
> Od verze sady Visual Studio 2015, typy synchronizace standardní knihovna C++ jsou založené na Windows synchronizace primitiv a nadále používat ConcRT (kromě případů, kdy cílové platformy systému Windows XP). Typy definované v \<mutex > by se neměla používat s žádné ConcRT typů nebo funkcí.

## <a name="syntax"></a>Syntaxe

```cpp
#include <mutex>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který se zkompiluje pomocí **/CLR**, tuto hlavičku je blokovaný.

Třídy `mutex` a `recursive_mutex` jsou *mutex typy*. Typ mutex má výchozí konstruktor a destruktor, který nevyvolá výjimku výjimky. Tyto objekty mají metody, které poskytují vzájemné vyloučení při pokusu o uzamčení na stejný objekt více vláken. Konkrétně typu mutex obsahuje metody `lock`, `try_lock`, a `unlock`:

- `lock` Metoda blokuje volající vlákno, dokud vlákno získá vlastnictví mutex. Vrácená hodnota se ignoruje.

- `try_lock` Metoda se pokusí získat vlastnictví mutex bez blokování. Její návratový typ je převést na `bool` a je `true` Pokud metoda získá vlastnictví, ale jinak `false`.

- `unlock` Metoda uvolní vlastnictví mutex z volající vlákno.

Mutex typy jako argumenty typu můžete použít k vytvoření instance šablony `lock_guard` a `unique_lock`. Můžete použít objekty tyto typy, jako `Lock` argument Čekání členské funkce v šabloně [condition_variable_any](../standard-library/condition-variable-any-class.md).

A *vypršel časový limit typu mutex* splňuje požadavky pro typ mutex. Kromě toho má `try_lock_for` a `try_lock_until` metod, které musí být možné volat pomocí jeden argument a musí vracet typ, který je převést na `bool`. Typ vypršel mutex můžete definovat tyto funkce pomocí další argumenty, za předpokladu, že tyto další argumenty všechny výchozí hodnoty.

- `try_lock_for` Metoda musí být možné volat pomocí jeden argument, `Rel_time`, jejichž typ je vytváření instancí z [chrono::duration](../standard-library/duration-class.md). Metoda se pokusí získat vlastnictví mutex, ale vrátí v čase, který je určen podle `Rel_time`, bez ohledu na to úspěch. Návratová hodnota převede na `true` Pokud metoda získá vlastnictví; jinak návratovou hodnotu převede na `false`.

- `try_lock_until` Metoda musí být možné volat pomocí jeden argument, `Abs_time`, jejichž typ je vytváření instancí z [chrono::time_point](../standard-library/time-point-class.md). Metoda se pokusí získat vlastnictví mutex, ale ne později než čas, který je určen podle vrátí `Abs_time`, bez ohledu na to úspěch. Návratová hodnota převede na `true` Pokud metoda získá vlastnictví; jinak návratovou hodnotu převede na `false`.

Je také označován jako typ objekt mutex *možno zablokovat typu*. Pokud ho neposkytne – členská funkce `try_lock`, je *základní typ možno zablokovat*. Typ vypršel mutex je také označován jako *vypršel časový limit možno zablokovat typu*.

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[lock_guard – třída](../standard-library/lock-guard-class.md)|Reprezentuje šablonu, která může být vytvořena instance pro vytvoření objektu jejichž destruktor odemkne `mutex`.|
|[mutex – třída (standardní knihovna C++)](../standard-library/mutex-class-stl.md)|Představuje typ mutex. Použití objekty tohoto typu vynutit vzájemné vyloučení v rámci programu.|
|[recursive_mutex – třída](../standard-library/recursive-mutex-class.md)|Představuje typ mutex. V constrast k `mutex` třída, je dobře definovaný chování volání metod uzamčení pro objekty, které jsou již uzamčena.|
|[recursive_timed_mutex – třída](../standard-library/recursive-timed-mutex-class.md)|Představuje typ mutex vypršel. Použití objekty tohoto typu vynutit vzájemné vyloučení, který má časově omezené blokování v rámci programu. Na rozdíl od objekty typu `timed_mutex`, účinek volání uzamčení metod pro `recursive_timed_mutex` objektů je dobře definovaný.|
|[timed_mutex – třída](../standard-library/timed-mutex-class.md)|Představuje typ mutex vypršel. Použití objekty tohoto typu vynutit vzájemné vyloučení, který má časově omezené blokování v rámci programu.|
|[unique_lock – třída](../standard-library/unique-lock-class.md)|Reprezentuje šablonu, která se dá vytvořit instance k vytváření objektů, které spravují zamykání a odemykání `mutex`.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[call_once](../standard-library/mutex-functions.md#call_once)|Poskytuje mechanismus pro volání právě jednou na zadaný objekt s během provádění.|
|[lock](../standard-library/mutex-functions.md#lock)|Pokusí se uzamknout všechny argumenty bez vzájemného zablokování.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[adopt_lock_t – struktura](../standard-library/adopt-lock-t-structure.md)|Představuje typ, který se používá k definování `adopt_lock`.|
|[defer_lock_t – struktura](../standard-library/defer-lock-t-structure.md)|Představuje typ, který definuje `defer_lock` objekt, který slouží k výběru jedné přetížené konstruktory `unique_lock`.|
|[once_flag – struktura](../standard-library/once-flag-structure.md)|Představuje `struct` používané funkce šablony `call_once` zajistit, že inicializace kód je volat pouze jednou, ani za přítomnosti více vláken provádění.|
|[try_to_lock_t – struktura](../standard-library/try-to-lock-t-structure.md)|Představuje `struct` , který definuje `try_to_lock` objektu a slouží k výběru jedné přetížené konstruktory `unique_lock`.|

### <a name="variables"></a>Proměnné

|Název|Popis|
|----------|-----------------|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Představuje objekt, který se dá předat do konstruktory pro `lock_guard` a `unique_lock` k označení, že objekt mutex, který je také se předaný konstruktoru je uzamčen.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Představuje objekt, který lze předat v konstruktoru pro `unique_lock`, k označení, že by neměl konstruktoru zamknout objekt mutex, který je také předávána k němu.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Představuje objekt, který lze předat v konstruktoru pro `unique_lock` k označení, že konstruktoru opakovat odemknutí `mutex` také se předá do něj bez blokování.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
