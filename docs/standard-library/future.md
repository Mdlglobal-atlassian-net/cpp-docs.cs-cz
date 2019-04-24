---
title: '&lt;budoucí&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: 189a9f16b65ae74fc2a86bee62bf8bd548c486aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159857"
---
# <a name="ltfuturegt"></a>&lt;budoucí&gt;

Zahrnout standardní hlavička \<budoucí > k definování tříd šablon a podpůrných šablon, které zjednodušují spuštění funkce – pravděpodobně v samostatném vlákně – a načítání jeho výsledek. Výsledkem je hodnota vrácená funkcí nebo výjimku, která je vygenerován pomocí funkce ale není zachycena ve funkci.

Toto záhlaví používá Concurrency Runtime (ConcRT), takže ho můžete použít společně s další mechanismy ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <future>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován s použitím **/CLR**, tato hlavička se zablokuje.

*Asynchronního poskytovatele* ukládá výsledek volání funkce. *Asynchronní vrácený objekt* slouží k načtení výsledku volání funkce. *Přidružený asynchronní stav* zajišťuje komunikaci mezi asynchronního poskytovatele a jeden nebo více asynchronních návratových objektů.

Program přímo nevytváří žádné objekty přidružený asynchronní stav. Program vytvoří asynchronního poskytovatele pokaždé, když je potřeba a z té vytvoří asynchronní vrácený objekt, který sdílí přidružený asynchronní stav s tímto poskytovatelem. Asynchronní poskytovatelů a asynchronních návratových objektů spravovat objekty, které obsahují, že jejich sdílené přidružený asynchronní stav. Když ho uvolní poslední objekt, který odkazuje na přidružený asynchronní stav, je objekt, který obsahuje přidružený asynchronní stav zničen.

Asynchronního poskytovatele nebo asynchronní vrácený objekt, který nemá žádný přidružený asynchronní stav je *prázdný*.

Je přidružený asynchronní stav *připravené* pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

Funkce šablony `async` a tříd šablon `promise` a `packaged_task` asynchronní poskytovatelé. Třídy šablon `future` a `shared_future` popisují asynchronních návratových objektů.

Každý z tříd šablon `promise`, `future`, a `shared_future` má specializaci pro typ **void** a částečnou specializaci pro ukládání a načítání hodnoty podle odkazu. Tyto specializace se liší od primární šablony pouze v podpisy a sémantika funkcí, které ukládají a načítají vrácené hodnoty.

Třídy šablon `future` a `shared_future` není nikdy blokována v jejich destruktory, s výjimkou v jednom případě, že je zachována z důvodu zpětné kompatibility: Na rozdíl od jiných termínu pro `future`– nebo poslední `shared_future`–, který je připojen k úloze spuštěné pomocí `std::async`je destruktor blokován, pokud úkol nebyl dokončen, tedy blokuje, pokud toto vlákno dosud nevolalo `.get()` nebo `.wait()`a je stále spuštěn úkol. Byla přidána následující poznámka použitelnost pro popis `std::async` koncept standardu: "[Poznámka: Pokud budoucí získané z std::async je přesunut mimo místní rozsah, jiný kód, který se používá v budoucnosti musí mějte na paměti, že do budoucna destruktor může blokovat sdíleného stavu Připraveno. k – poslední poznámku] "ve všech ostatních případech `future` a `shared_future` Destruktory jsou vyžadovány a zaručeně není nikdy blokována.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[future – třída](../standard-library/future-class.md)|Popisuje asynchronous vrácený objekt.|
|[future_error – třída](../standard-library/future-error-class.md)|Popisuje objekt výjimky, které mohou být vyvolány pomocí jiných metod typů, které spravují `future` objekty.|
|[packaged_task – třída](../standard-library/packaged-task-class.md)|Popisuje asynchronous zprostředkovatele, který je obálka volání a jehož signatura volání je `Ty(ArgTypes...)`. Přidružený asynchronní stav obsahuje kopii jeho volatelný objekt kromě potenciální výsledek.|
|[promise – třída](../standard-library/promise-class.md)|Popisuje asynchronous zprostředkovatele.|
|[shared_future – třída](../standard-library/shared-future-class.md)|Popisuje asynchronous vrácený objekt. Rozdíl od se `future` objektu, lze přidružit libovolný počet asynchronního poskytovatele `shared_future` objekty.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[is_error_code_enum – struktura](../standard-library/is-error-code-enum-structure.md)|Specializace, která označuje, že `future_errc` je vhodná pro ukládání `error_code`.|
|[uses_allocator – struktura](../standard-library/uses-allocator-structure.md)|Platí to vždy specializace.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Představuje asynchronní zprostředkovatele.|
|[future_category –](../standard-library/future-functions.md#future_category)|Vrátí odkaz na `error_category` objekt, který charakterizuje chyby, které jsou přidružené k `future` objekty.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Vytvoří `error_code` , který má `error_category` objekt, který charakterizuje `future` chyby.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Vytvoří `error_condition` , který má `error_category` objekt, který charakterizuje `future` chyby.|
|[swap](../standard-library/future-functions.md#swap)|Vymění přidružený asynchronní stav jednoho `promise` objektu z jiného.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Poskytuje symbolické názvy pro chyby, které jsou hlášeny sadou `future_error` třídy.|
|[future_status](../standard-library/future-enums.md#future_status)|Poskytuje symbolické názvy pro důvody, které můžou vrátit funkce vypršel časový limit čekání.|
|[spuštění](../standard-library/future-enums.md#launch)|Představuje typ bitová maska, která popisuje možné režimy pro šablonu funkce `async`.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
