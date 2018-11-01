---
title: Chyba kompilátoru C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: 217f97d205e1da075277b8b0bc22ff3baab13482
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602173"
---
# <a name="compiler-error-c2030"></a>Chyba kompilátoru C2030

destruktor s přístupností protected private nemůže být členem třídy deklarované jako sealed.

Prostředí Windows Runtime třídy deklarované jako `sealed` nemůže mít destruktor chráněné privátní. Veřejné virtuální a privátní nevirtuální destruktory jsou povoleny pouze v zapečetěných typech. Další informace najdete v tématu [referenční třídy a struktury](../../cppcx/ref-classes-and-structs-c-cx.md).

Chcete-li tuto chybu vyřešit, změňte přístupnost destruktor.