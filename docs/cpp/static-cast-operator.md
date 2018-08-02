---
title: static_cast – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b01e9799a1f8b03406750dca0b486c6c4d0f655
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466693"
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
  
 Z důvodu nebezpečí provádění nekontrolovaného přetypování nad relokačním kolektorem uvolnění paměti, použití **static_cast** by měly být pouze v kód kritickém pro výkon když jste si jisti, že bude správně fungovat. Pokud je nutné použít **static_cast** v režimu vydání, nahraďte ji [safe_cast](../windows/safe-cast-cpp-component-extensions.md) v sestavení ladění, aby byl zajištěn úspěch.  
  
## <a name="see-also"></a>Viz také:  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)