---
title: decltype (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decltype_cpp
dev_langs: C++
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee3c83512929e4592a5ee75b954bc6c19f52f448
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="decltype--c"></a>decltype (C++)
Specifikátor typu `decltype` vrací typ zadaného výrazu. `decltype` Zadejte specifikátor, společně s [auto – klíčové slovo](../cpp/auto-cpp.md), je užitečné především pro vývojáře, kteří vytvářejí knihovny šablon. Použití `auto` a `decltype` deklarovat funkce šablony jejichž návratový typ závisí na typy argumentů šablony. Nebo lze klíčová slova `auto` a `decltype` použít k deklarování šablony funkce, která zaobaluje volání další funkce, a potom vrátí návratový typ volané funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
decltype( expression )  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`expression`|Výraz. Další informace najdete v tématu [výrazy](../cpp/expressions-cpp.md).|  
  
## <a name="return-value"></a>Návratová hodnota  
 Typ parametru `expression`.  
  
## <a name="remarks"></a>Poznámky  
 Specifikátor typu `decltype` je podporován v jazyce Visual C++ 2010 nebo novější verzi a lze jej použít s nativním nebo spravovaným kódem. `decltype(auto)`(C ++ 14) jsou podporovány v sadě Visual Studio 2015 a vyšší.  
  
 Kompilátor používá následující pravidla pro určení typu parametru `expression`.  
  
-   Pokud `expression` parametr je identifikátor nebo [třídy přístup ke členu](../cpp/member-access-operators-dot-and.md), `decltype(expression)` je typ entity s názvem podle `expression`. Pokud není žádná taková entita nebo parametr `expression` vyjmenovává sadu přetížených funkcí, vrátí kompilátor chybovou zprávu.  
  
-   Pokud `expression` parametr je volání funkce nebo funkce přetížené operátor, `decltype(expression)` je návratový typ funkce. Závorky kolem přetíženého operátoru jsou ignorovány.  
  
-   Pokud `expression` parametr [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` je typ `expression`. Pokud `expression` parametr [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` je [odkazu lvalue](../cpp/lvalue-reference-declarator-amp.md) typu `expression`.  
  
 Následující příklad kódu ukazuje některá použití specifikátoru typu `decltype`. Nejprve předpokládejme, že jste nakódovali následující příkazy.  
  
```cpp  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 Dále zkontrolujte typy, které jsou vráceny pomocí čtyř příkazů `decltype` v následující tabulce.  
  
|Příkaz|Typ|Poznámky|  
|---------------|----------|-----------|  
|`decltype(fx());`|`const int&&`|[Deklarátor odkazu hodnoty](../cpp/rvalue-reference-declarator-amp-amp.md) k `const int`.|  
|`decltype(var);`|`int`|Typ proměnné `var`.|  
|`decltype(a->x);`|`double`|Typ přístupu členu.|  
|`decltype((a->x));`|`const double&`|Vnitřní závorky způsobí, že je příkaz vyhodnocen jako výraz namísto přístupu ke členu. A protože je proměnná `a` deklarována jako ukazatel `const`, je tento typ ukazatelem na typ `const double`.|  
  
## <a name="decltype-and-auto"></a>Klíčová slova Decltype a Auto  
 V C ++ 14, můžete použít `decltype(auto)` s žádné koncové návratový typ deklarovat s návratovým typem funkce šablony závisí na typech argumentů šablony.  
  
 V C ++ 11, můžete použít `decltype` specifikátor na konci návratový typ typu společně s `auto` – klíčové slovo deklarovat s návratovým typem funkce šablony závisí na typech argumentů šablony. Zvažte například následující příklad kódu, ve kterém návratový typ šablony funkce závisí na typech šablony argumentů. V příkladu kódu *neznámé* zástupný text označuje, že návratový typ nelze zadat.  
  
```cpp  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 Použití specifikátoru typu `decltype` umožňuje vývojáři získat typ výrazu, který šablona funkce vrátí. Použití *syntax deklarace funkce alternativní* , se zobrazí později, `auto` – klíčové slovo a `decltype` specifikátor deklarovat typu *pozdní zadaný* návratový typ. Pozdně určený návratový typ je určen při kompilaci deklarace, nikoli když je kódován.  
  
 Následující prototyp znázorňuje syntaxi alternativní deklarace funkce. Všimněte si, že `const` a `volatile` kvalifikátory a `throw` [specifikace výjimek](../cpp/exception-specifications-throw-cpp.md) jsou volitelné. *Function_body* zástupný symbol představuje složený příkaz, který určuje, jaké funkce. Jako nejvhodnější, zvykem *výraz* zástupný symbol v `decltype` příkaz by měl odpovídat výrazu určeného `return` příkaz, pokud existuje, v *function_body*.  
  
 **Automatické** *Název_funkce* **(** *parametry*<sub>opt</sub> **)**  **Const**<sub>opt</sub> **volatile**<sub>opt</sub>  **->**  **decltype (** *výraz* **)** **throw**<sub>opt</sub> **{** *function_body* **};**  
  
 V následujícím příkladu kódu je pozdně zadaný návratový typ šablony funkce `myFunc` určen pomocí typů `t` a `u` šablony argumentů. Jako nejvhodnější, zvykem, příklad kódu používá také odkazy rvalue a `forward` funkce šablony, která podporují *ideální předávání*. Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
```cpp  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## <a name="decltype-and-forwarding-functions-c11"></a>Decltype a předávání funkce (C ++ 11)  
 Funkce předávání zaobalují volání dalších funkcí. Zvažte šablonu funkce, která předává své argumenty nebo výsledky výrazu, který zahrnuje tyto argumenty, jiné funkci. Kromě toho funkce předávání vrátí výsledek volání další funkce. V tomto scénáři by měl návratový typ funkce předávání být stejný jako návratový typ zabalené funkce.  
  
 V tomto scénáři nelze odpovídající typ výrazu zapsat bez specifikátoru typu `decltype`. Specifikátor typu `decltype` umožňuje obecné funkce předávání, protože neztratí potřebné informace o tom, zda funkce vrací odkaz. Příklad kódu funkce předávání naleznete v předchozím příkladu šablony funkce `myFunc`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu deklaruje pozdně zadaný návratový typ šablony funkce `Plus()`. Funkce `Plus` zpracuje své dva operandy s přetížením `operator+`. V důsledku toho interpretace operátoru plus (+) a návratový typ funkce `Plus` závisí na typech argumentů funkce.  
  
```cpp  
// decltype_1.cpp  
// compile with: cl /EHsc decltype_1.cpp  
  
#include <iostream>  
#include <string>  
#include <utility>  
#include <iomanip>  
  
using namespace std;  
  
template<typename T1, typename T2>  
auto Plus(T1&& t1, T2&& t2) ->   
   decltype(forward<T1>(t1) + forward<T2>(t2))  
{  
   return forward<T1>(t1) + forward<T2>(t2);  
}  
  
class X  
{  
   friend X operator+(const X& x1, const X& x2)  
   {  
      return X(x1.m_data + x2.m_data);  
   }  
  
public:  
   X(int data) : m_data(data) {}  
   int Dump() const { return m_data;}  
private:  
   int m_data;  
};  
  
int main()  
{  
   // Integer   
   int i = 4;  
   cout <<   
      "Plus(i, 9) = " <<   
      Plus(i, 9) << endl;  
  
   // Floating point  
   float dx = 4.0;  
   float dy = 9.5;  
   cout <<     
      setprecision(3) <<   
      "Plus(dx, dy) = " <<  
      Plus(dx, dy) << endl;  
  
   // String        
   string hello = "Hello, ";  
   string world = "world!";  
   cout << Plus(hello, world) << endl;  
  
   // Custom type  
   X x1(20);  
   X x2(22);  
   X x3 = Plus(x1, x2);  
   cout <<   
      "x3.Dump() = " <<   
      x3.Dump() << endl;  
}  
```  
  
```Output  
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```
  
## <a name="example"></a>Příklad
**Visual Studio 2017 a novější:** kompilátor analyzuje decltype argumenty při šablony jsou deklarovaný místo vytvoření instance. V důsledku toho pokud nezávislých specializace najde v argumentu decltype, je termín, vytváření instancí čas a bude zpracován okamžitě a případné chyby bude zjištěna v daném čase.

Následující příklad ukazuje takové chybu kompilátoru, která se vyvolá v místě deklarace:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Požadavky  
 Jazyk Visual C++ 2010 nebo novější verze.  
  
 `decltype(auto)`vyžaduje Visual Studio 2015 nebo novější.  
  
