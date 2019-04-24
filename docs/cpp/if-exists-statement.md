---
title: __if_exists – příkaz
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: 9d5a0b24bb08a9485b2d212058fa8f0bd82e5842
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183671"
---
# <a name="ifexists-statement"></a>__if_exists – příkaz

**__If_exists** příkaz testuje, jestli existuje zadaný identifikátor. Pokud identifikátor neexistuje, je spuštěn zadaný blok příkazů.

## <a name="syntax"></a>Syntaxe

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*identifier*|Identifikátor, jehož existence bude testována.|
|*Příkazy*|Jeden nebo více příkazů, které budou spuštěny, pokud *identifikátor* existuje.|

## <a name="remarks"></a>Poznámky

> [!CAUTION]
>  K dosažení nejspolehlivějších výsledků, použít **__if_exists** příkaz následujícími omezeními.

- Použít **__if_exists** příkazu pouze jednoduché typy, nikoli na šablony.

- Použít **__if_exists** příkaz na identifikátory uvnitř i vně třídy. Se nevztahují **__if_exists** příkaz pro lokální proměnné.

- Použití **__if_exists** příkaz jenom v těle funkce. Mimo tělo funkce **__if_exists** příkazu můžete testovat pouze plně definované typy.

- Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.

Doplněk k **__if_exists** příkaz je [__if_not_exists](../cpp/if-not-exists-statement.md) příkazu.

## <a name="example"></a>Příklad

Všimněte si, že v tomto příkladu šablony, které se nedoporučuje.

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>Výstup

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>Viz také:

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__if_not_exists – příkaz](../cpp/if-not-exists-statement.md)