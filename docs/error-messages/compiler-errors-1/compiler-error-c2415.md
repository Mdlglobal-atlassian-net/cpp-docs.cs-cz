---
title: Chyba kompilátoru C2415 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd889880997828396521ddba638bb606552e7d92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112574"
---
# <a name="compiler-error-c2415"></a>Chyba kompilátoru C2415

nesprávný typ operandu

Opcode nepoužívá operandy tohoto typu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Operační kód nepodporuje počet operandů použít. Zkontrolujte referenčním manuálu sestavení jazyka určit správný počet operandů.

1. Novější procesor podporuje instrukce s další typy. Upravit [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) možnost použít novější procesoru.