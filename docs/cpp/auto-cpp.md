---
title: "Automatické (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6721aa5860f23025b8b6c762cc7e5f4d6178228d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="auto-c"></a>Automatické (C++)
Deduces typ deklarované proměnné z jeho inicializace výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## <a name="remarks"></a>Poznámky  
 `auto` Kompilátoru odvodit typ pomocí výrazu inicializace deklarované proměnné, nebo parametr výrazu lambda, přesměruje – klíčové slovo.  
  
 Doporučujeme vám, že používáte `auto` – klíčové slovo většině situací – Pokud chcete skutečně převodu z – protože poskytuje tyto výhody:  
  
-   **Robustnost:** dojde ke změně typu ve výrazu – to zahrnuje při změně návratový typ funkce – prostě funguje.  
  
-   **Výkon:** je zaručeno, že bude žádný převod.  
  
-   **Použitelnost:** nemusíte si dělat starosti o typ název pravopis problémy a překlepům.  
  
-   **Efektivita:** kódování může být efektivnější.  
  
 Převod případy, ve kterých není vhodné používat `auto`:  
  
-   Pokud chcete konkrétního typu a nic jiného provede.  
  
-   Typy výrazů šablony pomocná – například `(valarray+valarray)`.  
  
 Chcete-li použít `auto` – klíčové slovo, použijte místo typu deklarovat proměnnou a zadejte výraz inicializace. In addition, můžete upravit `auto` – klíčové slovo pomocí specifikátory a deklarátory například `const`, `volatile`, ukazatele (`*`), odkaz (`&`) a deklarátor odkazu hodnoty `(&&`). Kompilátor vyhodnotí výraz inicializace a pak používá tyto informace k odvodit typ proměnné.  
  
 Inicializace výraz může být přiřazení (znaménkem rovnosti syntaxe), přímý inicializace (funkce stylu syntaxe), [new – operátor](new-operator-cpp.md) může být výraz nebo výraz, který inicializace  *deklarace pro rozsah* parametr [na základě rozsahu pro příkaz (C++)](../cpp/range-based-for-statement-cpp.md) příkaz. Další informace najdete v tématu [inicializátory](../cpp/initializers.md) a ukázky kódu později v tomto dokumentu.  
  
 `auto` – Klíčové slovo je zástupný symbol pro typ, ale není samotného typu. Proto `auto` – klíčové slovo nelze použít v přetypování nebo operátory, jako [sizeof](../cpp/sizeof-operator.md) a [typeid](../windows/typeid-cpp-component-extensions.md).  
  
## <a name="usefulness"></a>Užitečnost  
 `auto` – Klíčové slovo je jednoduchý způsob, jak deklarovat proměnnou, která má složitý typ. Například můžete použít `auto` deklarovat proměnnou, pokud výraz inicializace zahrnuje šablony, ukazatelé na funkce nebo ukazatelé na členy.  
  
 Můžete také použít `auto` deklarovat a inicializovat proměnnou, do které výrazu lambda. Typ proměnné nelze deklarovat sami protože je jen pro kompilátor typ výrazu lambda. Další informace najdete v tématu [příklady výrazů Lambda](../cpp/examples-of-lambda-expressions.md).  
  
## <a name="trailing-return-types"></a>Koncové návratové typy  
 Můžete použít `auto`, společně s `decltype` specifikátor, abyste zápisu knihovny šablon typu. Použití `auto` a `decltype` deklarovat funkce šablony jejichž návratový typ závisí na typy argumentů šablony. Nebo použijte `auto` a `decltype` deklarovat funkci šablony, která zabalí volání jinou funkci a vrátí vše, co je návratový typ této funkce. Další informace najdete v tématu [decltype](../cpp/decltype-cpp.md).  
  
## <a name="references-and-cv-qualifiers"></a>Odkazy a kvalifikátory odchylka nákladů  
 Všimněte si, že pomocí `auto` zahodí odkazy, kvalifikátory const a volatile kvalifikátory. Podívejte se na následující příklad:  
  
```cpp  
// cl.exe /analyze /EHsc /W4  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
    int count = 10;  
    int& countRef = count;  
    auto myAuto = countRef;  
  
    countRef = 11;  
    cout << count << " ";  
  
    myAuto = 12;  
    cout << count << endl;  
}  
  
```  
  
 V předchozím příkladu myAuto je typ int, není odkaz na int, tak, aby výstup `11 11`, nikoli `11 12` jak by tomu bylo pokud kvalifikátor odkaz kdyby vyřazen `auto`.  
  
## <a name="type-deduction-with-braced-initializers-c14"></a>Odvození typu s braced inicializátory (C ++ 14)  
 Exmample následující kód ukazuje, jak inicializovat proměnná automaticky pomocí složené závorky. Všimněte si rozdílu mezi B a C a mezi A a E.  
  
```cpp  
#include <initializer_list>  
  
int main()  
{  
    // std::initializer_list<int>  
    auto A = { 1, 2 };  
  
    // std::initializer_list<int>  
    auto B = { 3 };  
  
    // int  
    auto C{ 4 };  
  
    // C3535: cannot deduce type for 'auto' from initializer list'  
    auto D = { 5, 6.7 };  
  
    // C3518 in a direct-list-initialization context the type for 'auto'  
    // can only be deduced from a single initializer expression  
    auto E{ 8, 9 };  
  
    return 0;  
}  
```  
  
## <a name="restrictions-and-error-messages"></a>Omezení a chybové zprávy  
 Následující tabulka uvádí omezení pro použití `auto` – klíčové slovo a odpovídající diagnostiky chybovou zprávu, která kompilátor vydává.  
  
|Číslo chyby|Popis|  
|------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|`auto` – Klíčové slovo nelze kombinovat s jakékoli jiné – specifikátor typu.|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol, který je deklarovaný s `auto` – klíčové slovo musí mít inicializátoru.|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Jste použili nesprávně `auto` – klíčové slovo deklarovat typ. Například deklarovat návratový typ. metoda nebo pole.|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Parametr nebo šablony argument nelze deklarovat s `auto` – klíčové slovo.|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Parametr metody nebo šablony nelze deklarovat s `auto` – klíčové slovo.|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Symbol nelze použít, před inicializací. V praxi to znamená, že proměnné nelze použít k chybě při inicializaci sám sebe.|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nelze přetypovat na typ, který je deklarovaný s `auto` – klíčové slovo.|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Všechny symboly deklarátor seznamu, který je deklarovaný s `auto` – klíčové slovo se musí přeložit stejného typu. Další informace najdete v tématu [deklarace a definice](declarations-and-definitions-cpp.md).|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md) a [typeid](../windows/typeid-cpp-component-extensions.md) operátory nelze použít na symbol, který je deklarovaný s `auto` – klíčové slovo.|  
  
## <a name="examples"></a>Příklady  
 Tyto fragmenty kódu ilustrovat některé z způsobů, ve kterém `auto` – klíčové slovo lze použít.  
  
 Následující deklarace jsou ekvivalentní. V prvním příkazu, proměnné `j` je deklarován jako typ `int`. V druhém příkazu, proměnné `k` není rozpoznán jako typ `int` protože inicializace výraz (0) je celé číslo.  
  
```cpp  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 Následující deklarace jsou ekvivalentní, ale druhý deklaraci je jednodušší než první. Jeden z nejvíce pádných důvodů pro použití `auto` – klíčové slovo je jednoduchost.  
  
```cpp  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 Následující fragment kódu deklaruje typ proměnné `iter` a `elem` při `for` a rozsah `for` cyklu start.  
  
```cpp  
// cl /EHsc /nologo /W4  
#include <deque>  
using namespace std;  
  
int main()  
{  
    deque<double> dqDoubleData(10, 0.1);  
  
    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)  
    { /* ... */ }  
  
    // prefer range-for loops with the following information in mind  
    // (this applies to any range-for with auto, not just deque)  
  
    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples  
    { /* ... */ }  
  
    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE  
    { /* ... */ }  
  
    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE  
    { /* ... */ }  
}  
```  
  
 Používá následující fragment kódu `new` operátor a ukazatel deklarace deklarovat ukazatele.  
  
```cpp  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 Následující fragment kódu deklaruje více symbolů v každém příkazu deklarace. Všimněte si, že všechny symboly v každý příkaz přeložit do stejného typu.  
  
```cpp  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 Podmíněný operátor používá tento fragment kódu (`?:`) deklarovat proměnnou `x` jako celé číslo, které má hodnotu 200:  
  
```cpp  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 Následující fragment kódu inicializuje proměnnou `x` na typ `int`, proměnné `y` na odkaz na typ `const int`a proměnnou `fp` na ukazatel na funkci, která vrátí typ `int`.  
  
```cpp  
int f(int x) { return x; }  
int main()  
{  
    auto x = f(0);  
    const auto & y = f(1);  
    int (*p)(int x);  
    p = f;  
    auto fp = p;  
    //...  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../cpp/auto-keyword.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [/ Zc: Auto (odvození typu proměnné)](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof – operátor](../cpp/sizeof-operator.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)   
 [new – operátor](new-operator-cpp.md)   
 [Deklarace a definice](declarations-and-definitions-cpp.md)   
 [Příklady výrazů Lambda](../cpp/examples-of-lambda-expressions.md)   
 [Inicializátory](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)