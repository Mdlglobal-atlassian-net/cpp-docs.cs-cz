---
title: '&lt;budoucí&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 0f1064fdf434560c3130d1254512470cc5bc1ee0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370699"
---
# <a name="ltfuturegt-enums"></a>&lt;budoucí&gt; výčty

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Spuštění](#launch)|

## <a name="future_errc-enumeration"></a><a name="future_errc"></a>future_errc výčet

Poskytuje symbolické názvy pro všechny chyby, které jsou hlášeny [future_error](../standard-library/future-error-class.md) třídy.

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a>future_status Výčet

Poskytuje symbolické názvy z důvodů, které může vrátit funkce časovaného čekání.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a>spuštění výčtu

Představuje typ bitové masky, který popisuje možné režimy pro [asynchronní](../standard-library/future-functions.md#async)funkci šablony .

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Viz také

[\<budoucí>](../standard-library/future.md)
