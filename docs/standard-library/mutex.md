---
title: '&lt;objekt&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 515318cda2155db81406a5c23cb64e46e79c4e19
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448414"
---
# <a name="ltmutexgt"></a>&lt;objekt&gt;

Pro definování tříd `mutex`, \< `recursive_mutex`, ,`timed_mutex`a ,šablon`lock_guard` a a`unique_lock`podporovaných typů a funkcí, které definují, přidejte > mutex standardní hlavičky. `recursive_timed_mutex` oblasti kódu vzájemného vyloučení.

> [!WARNING]
> Počínaje verzí Visual Studio 2015 jsou C++ standardní typy synchronizace knihovny založené na prostředích synchronizace systému Windows a již nepoužívají ConcRT (s výjimkou případů, kdy je cílová platforma Windows XP). Typy definované v \<> mutex by neměly být použity s žádnými ConcRT typy ani funkcemi.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován pomocí **/CLR**, je tato hlavička zablokována.

Třídy `mutex` a `recursive_mutex` jsou *typy mutex*. Typ mutex má výchozí konstruktor a destruktor, který nevyvolává výjimky. Tyto objekty mají metody, které poskytují vzájemné vyloučení při pokusu o uzamčení stejného objektu více vlákny. Konkrétně typ mutex obsahuje metody `lock`, `try_lock`a `unlock`:

- `lock` Metoda blokuje volající vlákno, dokud vlákno nezíská vlastnictví mutexu. Vrácená hodnota je ignorována.

- `try_lock` Metoda se pokusí získat vlastnictví mutex bez blokování. Jeho návratový typ je převoditelný na **bool** a má **hodnotu true** , pokud metoda získá vlastnictví, ale je v opačném případě **false**.

- `unlock` Metoda uvolní vlastnictví mutexu z volajícího vlákna.

Můžete použít typy mutex jako argumenty typu pro vytvoření instance šablon `lock_guard` a. `unique_lock` Objekty těchto typů lze použít jako `Lock` argument pro čekací členské funkce v šabloně [condition_variable_any](../standard-library/condition-variable-any-class.md).

*Typ* nečasovaného mutexu splňuje požadavky pro typ mutex. Kromě toho obsahuje `try_lock_for` metody a `try_lock_until` , které musí být možné volat pomocí jednoho argumentu a musí vracet typ, který je převoditeln na **bool**. Typ časovaného mutex může definovat tyto funkce pomocí dalších argumentů za předpokladu, že tyto další argumenty mají výchozí hodnoty.

- Metoda musí být volat pomocí jednoho argumentu, `Rel_time`jehož typ je instance [chrono::d uration](../standard-library/duration-class.md). `try_lock_for` Metoda se pokusí získat vlastnictví mutex, ale vrátí se v čase, který je určen pomocí `Rel_time`, bez ohledu na úspěch. Návratová hodnota se převede na **true** , pokud metoda získá vlastnictví. v opačném případě se návratová hodnota převede na **false**.

- Metoda musí být volat pomocí jednoho argumentu, `Abs_time`jehož typ je instance [chrono:: time_point](../standard-library/time-point-class.md). `try_lock_until` Metoda se pokusí získat vlastnictví mutexu, ale nevrátí hodnotu pozdější než čas, který je určen pomocí `Abs_time`, bez ohledu na úspěch. Návratová hodnota se převede na **true** , pokud metoda získá vlastnictví. v opačném případě se návratová hodnota převede na **false**.

Typ mutex je také označován jako *typ uzamykatelné*. Pokud neposkytuje členskou funkci `try_lock`, jedná se o *základní typ uzamykatelné*. Časový limit typu mutex je známý taky jako *typ časovaného*povýšení.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[lock_guard – třída](../standard-library/lock-guard-class.md)|Představuje šablonu, která může být vytvořena pro vytvoření objektu, jehož destruktor odemkne `mutex`.|
|[mutex – třída (standardní knihovna C++)](../standard-library/mutex-class-stl.md)|Představuje typ mutex. Pomocí objektů tohoto typu vynutili vzájemné vyloučení v rámci programu.|
|[recursive_mutex – třída](../standard-library/recursive-mutex-class.md)|Představuje typ mutex. V constrast ke `mutex` třídě je chování při volání metod zamykání pro objekty, které jsou již uzamčeny, správně definovány.|
|[recursive_timed_mutex – třída](../standard-library/recursive-timed-mutex-class.md)|Představuje typ nečasovaného mutexu. Pomocí objektů tohoto typu vynutili vzájemné vyloučení, které v rámci programu obsahuje časově omezené blokování. Na rozdíl od objektů typu `timed_mutex`je efekt volání metod zamykání pro `recursive_timed_mutex` objekty dobře definován.|
|[scoped_lock – třída](../standard-library/scoped-lock-class.md)||
|[timed_mutex – třída](../standard-library/timed-mutex-class.md)|Představuje typ nečasovaného mutexu. Pomocí objektů tohoto typu vynutili vzájemné vyloučení, které v rámci programu obsahuje časově omezené blokování.|
|[unique_lock – třída](../standard-library/unique-lock-class.md)|Představuje šablonu, která může být vytvořena pro vytváření objektů, které spravují uzamykání a odemykání `mutex`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|Poskytuje mechanismus pro volání zadaného volajícího objektu přesně jednou při spuštění.|
|[lock](../standard-library/mutex-functions.md#lock)|Pokusí se zamknout všechny argumenty bez zablokování.|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>Struktury

|||
|-|-|
|[adopt_lock_t – struktura](../standard-library/adopt-lock-t-structure.md)|Představuje typ, který se používá k definování `adopt_lock`.|
|[defer_lock_t – struktura](../standard-library/defer-lock-t-structure.md)|Představuje typ, který definuje `defer_lock` objekt, který se používá k výběru jednoho z přetížených konstruktorů. `unique_lock`|
|[once_flag – struktura](../standard-library/once-flag-structure.md)|Představuje **strukturu** , která se používá se šablonou funkce `call_once` , aby se zajistilo, že inicializační kód se volá jenom jednou, a to i v případě, že je k disčase více vláken provádění.|
|[try_to_lock_t – struktura](../standard-library/try-to-lock-t-structure.md)|Představuje **strukturu** , která definuje `try_to_lock` objekt a slouží k výběru jednoho z přetížených konstruktorů. `unique_lock`|

### <a name="variables"></a>Proměnné

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Představuje objekt, který lze předat konstruktorům pro `lock_guard` a `unique_lock` označit, že objekt mutex, který je také předán konstruktoru, je uzamčen.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Představuje objekt, který lze předat konstruktoru pro `unique_lock`, aby označoval, že konstruktor by neměl uzamknout objekt mutex, který je také předáván do něj.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Představuje objekt, který lze předat konstruktoru pro `unique_lock` , aby označoval, že by se měl konstruktor pokusit `mutex` odemknout, který je také předán bez blokování.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
