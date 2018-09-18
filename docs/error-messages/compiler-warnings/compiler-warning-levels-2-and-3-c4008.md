---
title: Upozornění (úrovně 2 a 3) C4008 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd052b8dd6a0b70dd90ca076d0085675b33dc621
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091176"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Kompilátor upozornění (úrovně 2 a 3) C4008

'identifier': atribut ' attribute ' ignorovat

Kompilátor ignoruje `__fastcall`, **statické**, nebo **vložené** atribut – funkce (upozornění úrovně 3) nebo data (upozornění úrovně 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. `__fastcall` atribut s daty.

1. **statické** nebo **vložené** atributem **hlavní** funkce.