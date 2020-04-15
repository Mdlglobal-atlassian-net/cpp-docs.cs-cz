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
ms.openlocfilehash: 609d576c6ab3eddca569ed4f19a4024b47b6a1d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374156"
---
# <a name="__if_exists-statement"></a>__if_exists – příkaz

Příkaz **__if_exists** testuje, zda zadaný identifikátor existuje. Pokud identifikátor existuje, zadaný blok příkazu je proveden.

## <a name="syntax"></a>Syntaxe

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Identifikátor*|Identifikátor, jehož existence bude testována.|
|*Příkazy*|Jeden nebo více příkazů, které mají být provedeny, pokud existuje *identifikátor.*|

## <a name="remarks"></a>Poznámky

> [!CAUTION]
> Chcete-li dosáhnout nejspolehlivějších výsledků, použijte **příkaz __if_exists** pod následujícími omezeními.

- Použijte **příkaz __if_exists** pouze na jednoduché typy, nikoli na šablony.

- Použijte **příkaz __if_exists** na identifikátory uvnitř i vně třídy. Nepoužívejte **příkaz __if_exists** na místní proměnné.

- Příkaz **__if_exists** použijte pouze v těle funkce. Mimo tělo funkce, **__if_exists** prohlášení můžete testovat pouze plně definované typy.

- Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.

Doplňkem **prohlášení __if_exists** je [prohlášení __if_not_exists.](../cpp/if-not-exists-statement.md)

## <a name="example"></a>Příklad

Všimněte si, že tento příklad používá šablony, které se nedoporučuje.

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

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__if_not_exists – příkaz](../cpp/if-not-exists-statement.md)
