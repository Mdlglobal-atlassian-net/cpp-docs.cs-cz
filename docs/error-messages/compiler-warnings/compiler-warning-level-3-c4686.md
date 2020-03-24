---
title: Upozornění kompilátoru (úroveň 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: a8eae1ddeb875d267b82c67e989cb41e8c9b2afb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185448"
---
# <a name="compiler-warning-level-3-c4686"></a>Upozornění kompilátoru (úroveň 3) C4686

> '*uživatelsky definovaný typ*': možná změna chování, změna v konvenci zpětného volání UDT

## <a name="remarks"></a>Poznámky

Specializace šablony třídy nebyla definována předtím, než byla použita v návratovém typu. Cokoli, co vytvoří instance třídy, vyřeší C4686; deklarace instance nebo přístup ke členu (C\<int >:: cokoli) jsou také možnosti.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Příklad

Místo toho zkuste použít následující:

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
