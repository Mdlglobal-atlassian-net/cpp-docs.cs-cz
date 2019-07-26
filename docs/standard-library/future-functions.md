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
ms.openlocfilehash: 5435c3b9e10f151fc77c72b58c93510b6a867ce1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447330"
---
# <a name="ltfuturegt-functions"></a>&lt;budoucí&gt; funkce

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a>Async

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

*politických*\
Hodnota [spuštění](../standard-library/future-enums.md#launch) .

### <a name="remarks"></a>Poznámky

Definice zkratek:

|||
|-|-|
|*dfn*|Výsledek volání funkce `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Výsledky volání funkce `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Typ `result_of<Fn(ArgTypes...)>::type`.|

První šablona funkce vrátí funkci `async(launch::any, fn, args...)`.

`future<Ty>` Druhá funkce vrátí objekt, jehož *přidružený asynchronní stav* obsahuje výsledek společně s hodnotami *DFN* a *dargs* a objekt vlákna ke správě samostatného vlákna provádění.

Není-li typ `decay<Fn>::type` jiný typ než spuštění, nebude se druhá funkce účastnit rozlišení přetížení.

Standardní C++ stavy, které jsou spuštěny v případě, že je spuštěna zásada:: Async, funkce vytvoří nové vlákno. Implementace Microsoftu ale v tuto chvíli nevyhovuje. Získává svá vlákna z fondu vláken systému Windows, což v některých případech může poskytnout recyklovaný podproces místo nového. To znamená, že `launch::async` zásada je skutečně implementována `launch::async|launch::deferred`jako.  Dalším odvozením implementace založeného na podprocesu je, že není nijak zaručeno, že místní proměnné vlákna budou zničeny po dokončení vlákna. Pokud se vlákno recykluje a poskytne novému volání `async`, staré proměnné budou pořád existovat. Proto doporučujeme, abyste místní proměnné vlákna nepoužívali s `async`.

Pokud  je `launch::deferred`zásada, funkce označí svůj přidružený asynchronní stav jako drží odloženou *funkci* a vrátí. První volání jakékoli nečasové funkce, která čeká, až bude související asynchronní stav připraven, v důsledku volá odloženou funkci pomocí vyhodnocení funkce `INVOKE(dfn, dargs..., Ty)`.

Ve všech případech není přidružený asynchronní stav `future` objektu nastaven na *připraveno* , `INVOKE(dfn, dargs..., Ty)` dokud se nedokončí vyhodnocení, buď vyvoláním výjimky, nebo vrácením normálně. Výsledek přidruženého asynchronního stavu je výjimka, pokud byla nějaká vyvolána, nebo libovolná hodnota, která je vrácena vyhodnocením.

> [!NOTE]
> `.wait()` `std::async` `.get()` [](../standard-library/shared-future-class.md)Pro (nebo poslední shared_future), které jsou připojeny k úloze spuštěné pomocí, destruktor zablokuje, jestli se úloha nedokončila. to znamená, že pokud toto vlákno ještě nevolalo, nebo a úkol je `future` pořád běží. Pokud je objekt `future` získaný z volání funkce `std::async` přesunut mimo místní rozsah, jiný kód, který jej používá, musí vědět, že jeho destruktor může být blokován, než sdílený stav změní na stav připraven.

Funkce pseudo-function `INVOKE` je definována ve [ \<funkční >](../standard-library/functional.md).

## <a name="future_category"></a>future_category

Vrátí odkaz na objekt [error_category](../standard-library/error-category-class.md) , který charakterizuje chyby spojené s `future` objekty.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>make_error_code

Vytvoří [error_code](../standard-library/error-code-class.md) spolu s objektem [error_category](../standard-library/error-category-class.md) , který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Hodnota [future_errc](../standard-library/future-enums.md#future_errc) , která identifikuje oznámenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>make_error_condition

Vytvoří [error_condition](../standard-library/error-condition-class.md) spolu s objektem [error_category](../standard-library/error-category-class.md) , který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Hodnota [future_errc](../standard-library/future-enums.md#future_errc) , která identifikuje oznámenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>adresu

Vyměňuje *přidružený asynchronní stav* jednoho `promise` objektu s jiným objektem.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `promise` objekt

*Kliknutím*\
Pravý `promise` objekt.

## <a name="see-also"></a>Viz také:

[\<budoucí >](../standard-library/future.md)
