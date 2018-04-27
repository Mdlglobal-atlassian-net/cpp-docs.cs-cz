---
title: '&lt;budoucí&gt; výčty | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: a32f777842b3c14a5c6f15d9c1c3b534bc4ffad8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltfuturegt-enums"></a>&lt;budoucí&gt; výčty

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Spuštění](#launch)|

## <a name="future_errc"></a>  future_errc – výčet

Poskytuje symbolické názvy pro všechny chyby, které jsou hlášeny [future_error](../standard-library/future-error-class.md) třídy.

Třída future_errc {broken_promise, future_already_retrieved, promise_already_satisfied, no_state};

## <a name="future_status"></a>  future_status – výčet

Poskytuje symbolické názvy z důvodů, které můžou vrátit funkce vypršel čekání.

```cpp
enum future_status{    ready,
    timeout,
 deferred};
```

## <a name="launch"></a>  Launch – výčet

Představuje typ bitová maska, která popisuje možné režimy pro funkce šablony [asynchronní](../standard-library/future-functions.md#async).

Třída spuštění {asynchronní, odložení};

## <a name="see-also"></a>Viz také

[\<budoucí >](../standard-library/future.md)<br/>
