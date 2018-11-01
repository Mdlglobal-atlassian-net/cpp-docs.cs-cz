---
title: Chyba kompilátoru C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 94a451bbe936507ac3b33747065a9b6aac9edd02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660613"
---
# <a name="compiler-error-c3715"></a>Chyba kompilátoru C3715

"ukazatelů": musí být ukazatel na 'class'

Zadán ukazatel v [__hook](../../cpp/hook.md) nebo [__unhook](../../cpp/unhook.md) , která neukazuje na platnou třídu. Chcete-li tuto chybu opravit, ujistěte se, že vaše `__hook` a `__unhook` volání určují odkazy na platné třídy.