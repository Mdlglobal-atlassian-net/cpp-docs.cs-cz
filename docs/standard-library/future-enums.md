---
title: '&lt;budoucích výčtů&gt;'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: a5bcebd80b296a0b8416580aa03acc59ce3750cd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865167"
---
# <a name="ltfuturegt-enums"></a>&lt;budoucích výčtů&gt;

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[předběžné](#launch)|

## <a name="future_errc"></a>Výčet future_errc

Poskytuje symbolické názvy pro všechny chyby, které jsou hlášeny [future_error](../standard-library/future-error-class.md) třídou.

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

## <a name="see-also"></a>Viz také

[\<budoucích >](../standard-library/future.md)
