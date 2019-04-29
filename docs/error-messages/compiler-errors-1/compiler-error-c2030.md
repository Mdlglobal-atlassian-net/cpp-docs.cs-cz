---
title: Chyba kompilátoru C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: 217f97d205e1da075277b8b0bc22ff3baab13482
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400523"
---
# <a name="compiler-error-c2030"></a>Chyba kompilátoru C2030

destruktor s přístupností protected private nemůže být členem třídy deklarované jako sealed.

Prostředí Windows Runtime třídy deklarované jako `sealed` nemůže mít destruktor chráněné privátní. Veřejné virtuální a privátní nevirtuální destruktory jsou povoleny pouze v zapečetěných typech. Další informace najdete v tématu [referenční třídy a struktury](../../cppcx/ref-classes-and-structs-c-cx.md).

Chcete-li tuto chybu vyřešit, změňte přístupnost destruktor.