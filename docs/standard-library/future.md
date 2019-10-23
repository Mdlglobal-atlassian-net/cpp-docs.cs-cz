---
title: '&lt;future &gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: c852b3040a94035f6a84b1f717c3583fababbb2c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688023"
---
# <a name="ltfuturegt"></a>&lt;future &gt;

Zahrňte standardní hlavičku \<future > k definování šablon tříd a podpoře šablon, které zjednodušují spuštění funkce – pravděpodobně v samostatném vlákně – a načtou svůj výsledek. Výsledkem je hodnota, která je vrácena funkcí nebo výjimkou, která je vygenerována funkcí, ale není zachycena ve funkci.

Tato hlavička používá Concurrency Runtime (ConcRT), takže ji můžete použít spolu s dalšími mechanismy ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <future>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován pomocí **/CLR**, je tato hlavička zablokována.

*Asynchronní zprostředkovatel* ukládá výsledek volání funkce. *Asynchronní návratový objekt* se používá k načtení výsledku volání funkce. *Přidružený asynchronní stav* zajišťuje komunikaci mezi asynchronním zprostředkovatelem a jedním nebo více asynchronními návratový objekty.

Program přímo nevytváří žádné přidružené objekty asynchronního stavu. Program vytvoří asynchronního zprostředkovatele vždy, když potřebuje jeden a z nich, vytvoří asynchronní návratový objekt, který sdílí přidružený asynchronní stav se zprostředkovatelem. Asynchronní zprostředkovatelé a asynchronní návratové objekty spravují objekty, které obsahují svůj sdílený přidružený asynchronní stav. Když poslední objekt, který odkazuje na přidružený asynchronní stav, je zničen objekt, který obsahuje přidružený asynchronní stav.

Asynchronní zprostředkovatel nebo asynchronní návratový objekt, který nemá přidružený asynchronní stav, je *prázdný*.

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

Funkce šablony `async` a šablony tříd `promise` a `packaged_task` jsou asynchronní zprostředkovatelé. Šablony tříd `future` a `shared_future` popisují asynchronní návratové objekty.

Každá ze šablon třídy `promise`, `future` a `shared_future` má specializaci typu **void** a částečnou specializaci pro ukládání a načítání hodnoty odkazem. Tyto specializace se liší od primární šablony pouze v signaturách a sémantikě funkcí, které ukládají a načítají vrácenou hodnotu.

Šablony tříd `future` a `shared_future` nikdy neblokují ve svých destruktorech, s výjimkou jednoho případu, který se zachovává kvůli zpětné kompatibilitě: na rozdíl od všech ostatních futures, pro `future`, nebo jako poslední `shared_future` – to je připojeno k úloze spuštěnou s `std::async` , destruktor zablokuje, pokud se úloha nedokončila; To znamená, že se zablokuje, pokud toto vlákno ještě nevolalo `.get()` nebo `.wait()` a úloha stále běží. Do popisu `std::async` v konceptu Standard byla přidána následující Poznámka k použitelnosti: "[Poznámka: Pokud je budoucí získaná z std:: Async přesunuta mimo místní rozsah, jiný kód, který používá budoucnost, musí vědět, že destruktor Future může být blokován pro sdílený stav, který je připravený. – koncová Poznámka] "ve všech ostatních případech jsou vyžadovány destruktory `future` a `shared_future` a je zaručeno, že nikdy neblokovat.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Name|Popis|
|----------|-----------------|
|[future – třída](../standard-library/future-class.md)|Popisuje asynchronní návratový objekt.|
|[future_error – třída](../standard-library/future-error-class.md)|Popisuje objekt výjimky, který může být vyvolán metodami typů, které spravují objekty `future`.|
|[packaged_task – třída](../standard-library/packaged-task-class.md)|Popisuje asynchronního zprostředkovatele, který je obálkou volání a jehož signatura volání je `Ty(ArgTypes...)`. Jeho přidružený asynchronní stav obsahuje kopii jeho volatelné objektu kromě potenciálního výsledku.|
|[promise – třída](../standard-library/promise-class.md)|Popisuje asynchronního zprostředkovatele.|
|[shared_future – třída](../standard-library/shared-future-class.md)|Popisuje asynchronní návratový objekt. Na rozdíl od `future` objektu může být asynchronní zprostředkovatel spojen s libovolným počtem objektů `shared_future`.|

### <a name="structures"></a>Struktury

|Name|Popis|
|----------|-----------------|
|[is_error_code_enum – struktura](../standard-library/is-error-code-enum-structure.md)|Specializace, která indikuje, že `future_errc` je vhodná pro ukládání `error_code`.|
|[uses_allocator – struktura](../standard-library/uses-allocator-structure.md)|Specializace, která vždycky drží hodnotu true.|

### <a name="functions"></a>Funkce

|Name|Popis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Představuje asynchronního zprostředkovatele.|
|[future_category](../standard-library/future-functions.md#future_category)|Vrátí odkaz na objekt `error_category`, který charakterizuje chyby spojené s objekty `future`.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Vytvoří `error_code`, který má objekt `error_category`, který charakterizuje `future` chyby.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Vytvoří `error_condition`, který má objekt `error_category`, který charakterizuje `future` chyby.|
|[adresu](../standard-library/future-functions.md#swap)|Vyměňuje přidružený asynchronní stav jednoho `promise` objektu jiným objektem.|

### <a name="enumerations"></a>Výčty

|Name|Popis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Poskytuje symbolické názvy pro chyby, které jsou hlášeny `future_error` třídy.|
|[future_status](../standard-library/future-enums.md#future_status)|Poskytuje symbolické názvy pro důvody, které může funkce časovaného čekání vrátit.|
|[předběžné](../standard-library/future-enums.md#launch)|Představuje typ maskování, který popisuje možné režimy pro funkci šablony `async`.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
