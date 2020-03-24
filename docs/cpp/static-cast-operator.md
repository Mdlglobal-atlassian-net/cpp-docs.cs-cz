---
title: static_cast – operátor
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 37708bf50b28eb120af8e8a79e770c3121e6f509
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178584"
---
# <a name="static_cast-operator"></a>static_cast – operátor

Převede *výraz* na typ *typu-ID* založený pouze na typech, které jsou k dispozici ve výrazu.

## <a name="syntax"></a>Syntaxe

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Poznámky

Ve standardním jazyce C++ se pro zajištění bezpečnosti převodu neprovádí žádné typové kontroly za běhu. V jazyce C + +/ CX se provádí kontrola během kompilace a za běhu. Další informace naleznete v tématu [přetypování](casting.md).

Operátor **static_cast** lze použít pro operace, jako je například převod ukazatele na základní třídu na ukazatel na odvozenou třídu. Tyto převody nejsou vždy bezpečné.

Obecně se používá **static_cast** , když chcete převést číselné datové typy, například výčty na čísla nebo čísla na hodnoty float, a Vy jste si jisti datovými typy, které jsou součástí převodu. **static_cast** převody nejsou tak bezpečné jako **dynamic_cast** převody, protože **static_cast** neprovádí kontrolu za běhu, zatímco **dynamic_cast** . **Dynamic_cast** k nejednoznačnému ukazateli selže, zatímco **static_cast** se vrátí, jako kdyby nebylo nic chybné; To může být nebezpečné. I když jsou převody **dynamic_cast** bezpečnější, **dynamic_cast** funguje pouze u ukazatelů nebo odkazů a kontrolní typ za běhu je režijní náklady. Další informace najdete v tématu [operátor dynamic_cast](../cpp/dynamic-cast-operator.md).

V následujícím příkladu `D* pd2 = static_cast<D*>(pb);` řádek není bezpečný, protože `D` může obsahovat pole a metody, které nejsou v `B`. Řádková `B* pb2 = static_cast<B*>(pd);` však představuje bezpečný převod, protože `D` vždy obsahuje všechny `B`.

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

Na rozdíl od [dynamic_cast](../cpp/dynamic-cast-operator.md)neprovádí žádná kontrolní rutina **static_cast** konverzi `pb`. Objekt, na který ukazuje `pb`, nesmí být objekt typu `D`. v takovém případě by použití `*pd2` mohlo být katastrofální důsledky. Například volání funkce, která je členem třídy `D`, ale ne `B` třídy, může mít za následek porušení přístupu.

Operátory **dynamic_cast** a **static_cast** přesouvají ukazatel v rámci hierarchie tříd. **Static_cast** však spoléhá výhradně na informace uvedené v příkazu cast a může být proto nebezpečná. Příklad:

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

Pokud `pb` skutečně odkazuje na objekt typu `D`, pak `pd1` a `pd2` získají stejnou hodnotu. Budou také mít stejnou hodnotu, pokud `pb == 0`.

Pokud `pb` odkazuje na objekt typu `B` a nikoli na úplnou třídu `D`, **dynamic_cast** bude dostatečně známa, aby vracela hodnotu nula. Nicméně **static_cast** spoléhá na tvrzení programátora, že `pb` odkazuje na objekt typu `D` a jednoduše vrátí ukazatel na tento předpokládaný objekt `D`.

V důsledku toho **static_cast** možné provést invertování implicitních převodů, v takovém případě nejsou výsledky definovány. Je ponecháno na programátorovi, aby bylo možné ověřit, zda jsou výsledky převodu **static_cast** bezpečné.

Toto chování platí také pro jiné typy než typy tříd. Například **static_cast** lze použít pro převod typu int na typ **char**. Výsledný **znak char** však nemusí mít dostatek bitů pro uložení celé hodnoty **int** . Znovu je ponecháno na programátorovi, aby bylo možné ověřit, zda jsou výsledky převodu **static_cast** bezpečné.

Operátor **static_cast** lze také použít k provedení jakéhokoli implicitního převodu, včetně standardních převodů a uživatelem definovaných převodů. Příklad:

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

Operátor **static_cast** může explicitně převést integrální hodnotu na typ výčtu. Pokud hodnota integrálního typu nespadá do rozsahu hodnot výčtu, výsledná hodnota výčtu není definována.

Operátor **static_cast** převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.

Libovolný výraz může být explicitně převeden na typ void operátorem **static_cast** . Cílový typ void může volitelně zahrnovat atribut **const**, **volatile**nebo **__unaligned** .

Operátor **static_cast** nemůže přetypovat na atributy **const**, **volatile**nebo **__unaligned** . Informace o odebírání těchto atributů najdete v tématu [operátor const_cast](../cpp/const-cast-operator.md) .

**C++/CLI:** Z důvodu nebezpečí provádění nekontrolovaného přetypování nad přemístění systému uvolňování paměti by použití **static_cast** mělo být pouze v kódu kritickém pro výkon, když jste si jisti, že bude správně fungovat. Pokud je nutné použít **static_cast** v režimu vydání, nahraďte ji [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) v sestavení ladění, abyste zajistili úspěch.

## <a name="see-also"></a>Viz také

[Operátory přetypování](../cpp/casting-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
