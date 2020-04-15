---
title: '&lt;budoucí&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.openlocfilehash: 16c26212cac13602e981f42d8333518da90615fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370667"
---
# <a name="ltfuturegt-functions"></a>&lt;budoucí&gt; funkce

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[Swap](#swap)|

## <a name="async"></a><a name="async"></a>Asynchronní

Představuje *asynchronního zprostředkovatele*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parametry

*Zásad*\
Hodnota [startu.](../standard-library/future-enums.md#launch)

### <a name="remarks"></a>Poznámky

Definice zkratek:

|||
|-|-|
|*dfn*|Výsledek volání funkce `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Výsledky volání funkce `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty (Ty)*|Typ `result_of<Fn(ArgTypes...)>::type`.|

První šablona funkce vrátí funkci `async(launch::any, fn, args...)`.

Druhá funkce vrátí `future<Ty>` objekt, jehož *přidružený asynchronní stav* obsahuje výsledek spolu s hodnotami *dfn* a *dargs* a objektem vlákna pro správu samostatného vlákna provádění.

Není-li typ `decay<Fn>::type` jiný typ než spuštění, nebude se druhá funkce účastnit rozlišení přetížení.

Standard Jazyka C++ uvádí, že pokud je zásada spuštěna::asynchronně, funkce vytvoří nové vlákno. Implementace společnosti Microsoft je však v současné době nevyhovující. Získává svá vlákna z fondu Windows ThreadPool, který v některých případech může poskytnout recyklované vlákno spíše než nové. To znamená, `launch::async` že zásada `launch::async|launch::deferred`je skutečně implementována jako .  Dalším důsledkem implementace založené na ThreadPool je, že neexistuje žádná záruka, že místní proměnné podprocesu budou zničeny po dokončení vlákna. Pokud je vlákno recyklováno a poskytnuto novému volání `async`, staré proměnné budou stále existovat. Proto doporučujeme nepoužívat proměnné místní vlákno `async`s .

Pokud je `launch::deferred` *zásada* , funkce označí přidružený asynchronní stav jako podržení *odložené funkce* a vrátí. První volání jakékoli nečasové funkce, která čeká, až bude související asynchronní stav připraven, v důsledku volá odloženou funkci pomocí vyhodnocení funkce `INVOKE(dfn, dargs..., Ty)`.

Ve všech případech přidružené asynchronní stav `future` objektu není nastavena na `INVOKE(dfn, dargs..., Ty)` *připraven,* dokud vyhodnocení dokončí, buď vyvolání výjimku nebo vrácení moru normálně. Výsledek přidruženého asynchronního stavu je výjimka, pokud byla nějaká vyvolána, nebo libovolná hodnota, která je vrácena vyhodnocením.

> [!NOTE]
> Pro `future`– nebo poslední [shared_future](../standard-library/shared-future-class.md)–, která je připojena k úkolu zahájeného pomocí `std::async`, destruktor zablokuje, pokud úkol nebyl dokončen; to znamená, že blokuje, pokud `.get()` toto vlákno ještě nevolalo nebo `.wait()` a úloha je stále spuštěna. Pokud je objekt `future` získaný z volání funkce `std::async` přesunut mimo místní rozsah, jiný kód, který jej používá, musí vědět, že jeho destruktor může být blokován, než sdílený stav změní na stav připraven.

Pseudofunkce `INVOKE` je definována [ \<ve funkční>](../standard-library/functional.md).

## <a name="future_category"></a><a name="future_category"></a>future_category

Vrátí odkaz na [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje `future` chyby, které jsou přidruženy k objektům.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

Vytvoří [error_code](../standard-library/error-code-class.md) spolu s [error_category](../standard-library/error-category-class.md) objektem, který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Hodnota [future_errc,](../standard-library/future-enums.md#future_errc) která identifikuje hlášenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

Vytvoří [error_condition](../standard-library/error-condition-class.md) spolu s [error_category](../standard-library/error-category-class.md) objektem, který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Hodnota [future_errc,](../standard-library/future-enums.md#future_errc) která identifikuje hlášenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a><a name="swap"></a>Swap

Vyměňuje *přidružený asynchronní* stav `promise` jednoho objektu s jiným.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `promise` objekt.

*Právo*\
Správný `promise` objekt.

## <a name="see-also"></a>Viz také

[\<budoucí>](../standard-library/future.md)
