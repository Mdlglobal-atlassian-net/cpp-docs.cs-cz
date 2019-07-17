---
title: parallel_unsequenced_policy třídy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: 92b4e3ce3743fdd3d5ba112a333b2306829b95d4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267988"
---
# <a name="parallelunsequencedpolicy-class"></a>parallel_unsequenced_policy třídy

Používá jako jedinečný typ na rozlišení přetížení paralelního algoritmu a značí, že může být spuštění paralelního algoritmu paralelizovaná a vektorizována.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>Poznámky

Během provádění paralelního algoritmu s `execution::parallel_unsequenced_policy` zásady, pokud se ukončí volání funkce přístupu k elementu prostřednictvím vydá nezachycenou výjimku `terminate()` musí být volána.
