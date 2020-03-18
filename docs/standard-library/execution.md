---
title: spuštění &lt;&gt;
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 81e9aa63265c367412fda709aacd5ca3953e9fdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445029"
---
# <a name="ltexecutiongt"></a>spuštění &lt;&gt;

Popisuje zásady spouštění paralelních algoritmů.

## <a name="syntax"></a>Syntaxe

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[is_execution_policy struktura](is-execution-policy-struct.md)|Detekuje zásady spouštění pro účely vyloučení signatur funkcí z jiné nejednoznačné účasti na rozlišení přetížení.|
|[parallel_policy – třída](parallel-policy-class.md)|Slouží jako jedinečný typ k jednoznačnému přetížení paralelního algoritmu a označuje, že spuštění paralelního algoritmu může být paralelní.|
|[parallel_unsequenced_policy – třída](parallel-unsequenced-policy-class.md)|Slouží jako jedinečný typ k jednoznačnému přetížení paralelního algoritmu a naznačují, že provádění paralelního algoritmu může být paralelní a vektorové.|
|[sequenced_policy – třída](sequenced-policy-class.md)|Používá se jako jedinečný typ k jednoznačnému přetížení paralelního algoritmu a vyžaduje, aby se provádění paralelního algoritmu nemohlo paralelní.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<provádění >

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také

\ [referenčních souborů hlaviček](cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](cpp-standard-library-reference.md)
