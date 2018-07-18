---
title: '&lt;budoucí&gt; funkce | Dokumentace Microsoftu'
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
ms.openlocfilehash: bbb724747052c6dd636199fd1cabdf97d2bd4045
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027394"
---
# <a name="ltfuturegt-functions"></a>&lt;budoucí&gt; funkce

||||
|-|-|-|
|[async](#async)|[future_category –](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[Prohození](#swap)|

## <a name="async"></a>  asynchronní

Představuje *asynchronního poskytovatele*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parametry

*zásady* A [spuštění](../standard-library/future-enums.md#launch) hodnotu.

### <a name="remarks"></a>Poznámky

Definice zkratek:

|||
|-|-|
|*dfn*|Výsledek volání funkce `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Výsledky volání funkce `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Typ `result_of<Fn(ArgTypes...)>::type`.|

První šablona funkce vrátí funkci `async(launch::any, fn, args...)`.

Druhá funkce vrátí `future<Ty>` jehož *přidružený asynchronní stav* uchovává výsledek spolu s hodnotami *dfn* a *dargs* a vlákno objekt pro správu samostatného vlákna provádění.

Není-li typ `decay<Fn>::type` jiný typ než spuštění, nebude se druhá funkce účastnit rozlišení přetížení.

C++ standard uvádí, že pokud je zásada launch::async, funkce vytvoří nové vlákno. Ale implementace společnosti Microsoft je aktuálně nonkonformní. Získá podprocesy z fondu podprocesů Windows, což v některých případech může poskytnout recyklován vlákno spíše než nové. To znamená, že `launch::async` zásad je ve skutečnosti implementovat jako `launch::async|launch::deferred`.  Jiné nepřímo provádění na základě fondu vláken je, že neexistuje žádná záruka, že místní proměnné vlákna zničí po dokončení vlákna. Pokud je vlákno recyklaci a k dispozici nové volání na `async`, bude stále existují staré proměnné. Doporučujeme proto, že je velmi riskantní používat místní proměnné vlákna s `async`.

Pokud *zásady* je `launch::deferred`, označí tato funkce jeho přidružený asynchronní stav jako držení *odložené funkce* a vrátí. První volání jakékoli nečasové funkce, která čeká, až bude související asynchronní stav připraven, v důsledku volá odloženou funkci pomocí vyhodnocení funkce `INVOKE(dfn, dargs..., Ty)`.

Ve všech případech přidružený asynchronní stav `future` není nastaven na *připravené* dokud vyhodnocení funkce `INVOKE(dfn, dargs..., Ty)` dokončení vyvoláním výjimky nebo normálním vrácením. Výsledek přidruženého asynchronního stavu je výjimka, pokud byla nějaká vyvolána, nebo libovolná hodnota, která je vrácena vyhodnocením.

> [!NOTE]
> Pro `future`– nebo poslední [shared_future –](../standard-library/shared-future-class.md)–, který je připojen k úloze spuštěné pomocí `std::async`je destruktor blokován, pokud úkol nebyl dokončen, tedy blokuje, pokud toto vlákno dosud nevolalo `.get()` nebo `.wait()` a je stále spuštěn úkol. Pokud je objekt `future` získaný z volání funkce `std::async` přesunut mimo místní rozsah, jiný kód, který jej používá, musí vědět, že jeho destruktor může být blokován, než sdílený stav změní na stav připraven.

Pseudofunkce `INVOKE` je definována v [ \<funkční >](../standard-library/functional.md).

## <a name="future_category"></a>  future_category –

Vrátí odkaz na [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje chyby, které jsou přidružené k `future` objekty.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>  make_error_code –

Vytvoří [error_code](../standard-library/error-code-class.md) spolu s [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno* A [future_errc](../standard-library/future-enums.md#future_errc) hodnotu, která identifikuje ohlášenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>  make_error_condition –

Vytvoří [error_condition –](../standard-library/error-condition-class.md) spolu s [error_category](../standard-library/error-category-class.md) objekt, který charakterizuje [budoucí](../standard-library/future-class.md) chyby.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno* A [future_errc](../standard-library/future-enums.md#future_errc) hodnotu, která identifikuje ohlášenou chybu.

### <a name="return-value"></a>Návratová hodnota

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>  Prohození

Výměna *přidružený asynchronní stav* jednoho `promise` objektu z jiného.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlevo* vlevo `promise` objektu.

*Pravé* vpravo `promise` objektu.

## <a name="see-also"></a>Viz také:

[\<Další >](../standard-library/future.md)<br/>
