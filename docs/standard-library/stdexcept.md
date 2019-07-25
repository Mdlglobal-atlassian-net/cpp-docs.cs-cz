---
title: '&lt;stdexcept&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stdexcept>
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
ms.openlocfilehash: d4028d57a6e8898f85a37d9731e7e8d4cda19a2f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453720"
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;

Definuje několik standardních tříd používaných pro vytváření sestav výjimek. Třídy tvoří hierarchii odvození vše odvozenou z [výjimky](../standard-library/exception-class.md) třídy a zahrnují dva obecné typy výjimek: logické chyby a běhové chyby. Logické chyby způsobují chyby programátora. Jsou odvozeny ze základní třídy logic_error a zahrnují:

- `domain_error`

- `invalid_argument`

- `length_error`

- `out_of_range`

K chybám za běhu dochází z důvodu chyb v knihovně funkcí nebo v systému za běhu. Jsou odvozeny ze základní třídy runtime_error a zahrnují:

- `overflow_error`

- `range_error`

- `underflow_error`

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[domain_error – třída](../standard-library/domain-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení chyby domény.|
|[invalid_argument – třída](../standard-library/invalid-argument-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení neplatného argumentu.|
|[length_error – třída](../standard-library/length-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané pro hlášení pokusu o vygenerování objektu, který je příliš dlouhý.|
|[logic_error – třída](../standard-library/logic-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení chyb, které byly zjištěny před provedením programu, například porušení logických podmínek.|
|[out_of_range – třída](../standard-library/out-of-range-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané pro hlášení argumentu, který je mimo platný rozsah.|
|[overflow_error – třída](../standard-library/overflow-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení aritmetického přetečení.|
|[range_error – třída](../standard-library/range-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení chyby rozsahu.|
|[runtime_error – třída](../standard-library/runtime-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané k ohlášení chyb, které jsou pravděpodobně zjišťovány pouze v případě, že je program proveden.|
|[underflow_error – třída](../standard-library/underflow-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané pro hlášení aritmetického podtečení.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
