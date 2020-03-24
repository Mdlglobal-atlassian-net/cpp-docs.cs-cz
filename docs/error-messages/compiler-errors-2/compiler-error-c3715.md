---
title: Chyba kompilátoru C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 13befc17b94fdf2c22cb84bc64ed55b9375b3473
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165909"
---
# <a name="compiler-error-c3715"></a>Chyba kompilátoru C3715

' pointer ': musí být ukazatel na ' class '

V [__hook](../../cpp/hook.md) nebo [__unhook](../../cpp/unhook.md) jste zadali ukazatel, který neodkazuje na platnou třídu. Chcete-li tuto chybu opravit, zajistěte, aby vaše `__hook` a `__unhook` zavolaly ukazatele na platné třídy.
