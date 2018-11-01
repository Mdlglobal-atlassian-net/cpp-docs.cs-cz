---
title: Chyba kompilátoru C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 84fa715c8bd567770f361552e203a37c44ffdde4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451048"
---
# <a name="compiler-error-c2414"></a>Chyba kompilátoru C2414

Neplatný počet operandů

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Operační kód nepodporuje počet operandů použít. Zkontrolujte referenčním manuálu sestavení jazyka určit správný počet operandů.

1. Novější procesor podporuje instrukce s různým počtem operandy. Upravit [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) možnost použít novější procesoru.