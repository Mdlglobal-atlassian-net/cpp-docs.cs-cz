---
title: '&lt;budoucí&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 83a1d50c0041c3cd66abbd3d52d2e2b49231c81c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ltfuturegt-functions"></a>&lt;budoucí&gt; funkce

||||
|-|-|-|
|[async](#async)|[future_category –](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[Swap](#swap)|

## <a name="async"></a>  Asynchronní

Představuje *asynchronní zprostředkovatele*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parametry

`policy` A [spusťte](../standard-library/future-enums.md#launch) hodnotu.

### <a name="remarks"></a>Poznámky

Definice zkratek:

|||
|-|-|
|*dfn*|Výsledek volání funkce `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Výsledky volání funkce `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Typ `result_of<Fn(ArgTypes...)>::type`.|

První šablona funkce vrátí funkci `async(launch::any, fn, args...)`.

Druhý funkce vrátí hodnotu `future<Ty>` objekt, jehož *přidružené asynchronní stavu* obsahuje výsledek spolu s hodnotami *dfn* a *dargs* a vlákna objekt, který chcete spravovat samostatný podproces provádění.

Není-li typ `decay<Fn>::type` jiný typ než spuštění, nebude se druhá funkce účastnit rozlišení přetížení.

Pokud má parametr `policy` hodnotu `launch::any`, může tato funkce vybrat funkci `launch::async` nebo `launch::deferred`. V této implementaci funkce používá funkci `launch::async`.

Pokud má parametr `policy` hodnotu `launch::async`, vytvoří tato funkce vlákno, jehož výsledkem je funkce `INVOKE(dfn, dargs..., Ty)`. Funkce se vrátí po vytvoření vlákna bez čekání na výsledky. Pokud systém nelze spustit nové vlákno, funkce vyvolá [system_error –](../standard-library/system-error-class.md) s kódem chyby `resource_unavailable_try_again`.

Pokud `policy` je `launch::deferred`, funkce označuje stav přidružené asynchronní jako podniku *odložení funkce* a vrátí. První volání jakékoli nečasové funkce, která čeká, až bude související asynchronní stav připraven, v důsledku volá odloženou funkci pomocí vyhodnocení funkce `INVOKE(dfn, dargs..., Ty)`.

Ve všech případech přidružený stav asynchronní `future` objekt není nastavený na *připraven* až po vyhodnocení `INVOKE(dfn, dargs..., Ty)` dokončí, došlo k výjimce nebo vrácení normálně. Výsledek přidruženého asynchronního stavu je výjimka, pokud byla nějaká vyvolána, nebo libovolná hodnota, která je vrácena vyhodnocením.

> [!NOTE]
> Pro `future`– nebo poslední [shared_future](../standard-library/shared-future-class.md)– připojená k úloze začít s `std::async`destruktor bloky, pokud úloha nebyla dokončena; to znamená, blokuje, pokud tohoto podprocesu ještě nezavolalo `.get()` nebo `.wait()` a je stále spuštěná úloha. Pokud je objekt `future` získaný z volání funkce `std::async` přesunut mimo místní rozsah, jiný kód, který jej používá, musí vědět, že jeho destruktor může být blokován, než sdílený stav změní na stav připraven.

Funkci pseudo `INVOKE` je definována v [ \<funkční >](../standard-library/functional.md).

## <a name="future_category"></a>  future_category –

Vrátí odkaz na [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje chyby, které jsou přidružené `future` objekty.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>  make_error_code –

Vytvoří [error_code](../standard-library/error-code-class.md) společně s [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

`Errno` A [future_errc](../standard-library/future-enums.md#future_errc) hodnotu, která identifikuje chybu.

### <a name="return-value"></a>Návratová hodnota

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>  make_error_condition –

Vytvoří [error_condition](../standard-library/error-condition-class.md) společně s [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

`Errno` A [future_errc](../standard-library/future-enums.md#future_errc) hodnotu, která identifikuje chybu.

### <a name="return-value"></a>Návratová hodnota

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>  Swap

Výměnu *přidružené asynchronní stavu* jednoho `promise` objekt se stejným jiného.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `promise` objektu.

`Right` Právo `promise` objektu.

## <a name="see-also"></a>Viz také

[\<budoucí >](../standard-library/future.md)<br/>
