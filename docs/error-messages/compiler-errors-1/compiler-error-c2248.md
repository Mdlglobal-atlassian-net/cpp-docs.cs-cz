---
title: Chyba kompilátoru C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: d9b9a6c04e7e9a5d88df516125280b6b23894a01
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302550"
---
# <a name="compiler-error-c2248"></a>Chyba kompilátoru C2248

"*člen*': Nelze získat přístup k '*access_level*"člen deklarovaný ve třídě"*třídy*"

Nedaří se členy odvozené třídy `private` členy základní třídy. Nejde získat přístup `private` nebo `protected` členů instance třídy.

## <a name="example"></a>Příklad

Následující ukázka generuje C2248 při soukromé nebo chráněné členy třídy jsou přístupné z mimo třídu. Chcete-li vyřešit tento problém, nemají přístup k těchto členů mimo třídu přímo. Použití dat veřejné členy a členské funkce pro interakci s třídou.

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

Jiný problém shoda, která zveřejňuje C2248 je použití šablona – friends a specializace. Chcete-li vyřešit tento problém, deklarace typu friend šablony funkce pomocí <> seznam parametrů prázdnou šablonu nebo konkrétní šablonu. parametry.

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

Jiný problém shoda, která zveřejňuje C2248 je při pokusu o deklarovat typ friend třídy a třídy není viditelný pro deklarace typu friend v oboru třídy. Chcete-li vyřešit tento problém, udělte Přátelský k nadřazené třídy.

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```