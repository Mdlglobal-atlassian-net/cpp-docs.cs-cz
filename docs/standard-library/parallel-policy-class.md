---
title: parallel_policy třídy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 7bb2b095a50e664dfc585e0bd4aaa608a6ad8e95
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268042"
---
# <a name="parallelpolicy-class"></a>parallel_policy třídy

Používá jako jedinečný typ na rozlišení přetížení paralelního algoritmu a značí, že může být paralelizována provádění paralelního algoritmu.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::parallel_policy;
```

## <a name="remarks"></a>Poznámky

Během provádění paralelního algoritmu s `execution::parallel_policy` zásady, pokud se ukončí volání funkce přístupu k elementu prostřednictvím vydá nezachycenou výjimku `terminate()` musí být volána.
