---
title: '&lt;pozdější&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: d33b67ed17a95b6717878aaca2f61682b1807c15
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454008"
---
# <a name="ltfuturegt"></a>&lt;pozdější&gt;

Zahrňte standardní hlavičku \<Standard > k definování tříd šablony a podpůrným šablonám, které zjednodušují spuštění funkce – pravděpodobně v samostatném vlákně – a načtou svůj výsledek. Výsledkem je hodnota, která je vrácena funkcí nebo výjimkou, která je vygenerována funkcí, ale není zachycena ve funkci.

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

Funkce `async` šablony a třídy `promise` šablony a `packaged_task` jsou asynchronní zprostředkovatelé. Třídy `future` šablony a `shared_future` popisují asynchronní návratové objekty.

Každá z tříd `promise`šablony, `future`a `shared_future` má specializace pro typ **void** a částečnou specializaci pro ukládání a načítání hodnoty odkazem. Tyto specializace se liší od primární šablony pouze v signaturách a sémantikě funkcí, které ukládají a načítají vrácenou hodnotu.

Třídy `future` šablony a `shared_future` nikdy nejsou zablokované ve svých destruktorech, s výjimkou jednoho případu, který se zachovává kvůli zpětné kompatibilitě: Na rozdíl od všech ostatních futures, `future`pro – nebo poslední `shared_future`– připojené k úloze, která byla spuštěna s `std::async`, destruktor zablokuje, jestli se úloha nedokončila. to znamená, že se zablokuje, pokud `.get()` toto vlákno ještě nevolalo nebo `.wait()`a úloha stále běží. Do popisu `std::async` v konceptu Standard byla přidána následující Poznámka k použitelnosti: "[Poznámka: Pokud je budoucí získaná z std:: Async přesunuta mimo místní rozsah, další kód, který používá budoucnost, musí mít na paměti, že destruktor budoucího stavu může zablokovat, aby se sdílený stav stal připravený. – koncová Poznámka] `future` ve `shared_future` všech ostatních případech a destruktory jsou povinné a zaručují, že nikdy neblokuje.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Name|Popis|
|----------|-----------------|
|[future – třída](../standard-library/future-class.md)|Popisuje asynchronní návratový objekt.|
|[future_error – třída](../standard-library/future-error-class.md)|Popisuje objekt výjimky, který může být vyvolán metodami typů, které `future` spravují objekty.|
|[packaged_task – třída](../standard-library/packaged-task-class.md)|Popisuje asynchronního zprostředkovatele, který je obálkou volání a jehož signatura `Ty(ArgTypes...)`volání je. Jeho přidružený asynchronní stav obsahuje kopii jeho volatelné objektu kromě potenciálního výsledku.|
|[promise – třída](../standard-library/promise-class.md)|Popisuje asynchronního zprostředkovatele.|
|[shared_future – třída](../standard-library/shared-future-class.md)|Popisuje asynchronní návratový objekt. Na rozdíl `future` od objektu může být asynchronní zprostředkovatel spojen s libovolným `shared_future` počtem objektů.|

### <a name="structures"></a>Struktury

|Name|Popis|
|----------|-----------------|
|[is_error_code_enum – struktura](../standard-library/is-error-code-enum-structure.md)|Specializace, která `future_errc` označuje, že je vhodná `error_code`pro ukládání.|
|[uses_allocator – struktura](../standard-library/uses-allocator-structure.md)|Specializace, která vždycky drží hodnotu true.|

### <a name="functions"></a>Funkce

|Name|Popis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Představuje asynchronního zprostředkovatele.|
|[future_category](../standard-library/future-functions.md#future_category)|Vrátí odkaz na `error_category` objekt, který charakterizuje chyby spojené s `future` objekty.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Vytvoří objekt, který má objekt, který charakterizuje `future` chyby. `error_code` `error_category`|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Vytvoří objekt, který má objekt, který charakterizuje `future` chyby. `error_condition` `error_category`|
|[swap](../standard-library/future-functions.md#swap)|Vyměňuje přidružený asynchronní stav jednoho `promise` objektu s jiným objektem.|

### <a name="enumerations"></a>Výčty

|Name|Popis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Poskytuje symbolické názvy pro chyby, které jsou hlášeny `future_error` třídou.|
|[future_status](../standard-library/future-enums.md#future_status)|Poskytuje symbolické názvy pro důvody, které může funkce časovaného čekání vrátit.|
|[předběžné](../standard-library/future-enums.md#launch)|Představuje typ maskování, který popisuje možné režimy pro funkci `async`šablony.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
