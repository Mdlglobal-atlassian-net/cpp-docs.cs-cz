---
title: '&lt;budoucí&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <future>
dev_langs:
- C++
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37e5e2ceff83704632a77ef0fb1eedecaa9e678b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ltfuturegt"></a>&lt;Budoucí&gt;

Zahrnují standardní hlavičku \<budoucí > k definování tříd šablon a podpůrné šablony, které zjednodušují spuštění funkce – případně v samostatné vlákna – a načítání její výsledek. Výsledkem je hodnota, kterou vrátí funkce nebo výjimku, která je vysílaných funkce ale není zachycena ve funkci.

Tuto hlavičku použije Concurrency Runtime (ConcRT), takže ho můžete použít společně s jiným mechanismem ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <future>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který se zkompiluje pomocí **/CLR**, tuto hlavičku je blokovaný.

*Asynchronní zprostředkovatele* ukládá výsledek volání funkce. *Asynchronní návratové objekt* se používá k načtení výsledek volání funkce. *Přidružené asynchronní stavu* poskytuje komunikaci mezi poskytovatele asynchronní a jeden nebo více asynchronní návratové objektů.

Program nevytváří přímo všechny objekty přidružené asynchronní stavu. Program vytvoří asynchronní zprostředkovatele, vždy, když ho potřebovat a od vytvoří asynchronní návratové objekt, který sdílí stav asynchronní související s poskytovatelem. Asynchronní zprostředkovatelů a objektů asynchronní návratové spravovat objekty, které mají spojenou s jejich sdílený stav asynchronní. Při poslední objekt, který odkazuje na přidružený stav asynchronní uvolněním, objekt, který obsahuje přidružený stav asynchronní zničena.

Asynchronní zprostředkovatele nebo asynchronní návratové objekt, který nemá žádný související stav asynchronní *prázdný*.

Je k dispozici přidružený stav asynchronní *připraven* jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.

Funkce šablony `async` a třídy šablony `promise` a `packaged_task` asynchronní poskytovatelé. Třídy šablon `future` a `shared_future` popisují asynchronní návratové objekty.

Každý tříd šablon `promise`, `future`, a `shared_future` má specializace pro typ `void` a částečná specializace pro ukládání a načítání hodnotu odkazem. Tyto specializací se liší od primární šablony pouze v podpisy a sémantiku funkce, které ukládají a načítají vrácené hodnoty.

Třídy šablon `future` a `shared_future` nikdy blokovat v jejich destruktory, s výjimkou v jeden případ, který se zachová, i pro zpětnou kompatibilitu: na rozdíl od jiných futures pro `future`– nebo poslední `shared_future`– připojená k úloze Práce s `std::async`destruktor bloky, pokud úloha nebyla dokončena; to znamená, blokuje, pokud tohoto podprocesu ještě nezavolalo `.get()` nebo `.wait()` a je stále spuštěná úloha. Následující poznámka použitelnost byl přidán do popis `std::async` ve verzi standard konceptu: "[Poznámka: Pokud budoucí získané z std::async je přesunut mimo místní rozsah, musí být jiný kód, který používá budoucí vědět, že může blokovat do budoucna – destruktor pro sdílené stavu Připraveno. k – Poznámka end] "ve všech ostatních případech `future` a `shared_future` destruktory jsou povinné a je zaručeno, že nikdy blokovat.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[future – třída](../standard-library/future-class.md)|Popisuje asynchronní návratové objekt.|
|[future_error – třída](../standard-library/future-error-class.md)|Popisuje výjimka objekt, který může být vyvolána metodami typů, které spravují `future` objekty.|
|[packaged_task – třída](../standard-library/packaged-task-class.md)|Popisuje asynchronní zprostředkovatele, který představuje obálku volání a jejíž volání podpis je `Ty(ArgTypes...)`. Jeho přidružený stav asynchronní obsahuje kopii svého s objektu kromě potenciální výsledek.|
|[promise – třída](../standard-library/promise-class.md)|Popisuje asynchronní zprostředkovatele.|
|[shared_future – třída](../standard-library/shared-future-class.md)|Popisuje asynchronní návratové objekt. Rozdíl s `future` objektu asynchronní zprostředkovatele lze přidružit libovolný počet `shared_future` objekty.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[is_error_code_enum – struktura](../standard-library/is-error-code-enum-structure.md)|Specializace, která označuje, že `future_errc` je vhodný pro ukládání `error_code`.|
|[uses_allocator – struktura](../standard-library/uses-allocator-structure.md)|Specializace, který obsahuje vždy hodnotu true.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Představuje asynchronní zprostředkovatele.|
|[future_category –](../standard-library/future-functions.md#future_category)|Vrátí odkaz na `error_category` objekt, který charakterizuje chyby, které jsou přidružené `future` objekty.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Vytvoří `error_code` který má `error_category` objekt, který charakterizuje `future` chyby.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Vytvoří `error_condition` který má `error_category` objekt, který charakterizuje `future` chyby.|
|[Swap](../standard-library/future-functions.md#swap)|Výměny přidružený stav asynchronní jednoho `promise` objekt se stejným jiného.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Poskytuje symbolické názvy chyby, které jsou hlášeny `future_error` třídy.|
|[future_status](../standard-library/future-enums.md#future_status)|Poskytuje symbolické názvy z důvodů, které můžou vrátit funkce vypršel čekání.|
|[Spuštění](../standard-library/future-enums.md#launch)|Představuje typ bitová maska, která popisuje možné režimy pro funkce šablony `async`.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
