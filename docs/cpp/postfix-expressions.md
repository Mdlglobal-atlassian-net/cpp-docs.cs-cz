---
title: "Výrazy přípony | Microsoft Docs"
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
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b965027e67cc2b2581c2ab00e51d2be7a899302
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="postfix-expressions"></a>Výrazy přípony
Výrazy přípony jsou tvořeny primárními výrazy nebo výrazy, ve kterých příponové operátory následují za primárním výrazem. Příponové operátory jsou uvedeny v následující tabulce.  
  
### <a name="postfix-operators"></a>Operátory přípony  
  
|Název operátoru|Zápis operátoru|  
|-------------------|-----------------------|  
|[Operátor dolního indexu](../cpp/subscript-operator.md)|**[ ]**|  
|[Operátor volání funkce](../cpp/function-call-operator-parens.md)|**( )**|  
|[Operátor převodu explicitního typu](../cpp/explicit-type-conversion-operator-parens.md)|*Název typu* **)**|  
|[Operátor přístupu členů](../cpp/member-access-operators-dot-and.md)|**.** nebo**->**|  
|[Operátory přírůstku operátor](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[Operátor snížení přípony](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|  
  
 Následující syntaxe popisuje možné výrazy přípony:  
  
```  
  
      primary-expression   
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )  
```  
  
 *Operátory výraz* vyšší může být výraz na primární nebo jiné operátory výraz.  V tématu **primární výrazy**.  Výrazy přípony se seskupují zleva doprava, takže umožňují následující řetězení výrazů:  
  
```  
func(1)->GetValue()++  
```  
  
 Ve výše uvedeném výrazu je func primární výraz, func(1) je výraz přípony funkce, func(1)->GetData je výraz přípony určující člena třídy, func(1)->GetData() je jiný výraz přípony funkce a celý výraz je výraz přípony zvyšující návratovou hodnotu funkce GetData.  Význam výrazu jako celek je volání funkce func předávající hodnotu 1 jako argument a získání ukazatele na třídu jako návratové hodnoty.  Pak následuje volání funkce GetValue() dané třídy a poté zvýšení vrácené hodnoty.  
  
 Výrazy uvedené výše jsou výrazy přiřazení, což znamená, že výsledkem těchto výrazů musí být hodnota r-value.  
  
 Tvar výrazu přípony  
  
```  
simple-type-name ( expression-list )  
```  
  
 označuje volání konstruktoru.  Pokud je simple-type-name základní typ, musí být seznam výrazů jeden výraz a tento výraz označuje přetypování hodnoty výrazu na základní typ.  Tento typ výrazu přetypování napodobuje konstruktor.  Vzhledem k tomu, že tento tvar umožňuje základním typům a třídám, aby byly konstruovány pomocí stejné syntaxe, je tento tvar obzvláště užitečný při definování tříd šablon.  
  
 *Cast – klíčové slovo* je jedním z `dynamic_cast`, `static_cast` nebo `reinterpret_cast`.  Další informace naleznete v **dynamic_cast**, **static_cast** a **reinterpet_cast**.  
  
 Operátor `typeid` se považuje za výraz přípony.  V tématu **typeid – operátor**.  
  
## <a name="formal-and-actual-arguments"></a>Formální a aktuální argumenty  
 Volání programů předává volaným funkcím informace ve „skutečných argumentech“. Volané funkce přistupují k těmto informacím pomocí odpovídajících „formálních argumentů“.  
  
 Při volání funkce jsou provedeny následující úkoly:  
  
-   Jsou vyhodnoceny všechny skutečné argumenty (poskytnuté volajícím). Neexistuje žádné předpokládané pořadí, ve kterém jsou tyto argumenty vyhodnoceny, ale před vstupem do této funkce jsou vyhodnoceny všechny argumenty a dokončeny všechny vedlejší účinky.  
  
-   Každý formální argument je inicializován s jeho odpovídajícím skutečným argumentem v seznamu výrazů. (Formální argument je argument, který je deklarován v hlavičce funkce a použit v těle funkce.) Jsou provedeny převody jako při inicializaci, jsou provedeny standardní i uživatelem definované převody a skutečný argument je převeden na správný typ. Provedená inicializace je konceptuálně znázorněna následujícím kódem:  
  
    ```  
    void Func( int i ); // Function prototype  
    ...  
    Func( 7 );          // Execute function call  
    ```  
  
     Konceptuální inicializace provedené před voláním jsou:  
  
    ```  
    int Temp_i = 7;  
    Func( Temp_i );  
    ```  
  
     Inicializace probíhá, jako kdyby byla použita syntaxe znaménka rovnosti namísto syntaxe se závorkami. Před předáním této hodnoty funkci je vytvořena kopie proměnné `i`. (Další informace najdete v tématu [inicializátory](../cpp/initializers.md) a [převody](../cpp/user-defined-type-conversions-cpp.md)).  
  
     Proto pokud prototyp funkce (deklarace) vyžaduje argument typu **dlouho**, a pokud volací program zadává skutečného argument typu `int`, skutečný argument je povýší pomocí standardní typ převodu na typ **dlouho** (viz [standardní převody](../cpp/standard-conversions.md)).  
  
     Poskytnutí skutečného argumentu, pro který neexistuje žádný standardní nebo uživatelem definovaný převod na typ formálního argumentu, vygeneruje chybu.  
  
     Pro skutečné argumenty typu třídy je formální argument inicializován pomocí volání konstruktoru třídy. (Viz [konstruktory](../cpp/constructors-cpp.md) Další informace o těchto třída speciální členské funkce.)  
  
-   Je provedeno volání funkce.  
  
 Následující fragment programu znázorňuje volání funkce:  
  
```  
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
  
 Když `func` je volána z hlavní formální parametr `param1` je inicializován s hodnotou `i` (`i` je převést na typ **dlouho** tak, aby odpovídaly správného typu pomocí standard převod) a typ formálního parametru `param2` je inicializován s hodnotou `j` (`j` je převést na typ **dvojité** pomocí standardní převod).  
  
## <a name="treatment-of-argument-types"></a>Zacházení s typy argumentů  
 Formální argumenty deklarované jako typy const nelze v těle funkce změnit. Funkce můžete změnit některý argument, který není typu **const**. Však změnu je místní pro funkci a neovlivní skutečné argument hodnotu, pokud skutečné argument měl odkaz na objekt není typu **const**.  
  
 Následující funkce znázorňují některé z těchto konceptů:  
  
```  
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
 Funkce lze deklarovat tak, aby přijímal argumenty méně než zadaný v definici funkce, pomocí jedné ze dvou způsobů: třemi tečkami (`...`) nebo výchozí argumenty.  
  
 Tři tečky označují, že argumenty může být nutný, ale, že počet a typy nejsou zadaný v deklaraci. To je obvykle nízký C++ programovací praxí, protože ji účinně chrání před jednou z výhod C++: typ zabezpečení. Jiné převody se používají k funkcím deklarovat s výpustky než na tyto funkce, pro které jsou známé typy argumentů formální a aktuální:  
  
-   Pokud je argumentem skutečný typ **float**, je povýšit na typ **dvojité** před volání funkce.  
  
-   Všechny podepsané nebo bez znaménka `char`, **krátké**, výčtový typ nebo bitová pole jsou převedeny na přihlášeni nebo nepodepsaný `int` integrální povýšení.  
  
-   Některý argument typu třídy je předaná hodnota jako datové struktury; kopie se vytvoří tak, že zkopírujete binární místo vyvoláním konstruktoru třídy kopírování (pokud existuje).  
  
 Tři tečky, pokud se používá, musí být deklarován poslední v seznamu argumentů. Další informace o předávání proměnný počet argumentů, přečtěte si diskuzi o [va_arg –, va_start – a VA_LIST –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) v *referenční dokumentace běhové knihovny*.  
  
 Informace o výchozí argumenty v CLR – programování v tématu [proměnné seznamy argumentů (...) (C + +/ CLI) ](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
 Výchozí argumenty umožňují zadat hodnotu, kterou argument musí předpokládat, pokud žádný je zadaný ve volání funkce. Následující fragment kódu ukazuje, jak fungují výchozí argumenty. Další informace o omezeních k zadávání výchozí argumenty najdete v tématu [výchozí argumenty](../cpp/default-arguments.md).  
  
```  
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
  
 Předchozí program deklaruje funkci, `print`, která má dva argumenty. Ale druhý argument, `terminator`, nemá výchozí hodnotu `"\n"`. V **hlavní**, první dva volání `print` povolit výchozí druhý argument zadat nový řádek ukončit tištěných řetězec. Třetí volání určuje explicitní hodnotu pro druhý argument. Výstup z programu  
  
```  
hello,  
world!  
good morning, sunshine.  
```  
  
## <a name="see-also"></a>Viz také  
 [Typy výrazů](../cpp/types-of-expressions.md)