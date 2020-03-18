---
title: sequenced_policy – třída
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444912"
---
# <a name="sequenced_policy-class"></a>sequenced_policy – třída

Používá se jako jedinečný typ k jednoznačnému přetížení paralelního algoritmu a vyžaduje, aby se provádění paralelního algoritmu nemohlo paralelní.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Poznámky

Při provádění paralelního algoritmu se zásadami `execution::sequenced_policy` platí, že pokud vyvolání funkce přístupu k elementu skončí prostřednictvím nezachycené výjimky, `terminate()` být volána.
