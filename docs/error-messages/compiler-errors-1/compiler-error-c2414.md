---
title: Chyba kompilátoru C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 84fa715c8bd567770f361552e203a37c44ffdde4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402980"
---
# <a name="compiler-error-c2414"></a>Chyba kompilátoru C2414

Neplatný počet operandů

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Operační kód nepodporuje počet operandů použít. Zkontrolujte referenčním manuálu sestavení jazyka určit správný počet operandů.

1. Novější procesor podporuje instrukce s různým počtem operandy. Upravit [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) možnost použít novější procesoru.