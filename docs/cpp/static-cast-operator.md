---
title: static_cast – operátor
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: dca6d5297379e6ddc1c70dba80f35f2f55672e49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267125"
---
# <a name="staticcast-operator"></a>static_cast – operátor

Převede *výraz* typu *id typu* pouze na základě typů, které jsou k dispozici ve výrazu.

## <a name="syntax"></a>Syntaxe

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Poznámky

Ve standardním jazyce C++ se pro zajištění bezpečnosti převodu neprovádí žádné typové kontroly za běhu. V jazyce C + +/ CX se provádí kontrola během kompilace a za běhu. Další informace najdete v tématu [přetypování](casting.md).

**Static_cast** operátor lze použít pro operace, jako je například převod ukazatele na základní třídu na ukazatel na odvozenou třídu. Tyto převody nejsou vždy bezpečné.

Obecně můžete použít **static_cast** když chcete převést číselné datové typy, například výčty na čísla nebo čísla na hodnoty float a jsou některé typy dat zapojených do převodu. **static_cast** nejsou tak bezpečné jako převody **dynamic_cast** převody, protože **static_cast** nespouští kontrolu žádný typ za běhu, zatímco **dynamic_cast** nepodporuje. A **dynamic_cast** na nejednoznačný ukazatel se nezdaří, zatímco **static_cast** vrátí, jako kdyby bylo vše; to může být nebezpečné. I když **dynamic_cast** převody jsou bezpečnější, **dynamic_cast** funguje pouze u ukazatelů nebo odkazů a kontrola typu v době spuštění je další režií. Další informace najdete v tématu [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md).

V příkladu, který následuje, řádek `D* pd2 = static_cast<D*>(pb);` není bezpečné protože `D` může obsahovat pole a metody, které nejsou v `B`. Ale řádku `B* pb2 = static_cast<B*>(pd);` je bezpečný převod, protože `D` vždy obsahuje všechny `B`.

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

Rozdíl od [dynamic_cast](../cpp/dynamic-cast-operator.md), žádná kontrola běhu provedena na **static_cast** převod `pb`. Objekt, který odkazuje `pb` nemusí být objekt typu `D`v takovém případě použití `*pd2` může mít katastrofální důsledky. Například volání funkce, který je členem skupiny `D` třídy, ale ne `B` třídy, může vést k narušení přístupu.

**Dynamic_cast** a **static_cast** operátory pohybují ukazatelem v rámci hierarchie tříd. Ale **static_cast** spoléhá výhradně na informace uvedené v prohlášení přetypování a může proto nebezpečný. Příklad:

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

Pokud `pb` ve skutečnosti odkazuje na objekt typu `D`, pak `pd1` a `pd2` dostane stejnou hodnotu. Dostanou také stejnou hodnotu Pokud `pb == 0`.

Pokud `pb` odkazuje na objekt typu `B` a nikoliv na úplnou `D` třídy, a pak **dynamic_cast** bude mít dost informací k vrácení nuly. Ale **static_cast** spoléhá na tvrzení programátora, který `pb` odkazuje na objekt typu `D` a jednoduše vrací ukazatel na tento předpokládaný `D` objektu.

V důsledku toho **static_cast** může provést inverzní implicitní převod; v takovém případě nejsou výsledky definovány. Je ponecháno na programátorovi, aby ověřil, zda jsou výsledky **static_cast** převodu jsou bezpečné.

Toto chování platí také pro jiné typy než typy tříd. Například **static_cast** je možné převést z int na **char**. Avšak výsledný **char** nemusí mít dostatek bitů k uložení celé **int** hodnotu. Opět je ponecháno na programátorovi, aby ověřte, že výsledky **static_cast** převodu jsou bezpečné.

**Static_cast** operátor slouží také k provádění jakýchkoli implicitních převodů, včetně standardních převodů a uživatelem definovaných převodů. Příklad:

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

**Static_cast** operátoru lze explicitně převést integrální hodnotu na typ výčtu. Pokud hodnota integrálního typu nespadá do rozsahu hodnot výčtu, výsledná hodnota výčtu není definována.

**Static_cast** operátor převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.

Libovolný výraz může být explicitně převeden na typ void **static_cast** operátor. Cílový typ void může volitelně zahrnovat **const**, **volatile**, nebo **__unaligned** atribut.

**Static_cast** operátor nemůže přetypovat **const**, **volatile**, nebo **__unaligned** atributy. Zobrazit [operátor const_cast](../cpp/const-cast-operator.md) informace o odebírání těchto atributů.

**C++/ CLI:** Z důvodu nebezpečí provádění nekontrolovaného přetypování nad relokačním kolektorem uvolnění paměti, použití **static_cast** by měly být pouze v kód kritickém pro výkon když jste si jisti, že bude správně fungovat. Pokud je nutné použít **static_cast** v režimu vydání, nahraďte ji [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) v sestavení ladění, aby byl zajištěn úspěch.

## <a name="see-also"></a>Viz také:

[Operátory přetypování](../cpp/casting-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)