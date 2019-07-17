---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: ed98966f651df76078fa47b05f5a2d8ae1b71d05
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244579"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Definuje třídy [condition_variable](../standard-library/condition-variable-class.md) a [condition_variable_any –](../standard-library/condition-variable-any-class.md) , která se používají k vytváření objektů, které čekání na podmínku jako true.

Toto záhlaví používá Concurrency Runtime (ConcRT), takže ho můžete použít společně s další mechanismy ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<condition_variable >

**Namespace:** std

> [!NOTE]
> V kódu, který je zkompilován s použitím **/CLR**, tato hlavička se zablokuje.

### <a name="remarks"></a>Poznámky

Kód, který čeká musíte taky použít podmínku proměnné `mutex`. Volající vlákno musí uzamčení `mutex` před voláním funkce, které počkejte podmínku proměnné. `mutex` Se následně možnosti změnit po návratu volané funkce. `mutex` Není uzamčeno době vlákno čeká podmínku jako true. Tak, že neexistují žádné nepředvídatelné výsledky, každý podproces, který čeká na proměnnou podmínku musíte použít stejné `mutex` objektu.

Objekty typu `condition_variable_any` jde použít s mutex libovolného typu. Typ vzájemně vyloučený přístup, který se používá k poskytování nemá `try_lock` metody. Objekty typu `condition_variable` jde použít jenom s vzájemně vyloučený přístup typu `unique_lock<mutex>`. Objekty tohoto typu může být rychlejší než u objektů typu `condition_variable_any<unique_lock<mutex>>`.

Čekání na událost, nejprve zamknout vyloučený a pak volat jednu z `wait` metody podmínku proměnné. `wait` Volání bloky, dokud signály podmínku proměnné jiného vlákna.

*Detekováno falešné wakeups* dojít, když vláken, která čekají pro podmínku proměnné budou odblokována bez potřeby oznámení. K rozpoznání takových detekováno falešné wakeups, by měl kód, který čeká na podmínku jako true explicitně zkontrolujte tuto podmínku, kód návratu z funkce čekání. To se obvykle provádí pomocí smyčky; můžete použít `wait(unique_lock<mutex>& lock, Predicate pred)` nedokázala tuto smyčku.

```cpp
while (condition is false)
    wait for condition variable;
```

`condition_variable_any` a `condition_variable` třídy každý mají tři metody, které čekání na podmínku.

- `wait` čeká bez vazby časové období.

- `wait_until` počká, dokud zadané `time`.

- `wait_for` čeká zadaný `time interval`.

Každá z těchto metod má dvě přetížené verze. Jeden právě čeká a může probudit falešně. Druhý přebírá argument další šablony, která definuje predikátu. Metoda nevrací dokud predikát je **true**.

Každá třída také obsahuje dvě metody, které se používají pro oznámení proměnnou podmínku, která je jeho stav **true**.

- `notify_one` probudí jedno z vláken, které čeká na proměnnou podmínku.

- `notify_all` probudí všechna vlákna, které čekají na proměnnou podmínku.

## <a name="functions-and-enums"></a>Funkce a výčty

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[condition_variable – třída](../standard-library/condition-variable-class.md)<br/>
[condition_variable_any – třída](../standard-library/condition-variable-any-class.md)<br/>
