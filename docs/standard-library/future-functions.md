---
title: '&lt;budoucích&gt;ch funkcí'
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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421749"
---
# <a name="ltfuturegt-functions"></a>&lt;budoucích&gt;ch funkcí

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[adresu](#swap)|

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

\ *zásad*
Hodnota [spuštění](../standard-library/future-enums.md#launch) .

### <a name="remarks"></a>Poznámky

Definice zkratek:

|||
|-|-|
|*dfn*|Výsledek volání funkce `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Výsledky volání funkce `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Typ `result_of<Fn(ArgTypes...)>::type`.|

První šablona funkce vrátí funkci `async(launch::any, fn, args...)`.

Druhá funkce vrátí objekt `future<Ty>`, jehož *přidružený asynchronní stav* obsahuje výsledek společně s hodnotami *DFN* a *dargs* a objekt vlákna ke správě samostatného vlákna provádění.

Není-li typ `decay<Fn>::type` jiný typ než spuštění, nebude se druhá funkce účastnit rozlišení přetížení.

Standardní C++ stavy, které jsou spuštěny v případě, že je spuštěna zásada:: Async, funkce vytvoří nové vlákno. Implementace Microsoftu ale v tuto chvíli nevyhovuje. Získává svá vlákna z fondu vláken systému Windows, což v některých případech může poskytnout recyklovaný podproces místo nového. To znamená, že zásady `launch::async` jsou ve skutečnosti implementované jako `launch::async|launch::deferred`.  Dalším odvozením implementace založeného na podprocesu je, že není nijak zaručeno, že místní proměnné vlákna budou zničeny po dokončení vlákna. Pokud se vlákno recykluje a poskytne novému volání `async`, staré proměnné budou pořád existovat. Proto doporučujeme, abyste pro `async`nepoužívali místní proměnné vlákna.

Pokud je *zásada* `launch::deferred`, funkce označí přidružený asynchronní stav jako drží *odloženou funkci* a vrátí. První volání jakékoli nečasové funkce, která čeká, až bude související asynchronní stav připraven, v důsledku volá odloženou funkci pomocí vyhodnocení funkce `INVOKE(dfn, dargs..., Ty)`.

Ve všech případech není přidružený asynchronní stav objektu `future` *připraven* , dokud se nedokončí vyhodnocení `INVOKE(dfn, dargs..., Ty)`, a to buď vyvoláním výjimky, nebo vrácením normálního typu. Výsledek přidruženého asynchronního stavu je výjimka, pokud byla nějaká vyvolána, nebo libovolná hodnota, která je vrácena vyhodnocením.

> [!NOTE]
> V případě `future`– nebo posledního [shared_future](../standard-library/shared-future-class.md), který je připojen k úloze spuštěné v `std::async`, destruktor zablokuje, pokud se úloha nedokončila. To znamená, že se zablokuje, pokud toto vlákno ještě nevolalo `.get()` nebo `.wait()` a úloha stále běží. Pokud je objekt `future` získaný z volání funkce `std::async` přesunut mimo místní rozsah, jiný kód, který jej používá, musí vědět, že jeho destruktor může být blokován, než sdílený stav změní na stav připraven.

`INVOKE` pseudo-function je definována v [\<funkční >](../standard-library/functional.md).

## <a name="future_category"></a>future_category

Vrátí odkaz na objekt [error_category](../standard-library/error-category-class.md) , který charakterizuje chyby spojené s objekty `future`.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>make_error_code

Vytvoří [error_code](../standard-library/error-code-class.md) společně s objektem [error_category](../standard-library/error-category-class.md) , který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Hodnota [future_errc](../standard-library/future-enums.md#future_errc) identifikující oznámenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>make_error_condition

Vytvoří [error_condition](../standard-library/error-condition-class.md) společně s objektem [error_category](../standard-library/error-category-class.md) , který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Hodnota [future_errc](../standard-library/future-enums.md#future_errc) identifikující oznámenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>adresu

Vyměňuje *přidružený asynchronní stav* jednoho `promise` objektu jiným objektem.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `promise`.

*Pravé*\
Pravý objekt `promise`.

## <a name="see-also"></a>Viz také

[\<budoucích >](../standard-library/future.md)
