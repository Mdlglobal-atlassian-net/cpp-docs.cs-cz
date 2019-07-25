---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: e63dc5a494f471997c28be8b2cd237aba45a6fd6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457387"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Definuje třídy [condition_variable](../standard-library/condition-variable-class.md) a [condition_variable_any](../standard-library/condition-variable-any-class.md) , které se používají k vytváření objektů, které čekají na hodnotu true podmínky.

Tato hlavička používá Concurrency Runtime (ConcRT), takže ji můžete použít spolu s dalšími mechanismy ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<condition_variable >

**Obor názvů:** std

> [!NOTE]
> V kódu, který je zkompilován pomocí **/CLR**, je tato hlavička zablokována.

### <a name="remarks"></a>Poznámky

Kód, který čeká na proměnnou podmínky `mutex`, musí také použít. Volající vlákno musí uzamknout `mutex` před voláním funkce, které čekají na proměnnou podmínky. Po návratu volané funkce jepakuzamčena.`mutex` Není `mutex` uzamčen, dokud vlákno počká, než se podmínka stane true. Aby nedocházelo k nepředvídatelným výsledkům, každé vlákno, které čeká na proměnnou podmínky, musí používat stejný `mutex` objekt.

Objekty typu `condition_variable_any` lze použít s objektem mutex libovolného typu. Typ mutex, který je použit, nemusí poskytovat `try_lock` metodu. Objekty typu `condition_variable` lze použít pouze s objektem mutex typu `unique_lock<mutex>`. Objekty tohoto typu mohou být rychlejší než objekty typu `condition_variable_any<unique_lock<mutex>>`.

Chcete-li počkat na událost, nejprve uzamkněte mutex a potom zavolejte jednu z `wait` metod pro proměnnou podmínky. Bloky `wait` volání, dokud jiné vlákno nesignalizuje proměnnou podmínky.

K *Spurious probuzení* dojde, když se vlákna, která čekají na proměnné podmínky, odblokují bez příslušných oznámení. Aby bylo možné takové probuzení spurious rozpoznat, kód, který čeká na hodnotu true, by měl explicitně kontrolovat podmínku, když se kód vrátí z funkce Wait. To se obvykle provádí pomocí smyčky. můžete použít `wait(unique_lock<mutex>& lock, Predicate pred)` k provedení této smyčky za vás.

```cpp
while (condition is false)
    wait for condition variable;
```

Třídy `condition_variable_any` a`condition_variable` mají tři metody, které čekají na určitou podmínku.

- `wait`čeká na neohraničené časové období.

- `wait_until`čeká na zadání `time`.

- `wait_for`čeká na zadanou `time interval`hodnotu.

Každá z těchto metod má dvě přetížené verze. Stačí pouze počkat a může probudit falešně. Druhý použije další argument šablony, který definuje predikát. Metoda nevrátí hodnotu, dokud predikát nebude **pravda**.

Každá třída má také dvě metody, které slouží k oznamování proměnné podmínky, že její podmínka je **pravdivá**.

- `notify_one`probudí jedno z vláken, která čekají na proměnnou podmínky.

- `notify_all`probudí všechna vlákna, která čekají na proměnnou podmínky.

## <a name="functions-and-enums"></a>Funkce a výčty

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[condition_variable – třída](../standard-library/condition-variable-class.md)\
[condition_variable_any – třída](../standard-library/condition-variable-any-class.md)
