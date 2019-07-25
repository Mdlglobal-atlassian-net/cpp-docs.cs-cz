---
title: '&lt;budoucí&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: a5bcebd80b296a0b8416580aa03acc59ce3750cd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448223"
---
# <a name="ltfuturegt-enums"></a>&lt;budoucí&gt; výčty

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[předběžné](#launch)|

## <a name="future_errc"></a>Výčet future_errc

Poskytuje symbolické názvy pro všechny chyby, které jsou hlášeny třídou [future_error](../standard-library/future-error-class.md) .

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status"></a>Výčet future_status

Poskytuje symbolické názvy pro důvody, které může funkce časovaného čekání vrátit.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch"></a>spustit výčet

Představuje typ maskování, který popisuje možné režimy pro funkci šablony [Async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Viz také:

[\<budoucí >](../standard-library/future.md)
