---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: 3ce9125a13f0dd2f2e4f98a217c4373f2be2f8a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663944"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Definuje třídy [condition_variable](../standard-library/condition-variable-class.md) a [condition_variable_any –](../standard-library/condition-variable-any-class.md) , která se používají k vytváření objektů, které čekání na podmínku jako true.

Toto záhlaví používá Concurrency Runtime (ConcRT), takže ho můžete použít společně s další mechanismy ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <condition_variable>
```

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

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[condition_variable – třída](../standard-library/condition-variable-class.md)<br/>
[condition_variable_any – třída](../standard-library/condition-variable-any-class.md)<br/>
