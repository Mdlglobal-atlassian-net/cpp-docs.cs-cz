---
title: '&lt;stdexcept&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stdexcept>
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
ms.openlocfilehash: 8a8c99f2651d10d4fc2aff413a06256127f32d7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412498"
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;

Definuje několik standardní třídy používané pro generování sestav výjimky. Třídy tvoří hierarchii odvození všechny odvozené od třídy [výjimka](../standard-library/exception-class.md) a zahrnují dva hlavní typy výjimek: logické chyby a chyby za běhu. Logické chyby jsou způsobeny programátor chyby. Tyto jsou odvozeny z logic_error – základní třída a zahrnují:

- `domain_error`

- `invalid_argument`

- `length_error`

- `out_of_range`

Z důvodu chyby v knihovně funkce nebo v systému za běhu dojít k chybám za běhu. Tyto jsou odvozeny z runtime_error – základní třída a zahrnují:

- `overflow_error`

- `range_error`

- `underflow_error`

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[domain_error – třída](../standard-library/domain-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané domény chybové zprávě.|
|[invalid_argument – třída](../standard-library/invalid-argument-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané oznamuje neplatný argument.|
|[length_error – třída](../standard-library/length-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané hlášení pokus o generování příliš dlouhý a zadat objekt.|
|[logic_error – třída](../standard-library/logic-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané pro hlášení chyb pravděpodobně zjistitelná před spuštěním programu, jako jsou porušení předběžné podmínky logické.|
|[out_of_range – třída](../standard-library/out-of-range-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané argument, který je mimo platný rozsah hlášení.|
|[overflow_error – třída](../standard-library/overflow-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané hlášení aritmetické přetečení.|
|[range_error – třída](../standard-library/range-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané rozsah chybové zprávě.|
|[runtime_error – třída](../standard-library/runtime-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané pro hlášení chyb pravděpodobně zjistitelná jenom v případě, že se program spustí.|
|[underflow_error – třída](../standard-library/underflow-error-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané hlásit k podtečení aritmetické.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
