---
title: sequenced_policy třídy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 63be7166b84fa452f53baf6b6de16831eb657a23
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268111"
---
# <a name="sequencedpolicy-class"></a>sequenced_policy třídy

Používá jako jedinečný typ na rozlišení přetížení paralelního algoritmu a vyžadovat, že nemusí být paralelizována provádění paralelního algoritmu.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Poznámky

Během provádění paralelního algoritmu s `execution::sequenced_policy` zásady, pokud se ukončí volání funkce přístupu k elementu prostřednictvím vydá nezachycenou výjimku `terminate()` musí být volána.
