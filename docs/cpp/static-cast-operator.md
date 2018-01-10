---
title: "static_cast – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: static_cast_cpp
dev_langs: C++
helpviewer_keywords: static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3913937d9099304c478404c4c55a09fa54392785
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="staticcast-operator"></a>static_cast – operátor
Převede *výraz* typu *id typu* podle pouze typy, které jsou k dispozici ve výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static_cast <type-id> ( expression )   
```  
  
## <a name="remarks"></a>Poznámky  
 Ve standardním jazyce C++ se pro zajištění bezpečnosti převodu neprovádí žádné typové kontroly za běhu. V jazyce C + +/ CX se provádí kontrola během kompilace a za běhu. Další informace najdete v tématu [přetypování](casting.md).  
  
 `static_cast` Operátor lze použít pro operace, jako je například převodu ukazatel na základní třída pro ukazatel na odvozené třídy. Tyto převody nejsou vždy bezpečné.  
  
 Obecně používáte `static_cast` Pokud chcete převést na proměnné ints nebo proměnné ints obtékaných objektů, a číselné datové typy, jako je například výčty určitých typů dat podílí převod. `static_cast`převody nejsou jako bezpečné jako `dynamic_cast` převody, protože `static_cast` zkontrolovat žádný typ spuštění, při `dynamic_cast` nepodporuje. A `dynamic_cast` na nejednoznačný ukazatel se nezdaří, zatímco `static_cast` vrátí, jako kdyby nic nesprávný; to může být nebezpečný. I když `dynamic_cast` převody jsou bezpečnější, `dynamic_cast` pouze funguje na ukazatele nebo odkazů a kontrola typu běhu je režijní náklady. Další informace najdete v tématu [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md).  
  
 V příkladu, který následuje, řádek `D* pd2 = static_cast<D*>(pb);` není bezpečná protože `D` může mít pole a metody, které nejsou v `B`. Ale řádku `B* pb2 = static_cast<B*>(pd);` je převodu z bezpečné, protože `D` vždy obsahuje všechny `B`.  
  
```  
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
  
 Rozdíl k [dynamic_cast](../cpp/dynamic-cast-operator.md), není provedena žádná kontrola běhu na `static_cast` převod `pb`. Objekt na kterou odkazuje `pb` nemusí být objekt typu `D`, v takovém případě použití `*pd2` může být katastrofální. Například volání funkce, který je členem skupiny `D` třídy, ale ne `B` třídy, může mít za následek porušení přístupu.  
  
 `dynamic_cast` a `static_cast` operátory přesunout ukazatel v celé hierarchii tříd. Ale `static_cast` využívá výhradně na informacích uvedených v příkazu cast a proto může nebezpečný. Příklad:  
  
```  
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
  
 Pokud `pb` skutečně odkazuje na objekt typu `D`, pak `pd1` a `pd2` mít stejnou hodnotu. Budou bude mít také stejnou hodnotu Pokud `pb == 0`.  
  
 Pokud `pb` odkazuje na objekt typu `B` , ne na kompletní `D` třídy, a pak `dynamic_cast` věděli, že je dost vrátit nula. Ale `static_cast` spoléhá na assertion pro programátory, `pb` odkazuje na objekt typu `D` a jednoduše vrací ukazatel na který by měl `D` objektu.  
  
 V důsledku toho `static_cast` můžete provést inverzní implicitní převody, v takovém případě výsledky nejsou definovány. Pro programátory ověřit, jestli je ponechán výsledky `static_cast` převod jsou bezpečné.  
  
 Toto chování platí také pro jiné typy než typy tříd. Například `static_cast` lze převést na typ int `char`. Ale výsledná `char` nemusí mít dostatek bits k uložení celého `int` hodnotu. Znovu, je ponechán pro programátory ověřit, jestli výsledky `static_cast` převod jsou bezpečné.  
  
 `static_cast` Operátor lze také provést žádné implicitní převod, včetně standardní převody a uživatelem definované převody. Příklad:  
  
```  
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
  
 `static_cast` Operátor můžete celočíselné hodnoty explicitně převést na typ výčtu. Pokud hodnota integrálního typu nespadá do rozsahu hodnot výčtu, výsledná hodnota výčtu není definována.  
  
 `static_cast` Operátor převede hodnotu ukazatele null. hodnota ukazatele null typu cílový.  
  
 Jakýkoli výraz možné explicitně převést na typ void pomocí `static_cast` operátor. Cílový typ void může volitelně obsahovat `const`, `volatile`, nebo `__unaligned` atribut.  
  
 `static_cast` Operátor nelze přetypovat rychle `const`, `volatile`, nebo `__unaligned` atributy. V tématu [const_cast – operátor](../cpp/const-cast-operator.md) informace o odebrání těchto atributů.  
  
 Z důvodu nebezpečí provedení nezaškrtnuté položky CAST v horní části relocating uvolňování paměti, použití `static_cast` by měly být jenom v kód kritický pro výkon když jste si jisti, bude správně fungovat. Pokud musíte použít `static_cast` v režimu vydání, nahraďte ho s [safe_cast](../windows/safe-cast-cpp-component-extensions.md) ve vašich sestaveních ladění k zajištění úspěšné.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)