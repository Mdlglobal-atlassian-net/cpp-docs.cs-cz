---
title: Chyba kompilátoru C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: 81e2da31b39b323919132ae86cd365d9c119be32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402954"
---
# <a name="compiler-error-c2415"></a>Chyba kompilátoru C2415

nesprávný typ operandu

Opcode nepoužívá operandy tohoto typu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Operační kód nepodporuje počet operandů použít. Zkontrolujte referenčním manuálu sestavení jazyka určit správný počet operandů.

1. Novější procesor podporuje instrukce s další typy. Upravit [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) možnost použít novější procesoru.