---
title: '&lt;Spuštění&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3bce34019f9ed4880d72a9d16c3c8b78dde0e0e3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267880"
---
# <a name="ltexecutiongt"></a>&lt;Spuštění&gt;

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
|[is_execution_policy – struktura](is-execution-policy-struct.md)|Zjistí zásady spouštění pro účely vyloučení podpisech funkcí z účasti rozlišení přetížení jinak nejednoznačný.|
|[parallel_policy třídy](parallel-policy-class.md)|Používá jako jedinečný typ na rozlišení přetížení paralelního algoritmu a značí, že může být paralelizována provádění paralelního algoritmu.|
|[parallel_unsequenced_policy třídy](parallel-unsequenced-policy-class.md)|Používá jako jedinečný typ na rozlišení přetížení paralelního algoritmu a značí, že může být spuštění paralelního algoritmu paralelizovaná a vektorizována.|
|[sequenced_policy třídy](sequenced-policy-class.md)|Používá jako jedinečný typ na rozlišení přetížení paralelního algoritmu a vyžadovat, že nemusí být paralelizována provádění paralelního algoritmu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<spuštění >

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](cpp-standard-library-reference.md)
