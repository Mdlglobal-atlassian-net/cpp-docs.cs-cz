---
title: Chyba kompilátoru C3772
ms.date: 11/04/2016
f1_keywords:
- C3772
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
ms.openlocfilehash: 420e1eb12cbb178459a96f55efab444a538e6c2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400172"
---
# <a name="compiler-error-c3772"></a>Chyba kompilátoru C3772

"name": Neplatná deklarace šablony friend

Je neplatná deklarace typu friend specializace šablony třídy. Nelze deklarovat explicitní nebo částečná specializace šablony třídy a ve stejném příkazu deklarovat typ friend. Tento specializace. *Název* zástupný text označuje neplatnou deklarací.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nedeklarujte spřátelené specializace šablony třídy.

- V případě potřeby pro vaši aplikaci, deklarovat typ friend šablony třídy nebo deklarovat typ friend konkrétní explicitní nebo částečné specializace.

## <a name="example"></a>Příklad

Následující příklad kódu se nezdaří, protože deklaruje přátelská částečná specializace šablony třídy.

```cpp
// c3772.cpp
// compile with: /c

// A class template.
    template<class T> class A {};

// A partial specialization of the class template.
    template<class T> class A<T*> {};

// An explicit specialization.
    template<> class A<char>;

class X {
// Invalid declaration of a friend of a partial specialization.
    template<class T> friend class A<T*>; // C3772

// Instead, if it is appropriate for your application, declare a
// friend of the class template. Consequently, all specializations
// of the class template are friends:
//    template<class T> friend class A;
// Or declare a friend of a particular partial specialization:
//    friend class A<int*>;
// Or declare a friend of a particular explicit specialization:
//    friend class A<char>;
};
```

## <a name="see-also"></a>Viz také:

[Šablony](../../cpp/templates-cpp.md)<br/>
[Specializace šablon](../../cpp/template-specialization-cpp.md)
