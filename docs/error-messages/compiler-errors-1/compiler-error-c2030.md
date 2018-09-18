---
title: Chyba kompilátoru C2030 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0c5849c372cc4c7ebf27dbe010e65d406ad1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032890"
---
# <a name="compiler-error-c2030"></a>Chyba kompilátoru C2030

destruktor s přístupností protected private nemůže být členem třídy deklarované jako sealed.

Prostředí Windows Runtime třídy deklarované jako `sealed` nemůže mít destruktor chráněné privátní. Veřejné virtuální a privátní nevirtuální destruktory jsou povoleny pouze v zapečetěných typech. Další informace najdete v tématu [referenční třídy a struktury](../../cppcx/ref-classes-and-structs-c-cx.md).

Chcete-li tuto chybu vyřešit, změňte přístupnost destruktor.