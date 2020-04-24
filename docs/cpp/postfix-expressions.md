---
title: Výrazy přípony
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 897eb80c713f786ecf0f7e6c9cf24cd8bdfc0aa8
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032275"
---
# <a name="postfix-expressions"></a>Výrazy přípony

Výrazy přípony jsou tvořeny primárními výrazy nebo výrazy, ve kterých příponové operátory následují za primárním výrazem. Příponové operátory jsou uvedeny v následující tabulce.

### <a name="postfix-operators"></a>Operátory přípony

|Název operátoru|Zápis operátoru|
|-------------------|-----------------------|
|[Operátor dolního indexu](../cpp/subscript-operator.md)|**[ ]**|
|[Operátor volání funkce](../cpp/function-call-operator-parens.md)|**( )**|
|[Operátor převodu explicitního typu](../cpp/explicit-type-conversion-operator-parens.md)|*název typu* **( )**|
|[Operátor přístupu člena](../cpp/member-access-operators-dot-and.md)|**.** Nebo**->**|
|[Příponový operátor inkrementace](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Příponový operátor dekrementace](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

Následující syntaxe popisuje možné výrazy přípony:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

Výše uvedený *výraz přípony* může být primární výraz nebo jiný výraz přípony.  Viz **primární výrazy**.  Výrazy přípony se seskupují zleva doprava, takže umožňují následující řetězení výrazů:

```cpp
func(1)->GetValue()++
```

Ve výše uvedeném výrazu `func` `func(1)` je primární výraz, `func(1)->GetValue` je postfix výraz funkce, je postfix výraz určující člen třídy, `func(1)->GetValue()` je další funkce postfix výraz a celý výraz je postfix výraz zvýšení návratové hodnoty GetValue.  Význam výrazu jako celek je volání funkce func předávající hodnotu 1 jako argument a získání ukazatele na třídu jako návratové hodnoty.  Potom `GetValue()` volání této třídy, potom přírůstek vrácené hodnoty.

Výrazy uvedené výše jsou výrazy přiřazení, což znamená, že výsledkem těchto výrazů musí být hodnota r-value.

Tvar výrazu přípony

```cpp
simple-type-name ( expression-list )
```

označuje volání konstruktoru.  Pokud je simple-type-name základní typ, musí být seznam výrazů jeden výraz a tento výraz označuje přetypování hodnoty výrazu na základní typ.  Tento typ výrazu přetypování napodobuje konstruktor.  Vzhledem k tomu, že tento tvar umožňuje základním typům a třídám, aby byly konstruovány pomocí stejné syntaxe, je tento tvar obzvláště užitečný při definování tříd šablon.

Klíčové *slovo cast* je jedním z **dynamic_cast**, **static_cast** nebo **reinterpret_cast**.  Více informací naleznete v **dynamic_cast**, **static_cast** a **reinterpet_cast**.

Operátor **typeid** je považován za výraz přípony.  Viz **operátor typeid**.

## <a name="formal-and-actual-arguments"></a>Formální a skutečné argumenty

Volání programů předává volaným funkcím informace ve „skutečných argumentech“. Volané funkce přistupují k těmto informacím pomocí odpovídajících „formálních argumentů“.

Při volání funkce jsou provedeny následující úkoly:

- Jsou vyhodnoceny všechny skutečné argumenty (poskytnuté volajícím). Neexistuje žádné předpokládané pořadí, ve kterém jsou tyto argumenty vyhodnoceny, ale před vstupem do této funkce jsou vyhodnoceny všechny argumenty a dokončeny všechny vedlejší účinky.

- Každý formální argument je inicializován s jeho odpovídajícím skutečným argumentem v seznamu výrazů. (Formální argument je argument, který je deklarován v záhlaví funkce a použit v těle funkce.) Převody se provádějí jako inicializace – standardní i uživatelem definované převody se provádějí při převodu skutečného argumentu na správný typ. Provedená inicializace je konceptuálně znázorněna následujícím kódem:

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

   Inicializace probíhá, jako kdyby byla použita syntaxe znaménka rovnosti namísto syntaxe se závorkami. Před předáním této hodnoty funkci je vytvořena kopie proměnné `i`. (Další informace naleznete v tématu [Initializers](../cpp/initializers.md) and [Conversions](../cpp/user-defined-type-conversions-cpp.md)).

   Proto pokud prototyp funkce (deklarace) vyžaduje argument typu **long**a volající program poskytuje skutečný argument typu **int**, skutečný argument je povýšen pomocí standardního převodu typu na typ **long** (viz [Standardní převody](../cpp/standard-conversions.md)).

   Poskytnutí skutečného argumentu, pro který neexistuje žádný standardní nebo uživatelem definovaný převod na typ formálního argumentu, vygeneruje chybu.

   Pro skutečné argumenty typu třídy je formální argument inicializován pomocí volání konstruktoru třídy. (Další informace o těchto speciálních funkcích členů třídy naleznete v [tématu Konstruktory.)](../cpp/constructors-cpp.md)

- Je provedeno volání funkce.

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

Když `func` je volána z `param1` main, formální parametr `i` je`i` inicializován s hodnotou ( je převeden na typ `param2` **dlouhý,** aby odpovídal správnému typu pomocí standardního převodu) a formální parametr je inicializován s hodnotou `j` (`j` je převeden na typ **double** pomocí standardního převodu).

## <a name="treatment-of-argument-types"></a>Zacházení s typy argumentů

Formální argumenty deklarované jako typy const nelze v těle funkce změnit. Funkce můžete změnit libovolný argument, který není typu **const**. Změna je však místní funkce a nemá vliv na hodnotu skutečného argumentu, pokud skutečný argument nebyl odkazem na objekt, který není typu **const**.

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

## <a name="ellipsis-and-default-arguments"></a>Tři tečky a výchozí argumenty

Funkce lze deklarovat tak, že přijímají méně argumentů, než je`...`určeno v definici funkce, pomocí jedné ze dvou metod: tři tečky ( ) nebo výchozí argumenty.

Tři tečky označuje, že argumenty mohou být požadovány, ale že počet a typy nejsou zadány v deklaraci. To je obvykle špatné C++ programovací praxe, protože porazí jednu z výhod C++: bezpečnost typů. Různé převody se používají pro funkce deklarované třemi tečkami než na funkce, pro které jsou známy formální a skutečné typy argumentů:

- Pokud je skutečný argument typu **float**, je povýšen na typ **double** před volání funkce.

- Všechny podepsané nebo nepodepsané **znak**, **krátký**, výčtový typ nebo bitové pole jsou převedeny na podepsané nebo nepodepsané **int** pomocí integrální propagace.

- Každý argument typu třídy je předán hodnotou jako datová struktura; kopie je vytvořena binárníkopírování namísto vyvolání množiny třídy (pokud existuje).

Tři tečky, pokud jsou použity, musí být deklarovány jako poslední v seznamu argumentů. Další informace o předání proměnného počtu argumentů naleznete v diskusi o [va_arg, va_start a va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) v *odkazu na knihovnu za běhu*.

Informace o výchozích argumentech v programování CLR naleznete v [tématu Variable Argument Lists (...) (C++/CLI).](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)

Výchozí argumenty umožňují určit hodnotu, kterou by měl argument předpokládat, pokud není ve volání funkce zadánžádný. Následující fragment kódu ukazuje, jak fungují výchozí argumenty. Další informace o omezeních zadávání výchozích argumentů naleznete [v tématu Výchozí argumenty](../cpp/default-arguments.md).

```cpp
// expre_Ellipsis_and_Default_Arguments.cpp
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

Předchozí program deklaruje `print`funkci , která přebírá dva argumenty. Druhý argument, *zakončení*, má však výchozí hodnotu . `"\n"` V `main`, první dvě `print` volání povolit výchozí druhý argument zadat nový řádek ukončit tištěný řetězec. Třetí volání určuje explicitní hodnotu pro druhý argument. Výstup z programu je

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Viz také

[Typy výrazů](../cpp/types-of-expressions.md)
