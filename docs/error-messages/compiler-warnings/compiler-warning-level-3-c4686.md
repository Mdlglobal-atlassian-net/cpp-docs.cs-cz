---
title: Upozornění (úroveň 3) C4686 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4686
dev_langs:
- C++
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32a44cd929eb7629ef317ce9847950b613bde52c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202077"
---
# <a name="compiler-warning-level-3-c4686"></a>Kompilátor upozornění (úroveň 3) C4686

> "*uživatelem definovaného typu*': možné změny v chování, změna ve vrácení konvence volání

## <a name="remarks"></a>Poznámky

Specializace šablony třídy nebyl určen předtím, než byl použit v návratovém typu. Cokoli, co vytvoří instanci třídy vyřeší C4686; deklarování instance nebo přístup ke členovi (C\<int >:: NIC) jsou také možnosti.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

## <a name="example"></a>Příklad

Zkuste místo toho následující:

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```