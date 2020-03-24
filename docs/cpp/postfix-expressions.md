---
title: Výrazy přípony
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 25dfc6fd8f28f6c78fd5a4e9f76759ac076cae1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177687"
---
# <a name="postfix-expressions"></a>Výrazy přípony

Výrazy přípony jsou tvořeny primárními výrazy nebo výrazy, ve kterých příponové operátory následují za primárním výrazem. Příponové operátory jsou uvedeny v následující tabulce.

### <a name="postfix-operators"></a>Operátory přípony

|Název operátoru|Zápis operátoru|
|-------------------|-----------------------|
|[Operátor dolního indexu](../cpp/subscript-operator.md)|**[ ]**|
|[Operátor volání funkce](../cpp/function-call-operator-parens.md)|**( )**|
|[Operátor převodu explicitního typu](../cpp/explicit-type-conversion-operator-parens.md)|*název typu* **()**|
|[Operátor přístupu ke členu](../cpp/member-access-operators-dot-and.md)|**.** nebo **->**|
|[Operátor přírůstku přípony](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Operátor snížení přípony](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

Následující syntaxe popisuje možné výrazy přípony:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

Výše uvedený *výraz přípony* může být primární výraz nebo jiný výraz přípony.  Viz **Primary Expressions**.  Výrazy přípony se seskupují zleva doprava, takže umožňují následující řetězení výrazů:

```cpp
func(1)->GetValue()++
```

Ve výše uvedeném výrazu je `func` primární výraz, `func(1)` je výraz přípony funkce, `func(1)->GetValue` je výraz přípony určující člena třídy, `func(1)->GetValue()` je další výraz přípony funkce a celý výraz je příponový výraz, který zvyšuje návratovou hodnotu GetValue.  Význam výrazu jako celek je volání funkce func předávající hodnotu 1 jako argument a získání ukazatele na třídu jako návratové hodnoty.  Pak na tuto třídu zavolejte `GetValue()` a pak zvyšte hodnotu vrácenou.

Výrazy uvedené výše jsou výrazy přiřazení, což znamená, že výsledkem těchto výrazů musí být hodnota r-value.

Tvar výrazu přípony

```cpp
simple-type-name ( expression-list )
```

označuje volání konstruktoru.  Pokud je simple-type-name základní typ, musí být seznam výrazů jeden výraz a tento výraz označuje přetypování hodnoty výrazu na základní typ.  Tento typ výrazu přetypování napodobuje konstruktor.  Vzhledem k tomu, že tento tvar umožňuje základním typům a třídám, aby byly konstruovány pomocí stejné syntaxe, je tento tvar obzvláště užitečný při definování tříd šablon.

*Klíčové slovo cast-* je jedním z **dynamic_cast**, **static_cast** nebo **reinterpret_cast**.  Další informace lze nalézt v **dynamic_cast** **static_cast** a **reinterpet_cast**.

Operátor **typeid** je považován za výraz přípony.  Viz **Operátor typeid**.

## <a name="formal-and-actual-arguments"></a>Formální a skutečné argumenty

Volání programů předává volaným funkcím informace ve „skutečných argumentech“. Volané funkce přistupují k těmto informacím pomocí odpovídajících „formálních argumentů“.

Při volání funkce jsou provedeny následující úkoly:

- Jsou vyhodnoceny všechny skutečné argumenty (poskytnuté volajícím). Neexistuje žádné předpokládané pořadí, ve kterém jsou tyto argumenty vyhodnoceny, ale před vstupem do této funkce jsou vyhodnoceny všechny argumenty a dokončeny všechny vedlejší účinky.

- Každý formální argument je inicializován s jeho odpovídajícím skutečným argumentem v seznamu výrazů. (Formální argument je argument, který je deklarován v hlavičce funkce a použit v těle funkce.) Převody jsou provedeny jako při inicializaci – standardní i uživatelsky definované převody jsou prováděny při převodu skutečného argumentu na správný typ. Provedená inicializace je konceptuálně znázorněna následujícím kódem:

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

   Inicializace probíhá, jako kdyby byla použita syntaxe znaménka rovnosti namísto syntaxe se závorkami. Před předáním této hodnoty funkci je vytvořena kopie proměnné `i`. (Další informace naleznete v tématu [Inicializátory](../cpp/initializers.md) a [převody](../cpp/user-defined-type-conversions-cpp.md)).

   Proto pokud prototyp funkce (deklarace) volá argument typu **Long**a v případě, že volající program dodá skutečný argument typu **int**, je skutečný argument povýšen pomocí standardního převodu typu na typ **Long** (viz [standardní převody](../cpp/standard-conversions.md)).

   Poskytnutí skutečného argumentu, pro který neexistuje žádný standardní nebo uživatelem definovaný převod na typ formálního argumentu, vygeneruje chybu.

   Pro skutečné argumenty typu třídy je formální argument inicializován pomocí volání konstruktoru třídy. (Další informace o těchto speciálních členských funkcích třídy naleznete v tématu [konstruktory](../cpp/constructors-cpp.md) .)

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

Když je `func` volána z Main, je formální parametr `param1` inicializován s hodnotou `i` (`i` je převeden na typ **Long** , aby odpovídal správnému typu pomocí standardního převodu), a formální parametr `param2` je inicializován s hodnotou `j` (`j` je převedena na typ **Double** s použitím standardního převodu).

## <a name="treatment-of-argument-types"></a>Zpracování typů argumentů

Formální argumenty deklarované jako typy const nelze v těle funkce změnit. Funkce mohou změnit libovolný argument, který není typu **const**. Tato změna je však místní pro funkci a nemá vliv na hodnotu skutečného argumentu, pokud skutečný argument nebyl odkaz na objekt, který není typu **const**.

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

## <a name="ellipses-and-default-arguments"></a>Tři tečky a výchozí argumenty

Funkce mohou být deklarovány pro přijetí menšího počtu argumentů, než je zadáno v definici funkce, pomocí jedné ze dvou metod: tři tečky (`...`) nebo výchozí argumenty.

Tři tečky označují, že argumenty mohou být požadovány, ale že počet a typy nejsou v deklaraci zadány. To je obvykle špatný C++ způsob programování, protože se tím zachováním jedné z C++výhod: bezpečnost typů. Různé převody jsou aplikovány na funkce deklarované se třemi tečkami než na funkce, pro které jsou známé typy formální a skutečné argumenty:

- Pokud je skutečný argument typu **float**, je povýšen na typ **Double** před voláním funkce.

- Jakýkoli podepsaný nebo nepodepsaný **znak**, **krátký**, Výčtový typ nebo bitové pole je převeden na znaménko nebo unsigned **int** pomocí integrálního povýšení.

- Libovolný argument typu třídy je předán hodnotou jako datová struktura; kopie je vytvořena binárním kopírováním místo vyvoláním kopírovacího konstruktoru třídy (pokud existuje).

Tři tečky, pokud je použita, musí být deklarovány jako poslední v seznamu argumentů. Další informace o předání variabilního počtu argumentů naleznete v diskuzi o [va_arg, va_start a va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) v tématu *reference ke knihovně run-time*.

Informace o výchozích argumentech v programování CLR naleznete v tématu [proměnné seznamy argumentů (...)C++(/CLI)](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Výchozí argumenty umožňují zadat hodnotu, kterou by měl argument předpokládat, pokud není ve volání funkce žádná. Následující fragment kódu ukazuje, jak fungují výchozí argumenty. Další informace o omezeních zadání výchozích argumentů naleznete v tématu [Default arguments](../cpp/default-arguments.md).

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

Předchozí program deklaruje funkci, `print`, která přijímá dva argumenty. Nicméně druhý argument, *ukončovací*znak má výchozí hodnotu, `"\n"`. V `main`první dvě volání `print` umožňují výchozímu druhému argumentu poskytnout nový řádek pro ukončení vytištěného řetězce. Třetí volání určuje explicitní hodnotu pro druhý argument. Výstup programu je

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Viz také

[Typy výrazů](../cpp/types-of-expressions.md)
