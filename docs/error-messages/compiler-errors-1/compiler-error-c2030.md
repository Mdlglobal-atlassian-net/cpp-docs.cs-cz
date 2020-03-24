---
title: Chyba kompilátoru C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: e3f3936e6fd37da16c923cb482f45cec11833b3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208029"
---
# <a name="compiler-error-c2030"></a>Chyba kompilátoru C2030

destruktor s přístupností Protected Private nemůže být členem třídy deklarované jako Sealed.

Třída prostředí Windows Runtime deklarovaná jako `sealed` nemůže mít chráněný privátní destruktor. Pro zapečetěné typy jsou povoleny pouze veřejné virtuální a soukromé nevirtuální destruktory. Další informace naleznete v tématu [ref Classes and Structs](../../cppcx/ref-classes-and-structs-c-cx.md).

Chcete-li tuto chybu opravit, změňte přístupnost destruktoru.
