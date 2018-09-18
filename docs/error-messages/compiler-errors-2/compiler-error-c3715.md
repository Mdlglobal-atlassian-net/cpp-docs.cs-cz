---
title: Chyba kompilátoru C3715 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63ae3486b4db21a3aa241d5ebdbbfa0cdc6806f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026553"
---
# <a name="compiler-error-c3715"></a>Chyba kompilátoru C3715

"ukazatelů": musí být ukazatel na 'class'

Zadán ukazatel v [__hook](../../cpp/hook.md) nebo [__unhook](../../cpp/unhook.md) , která neukazuje na platnou třídu. Chcete-li tuto chybu opravit, ujistěte se, že vaše `__hook` a `__unhook` volání určují odkazy na platné třídy.