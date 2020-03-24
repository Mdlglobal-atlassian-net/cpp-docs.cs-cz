---
title: Chyba kompilátoru C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: 843676638037aab9544f1fbd8c5c6d56d351e485
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206541"
---
# <a name="compiler-error-c2248"></a>Chyba kompilátoru C2248

*člen*: nejde získat přístup k členu*access_level*deklarovanému ve třídě*Class*.

Členové odvozené třídy nemají přístup `private` členů základní třídy. Nemůžete získat přístup k `private` nebo `protected` členů instancí třídy.

## <a name="example"></a>Příklad

Následující ukázka generuje C2248, pokud jsou k soukromým nebo chráněným členům třídy přistup z vnějšku třídy. Chcete-li tento problém vyřešit, neprovádějte přístup k těmto členům přímo mimo třídu. Použijte veřejná Členská data a členské funkce pro interakci s třídou.

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

Další problém s vyhovujícím problémem, který zveřejňuje C2248, je použití šablon a specializace šablon. Chcete-li tento problém vyřešit, Deklarujte funkci Friend Template pomocí prázdného seznamu parametrů šablony < > nebo specifických parametrů šablony.

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

Další problém s vyhovujícím problémem, který zveřejňuje C2248, je když se pokusíte deklarovat přítele třídy a když třída není viditelná pro deklaraci typu Friend v oboru třídy. Chcete-li tento problém vyřešit, udělte do ohraničující třídy přátelství.

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
