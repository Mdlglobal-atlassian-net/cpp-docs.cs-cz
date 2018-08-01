---
title: Výrazy přípony | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a951c45da8c5c6b672540c03bc1d97b5d54d9338
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403138"
---
# <a name="postfix-expressions"></a>Výrazy přípony
Výrazy přípony jsou tvořeny primárními výrazy nebo výrazy, ve kterých příponové operátory následují za primárním výrazem. Příponové operátory jsou uvedeny v následující tabulce.  
  
### <a name="postfix-operators"></a>Operátory přípony  
  
|Název operátoru|Zápis operátoru|  
|-------------------|-----------------------|  
|[Operátor dolního indexu](../cpp/subscript-operator.md)|**[ ]**|  
|[Operátor volání funkce](../cpp/function-call-operator-parens.md)|**( )**|  
|[Operátor převodu explicitního typu](../cpp/explicit-type-conversion-operator-parens.md)|*Název typu* **)**|  
|[Operátor přístupu členů](../cpp/member-access-operators-dot-and.md)|**.** Nebo **->**|  
|[Příponový operátor Inkrementace](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|  
|[Příponový operátor dekrementace](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|  
  
 Následující syntaxe popisuje možné výrazy přípony:  
  
```  
primary-expression   
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )  
```  
  
 *Postfix-expression* uvedený výše může být primární výraz nebo jiný výraz přípony.  Zobrazit **primární výrazy**.  Výrazy přípony se seskupují zleva doprava, takže umožňují následující řetězení výrazů:  
  
```cpp 
func(1)->GetValue()++  
```  
  
 Ve výše uvedeném výrazu `func` je primární výraz `func(1)` je výraz přípony funkce `func(1)->GetData` je výraz přípony určující člena třídy, `func(1)->GetData()` je jiný výraz přípony funkce a celý výraz je výraz přípony zvyšující návratovou hodnotu funkce GetData.  Význam výrazu jako celek je volání funkce func předávající hodnotu 1 jako argument a získání ukazatele na třídu jako návratové hodnoty.  Poté zavolejte `GetValue()` dané třídy, poté zvýšení vrácené hodnoty.  
  
 Výrazy uvedené výše jsou výrazy přiřazení, což znamená, že výsledkem těchto výrazů musí být hodnota r-value.  
  
 Tvar výrazu přípony  
  
```cpp 
simple-type-name ( expression-list )  
```  
  
 označuje volání konstruktoru.  Pokud je simple-type-name základní typ, musí být seznam výrazů jeden výraz a tento výraz označuje přetypování hodnoty výrazu na základní typ.  Tento typ výrazu přetypování napodobuje konstruktor.  Vzhledem k tomu, že tento tvar umožňuje základním typům a třídám, aby byly konstruovány pomocí stejné syntaxe, je tento tvar obzvláště užitečný při definování tříd šablon.  
  
 *Cast-keyword* je jedním z **dynamic_cast**, **static_cast** nebo **reinterpret_cast**.  Další informace lze nalézt v **dynamic_cast**, **static_cast** a **reinterpet_cast**.  
  
 **Typeid** operátor se považuje za výraz přípony.  Zobrazit **operátor typeid**.  
  
## <a name="formal-and-actual-arguments"></a>Formální a aktuální argumenty  
 Volání programů předává volaným funkcím informace ve „skutečných argumentech“. Volané funkce přistupují k těmto informacím pomocí odpovídajících „formálních argumentů“.  
  
 Při volání funkce jsou provedeny následující úkoly:  
  
-   Jsou vyhodnoceny všechny skutečné argumenty (poskytnuté volajícím). Neexistuje žádné předpokládané pořadí, ve kterém jsou tyto argumenty vyhodnoceny, ale před vstupem do této funkce jsou vyhodnoceny všechny argumenty a dokončeny všechny vedlejší účinky.  
  
-   Každý formální argument je inicializován s jeho odpovídajícím skutečným argumentem v seznamu výrazů. (Formální argument je argument, který je deklarován v hlavičce funkce a použit v těle funkce.) Jsou provedeny převody jako při inicializaci, jsou provedeny standardní i uživatelem definované převody a skutečný argument je převeden na správný typ. Provedená inicializace je konceptuálně znázorněna následujícím kódem:  
  
    ```cpp 
    void Func( int i ); // Function prototype  
    ...  
    Func( 7 );          // Execute function call  
    ```  
  
     Konceptuální inicializace provedené před voláním jsou:  
  
    ```cpp 
    int Temp_i = 7;  
    Func( Temp_i );  
    ```  
  
     Inicializace probíhá, jako kdyby byla použita syntaxe znaménka rovnosti namísto syntaxe se závorkami. Před předáním této hodnoty funkci je vytvořena kopie proměnné `i`. (Další informace najdete v tématu [inicializátory](../cpp/initializers.md) a [převody](../cpp/user-defined-type-conversions-cpp.md)).  
  
     Proto pokud prototyp funkce (deklarace) vyžaduje argument typu **dlouhé**, a pokud volající program poskytne skutečný argument typu **int**, je skutečný argument povýšen pomocí Převod standardního typu na typ **dlouhé** (viz [standardní převody](../cpp/standard-conversions.md)).  
  
     Poskytnutí skutečného argumentu, pro který neexistuje žádný standardní nebo uživatelem definovaný převod na typ formálního argumentu, vygeneruje chybu.  
  
     Pro skutečné argumenty typu třídy je formální argument inicializován pomocí volání konstruktoru třídy. (Viz [konstruktory](../cpp/constructors-cpp.md) Další informace o těchto speciálních členských funkcích třídy.)  
  
-   Je provedeno volání funkce.  
  
 Následující fragment programu znázorňuje volání funkce:  
  
```cpp 
// expre_Formal_and_Actual_Arguments.cpp  
void func( long param1, double param2 );  
  
int main()  
{  
    long i = 1;  
    double j = 2;  
  
    // Call func with actual arguments i and j.  
    func( i, j );  
}  
  
// Define func with formal parameters param1 and param2.  
void func( long param1, double param2 )  
{  
}  
```  
  
 Když `func` je volána z hlavní, formální parametr `param1` je inicializován s hodnotou `i` (`i` je převeden na typ **dlouhé** tak, aby odpovídaly správný typ použití standardního převod) a formální parametr `param2` je inicializován s hodnotou `j` (`j` je převeden na typ **double** pomocí standardního převodu).  
  
## <a name="treatment-of-argument-types"></a>Zacházení s typy argumentů  
 Formální argumenty deklarované jako typy const nelze v těle funkce změnit. Funkce mohou změnit jakýkoliv argument, který není typu **const**. Ale tato změna je místní pro funkci a nemá vliv skutečnou hodnotu argumentu není-li skutečný argument nebyl odkazem na objekt není typu **const**.  
  
 Následující funkce znázorňují některé z těchto konceptů:  
  
```cpp 
// expre_Treatment_of_Argument_Types.cpp  
int func1( const int i, int j, char *c ) {  
   i = 7;   // C3892 i is const.  
   j = i;   // value of j is lost at return  
   *c = 'a' + j;   // changes value of c in calling function  
   return i;  
}  
  
double& func2( double& d, const char *c ) {  
   d = 14.387;   // changes value of d in calling function.  
   *c = 'a';   // C3892 c is a pointer to a const object.  
    return d;  
}  
```  
  
## <a name="ellipses-and-default-arguments"></a>Výpustky a výchozí argumenty  
 Funkce mohou být deklarovány pro přijmutí méně argumentů, než je určeno v definici funkce, pomocí dvou metod: tři tečky (`...`) nebo výchozí argumenty.  
  
 Symbol tří teček označuje, že argumenty mohou být požadovány, ale že počet a typy nejsou uvedené v deklaraci. Toto je obvykle nedostatečná praxe programování v C++, protože to anuluje jednu z výhod typu jazyka C++: bezpečnost typů. Různé konverze se použijí na funkce deklarované s elipsami spíše než s těmito funkcemi, u kterých formální a skutečné typy argumentů jsou známé:  
  
-   Pokud je skutečný argument typu **float**, je povýšen na typ **double** před voláním funkce.  
  
-   Všechny podepsané nebo nepodepsané **char**, **krátký**, výčtový typ nebo bitové pole budou převedeny na podepsaný nebo nepodepsaný **int** pomocí integrální propagace.  
  
-   Některý argument typu třídy je předán podle hodnoty jako datová struktura; kopie je vytvořena binárním kopírováním namísto vyvoláním konstruktoru třídy kopie (pokud existuje).  
  
 Symbol tří teček, pokud se používá, musí být deklarován poslední v seznamu argumentů. Další informace o předávání proměnný počet argumentů, najdete v diskuzi o [va_arg, va_start a va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) v *Run-Time Library Reference*.  
  
 Informace o výchozích argumentech v CLR programování naleznete v tématu [seznamy argumentů proměnných (...) (C + +/ CLI) ](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
 Výchozí argumenty umožňují zadat hodnotu, kterou by měl předpokládat argument, pokud žádná není zadána ve volání funkce. Následující fragment kódu ukazuje, jak pracuje výchozí argument. Další informace o omezeních na určení výchozích argumentů naleznete v tématu [výchozí argumenty](../cpp/default-arguments.md).  
  
```cpp 
// expre_Ellipses_and_Default_Arguments.cpp  
// compile with: /EHsc  
#include <iostream>  
  
// Declare the function print that prints a string,  
// then a terminator.  
void print( const char *string,  
            const char *terminator = "\n" );  
  
int main()  
{  
    print( "hello," );  
    print( "world!" );  
  
    print( "good morning", ", " );  
    print( "sunshine." );  
}  
  
using namespace std;  
// Define print.  
void print( const char *string, const char *terminator )  
{  
    if( string != NULL )  
        cout << string;  
  
    if( terminator != NULL )  
        cout << terminator;  
}  
```  
  
 Předchozí program deklaruje funkci `print`, která přijímá dva argumenty. Nicméně druhý argument, *ukončovací znak*, má výchozí hodnotu, `"\n"`. V `main`, první dvě volání na `print` umožňují výchozímu druhému argumentu dodat novému řádku ukončení tištěného řetězce. Třetí volání určuje explicitní hodnotu pro druhý argument. Zobrazí se výstup z programu  
  
```Output 
hello,  
world!  
good morning, sunshine.  
```  
  
## <a name="see-also"></a>Viz také:  
 [Typy výrazů](../cpp/types-of-expressions.md)