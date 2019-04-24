---
title: '&lt;funkční&gt;'
ms.date: 02/21/2019
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
ms.openlocfilehash: 317344db856a7a0568aca422ecfe8280b80db097
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159415"
---
# <a name="ltfunctionalgt"></a>&lt;funkční&gt;

Definuje funkce standardní knihovny C++, které pomáhají při vytváření *objekty funkce*, označované také jako *funktory*a jejich vazačů. Objekt funkce je objekt typu, který definuje `operator()`. Objekt funkce může být ukazatel na funkci, ale častěji tento objekt slouží k ukládání dalších informací, ke kterým lze získat přístup během volání funkce.

## <a name="syntax"></a>Syntaxe

```cpp
#include <functional>
```

## <a name="remarks"></a>Poznámky

Algoritmy vyžadují dva druhy objektů funkce: *unární* a *binární*. Jednočlenné objekty funkce vyžadují jeden argument a binární objekty funkce vyžadují dva argumenty. Objekt funkce a ukazatelů na funkce lze předat jako predikát algoritmus, ale objekty funkce jsou také přizpůsobivé a zvýšit rozsah, flexibilitu a efektivitu standardní knihovny C++. Například, pokud potřebná hodnota musí být navázána na funkci před předáním algoritmu, nelze ukazatel na funkci použít. Adaptéry funkce převádějí ukazatele na funkci na přizpůsobitelné objekty funkce, které lze navázat na hodnotu. Záhlaví \<funkční > také obsahuje adaptéry členské funkce, které umožňují členské funkce, která se má volat jako přizpůsobitelné objekty funkce. Funkce jsou přizpůsobitelné, pokud obsahují deklarace vnořených typů určující jejich argumenty a návratové typy. Objekty funkcí a jejich adaptéry umožňují upgrade existujících aplikací a pomáhají integrovat knihovnu do programovacího prostředí jazyka C++ standardní knihovny C++.

Implementace objektů funkce v \<funkční > obsahuje *transparentní funktory operátorů*. což jsou specializované standardní funkci objektů a nepřebírající žádné parametry šablony a provádět dokonalé předávání argumentů funkce a dokonalé vrácení výsledku. Tyto specializace šablony nevyžadují určení typů argumentu při vyvolání aritmetických, relačních, logických a bitových operátorů funktorů. Lze přetěžovat aritmetické, relační, logické a bitové operátory vlastních typů nebo heterogenní kombinace typů, a potom použít funktory transparentního operátoru jako argumenty funkce. Například pokud váš typ *MyType* implementuje `operator<`, můžete volat `sort(my_collection.begin(), my_collection.end(), less<>())` namísto explicitního určení typu `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.

V C ++ 11, C ++ 14 a C ++ 17 jsou přidány následující funkce:

- A *signatura volání* je název návratového typu následovaného seznamem oddělených čárkou v závorkách nula nebo více typů argumentů.

- A *volatelného typu* je ukazatel na funkci, ukazatel na členskou funkci, ukazatel na členská data nebo typ třídy, jejichž objekty se mohou zobrazit bezprostředně nalevo od operátoru volání funkce.

- A *volatelný objekt* je objekt volatelného typu.

- A *typ obálky volání* je typ, který uchovává volatelný objekt a podporuje operaci volání, které přeposílá požadavky do tohoto objektu.

- A *Obálka volání* je objekt typu obálky volání.

- A *cílový objekt* je volatelný objekt uchovaný objektem obálky volání.

Pseudofunkcí `INVOKE(f, t1, t2, ..., tN)` se rozumí jedna z následujících možností:

- `(t1.*f)(t2, ..., tN)` Když `f` je ukazatel na členskou funkci třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z `T`.

- `((*t1).*f)(t2, ..., tN)` Když `f` je ukazatel na členskou funkci třídy `T` a `t1` není jedním z typů uvedených v předchozí položce.

- `t1.*f` Když N == 1 a `f` je ukazatel na členská data třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z `T`.

- `(*t1).*f` Když N == 1 a `f` je ukazatel na členská data třídy `T` a `t1` není jedním z typů uvedených v předchozí položce.

- `f(t1, t2, ..., tN)` ve všech ostatních případech.

Pseudofunkce `INVOKE(f, t1, t2, ..., tN, R)` znamená `INVOKE(f, t1, t2, ..., tN)` implicitně převedenou na `R`.

Pokud má obálka volání *slabý typ výsledku*, typ jeho členského typu `result_type` je založená na typu `T` cílového objektu obálky následujícím způsobem:

- Pokud je `T` ukazatel na funkci, je `result_type` synonymem návratového typu `T`.

- Pokud je `T` ukazatel na členskou funkci, je `result_type` synonymem návratového typu `T`.

- Pokud je `T` typ třídy, která obsahuje typ členu `result_type`, pak je `result_type` synonymem pro `T::result_type`.

- Jinak neexistuje žádný člen `result_type`.

Každá obálka volání má konstruktor přesunutí a konstruktor kopírování. A *jednoduchou obálku volání* je obálka volání obsahující operátor a jehož kopírovací konstruktor, konstruktor přesunutí a operátor přiřazení nevyvolají výjimky přiřazení. A *Obálka předání volání* je obálka volání, kterou lze volat pomocí libovolného seznamu argumentů a která přenáší tyto argumenty zkomprimovaným volatelným objektům jako reference. Všechny argumenty r-hodnot jsou dodávány jako odkazy r-hodnot a argumenty l-hodnot jsou dodávány jako odkazy l-hodnot.

## <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[bad_function_call](../standard-library/bad-function-call-class.md)|Třída, která popisuje vyvolanou výjimku k označení, že volání `operator()` na [funkce](../standard-library/function-class.md) se nezdařilo, protože byl tento objekt prázdný.|
|[binary_negate](../standard-library/binary-negate-class.md)|Třída šablony poskytující členské funkce, které negují návratovou hodnotu zadané binární funkce.<br/> (Zastaralé v C ++ 17.) |
|[binder1st](../standard-library/binder1st-class.md)|Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním prvního argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[binder2nd](../standard-library/binder2nd-class.md)|Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním druhého argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem reference.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem ukazatele.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která přijímá jeden argument, jako objekt binární funkce při inicializaci s argumentem reference.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která přijímá jeden argument, jako objekt binární funkce při inicializaci s argumentem ukazatele.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[– funkce](../standard-library/function-class.md)|Třída, která obaluje volatelný objekt.|
|[Hodnota hash](../standard-library/hash-class.md)|Třída, která vypočítá kód hash hodnoty.|
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|Třída, která testuje, zda je určitý typ generován voláním metody `bind`.|
|[is_placeholder](../standard-library/is-placeholder-class.md)|Třída, která testuje, zda je určitý typ zástupným symbolem.|
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Třída adaptéru umožňující `non_const` členskou funkci, která nepřijímá žádné argumenty, která se má volat jako objekt jednočlenné funkce při inicializaci s argumentem reference.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Třída adaptéru umožňující `non_const` členskou funkci, která nepřijímá žádné argumenty, která se má volat jako objekt jednočlenné funkce při inicializaci s argumentem ukazatele.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Třída adaptéru umožňující `non_const` členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem reference.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Třída adaptéru umožňující `non_const` členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem ukazatele.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|Převede ukazatel na binární funkci na přizpůsobitelnou binární funkci.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[reference_wrapper](../standard-library/reference-wrapper-class.md)|Třída, která obaluje referenci.|
|[unary_negate](../standard-library/unary-negate-class.md)|Třída šablony poskytující členské funkce, které negují návratovou hodnotu zadané jednočlenné funkce.<br/> (Zastaralé v C ++ 17.)  |

## <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Vytvoření vazby](../standard-library/functional-functions.md#bind)|Naváže argumenty na volatelný objekt.|
|[bind1st](../standard-library/functional-functions.md#bind1st)|Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby prvního argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[bind2nd](../standard-library/functional-functions.md#bind2nd)|Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby druhého argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[bit_and](../standard-library/functional-functions.md#bit_and)|Vrací bitové logické AND (binární operátor &) dvou parametrů.|
|[bit_not](../standard-library/functional-functions.md#bit_not)|Vrací bitový logický doplněk (operátor ~) parametru.<br/> (Přidáno v C ++ 14.) |
|[bit_or](../standard-library/functional-functions.md#bit_or)|Vrací bitové logické OR (operátor&#124;) dvou parametrů.|
|[bit_xor](../standard-library/functional-functions.md#bit_xor)|Vrací bitové logické XOR (operátor ^) dvou parametrů.|
|[cref](../standard-library/functional-functions.md#cref)|Z argumentu vytvoří konstantní `reference_wrapper`.|
|[mem_fn](../standard-library/functional-functions.md#mem_fn)|Vygeneruje jednoduchou obálku volání.|
|[mem_fun](../standard-library/functional-functions.md#mem_fun)|Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů ukazatelů.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)|Pomocná funkce šablony použitá k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů reference.|
|[not1 –](../standard-library/functional-functions.md#not1)|Vrací doplněk jednočlenného predikátu.<br/> (Zastaralé v C ++ 17.) |
|[not2](../standard-library/functional-functions.md#not2)|Vrací doplněk binárního predikátu.<br/> (Zastaralé v C ++ 17.) |
|[not_fn](../standard-library/functional-functions.md#not_fn)|Vrací doplněk výsledkem jeho objekt funkce.<br/> (Přidáno v C ++ 17.) |
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun)|Pomocná funkce šablony použitá k převedení ukazatelů na jednočlenné a binární funkce do jednočlenných a binárních přizpůsobitelných funkcí.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[ref](../standard-library/functional-functions.md#ref)|Vytvoří `reference_wrapper` z argumentu.|
|[swap](../standard-library/functional-functions.md#swap)|Prohodí dva `function` objekty.|

## <a name="structs"></a>Struktury

|Struktura|Popis|
|-|-|
|[binary_function –](../standard-library/binary-function-struct.md)|Prázdná základní třída definující typy, které mohou být zděděny odvozenou třídou obsahující objekt binární funkce.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |
|[vydělí](../standard-library/divides-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace dělení na prvcích zadaného typu hodnoty.|
|[equal_to](../standard-library/equal-to-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu rovna jiné hodnotě tohoto typu.|
|[greater](../standard-library/greater-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu větší než jiná hodnota tohoto typu.|
|[greater_equal](../standard-library/greater-equal-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu větší nebo rovna jiné hodnotě tohoto typu.|
|[méně](../standard-library/less-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu menší než jiná hodnota tohoto typu.|
|[less_equal](../standard-library/less-equal-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu menší nebo rovna jiné hodnotě tohoto typu.|
|[logical_and](../standard-library/logical-and-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace konjunkce prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|
|[logical_not](../standard-library/logical-not-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace negace prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|
|[logical_or](../standard-library/logical-or-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace disjunkce prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|
|[minus](../standard-library/minus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace odčítání na prvcích zadaného typu hodnoty.|
|[modulus](../standard-library/modulus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace numerického zbytku (modulus) na prvcích zadaného typu hodnoty.|
|[Vynásobí](../standard-library/multiplies-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace násobení na prvcích zadaného typu hodnoty.|
|[negate](../standard-library/negate-struct.md)|Třída poskytující předdefinovaný objekt funkce, který vrací záporné hodnoty prvku.|
|[not_equal_to](../standard-library/not-equal-to-struct.md)|Binární predikát, který testuje, zda není hodnota zadaného typu rovna jiné hodnotě tohoto typu.|
|[plus](../standard-library/plus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace sčítání na prvcích zadaného typu hodnoty.|
|[unary_function –](../standard-library/unary-function-struct.md)|Prázdná základní třída definující typy, které mohou být zděděny odvozenou třídou obsahující objekt jednočlenné funkce.<br/> (Zastaralé v C ++ 11 v C ++ 17 odebrané.) |

## <a name="objects"></a>Objekty

|Objekt|Popis|
|-|-|
|[_1.._M](../standard-library/1-object.md)|Zástupné symboly pro nahraditelné argumenty.|

## <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](../standard-library/functional-operators.md#op_eq_eq)|Zakáže porovnávání rovnosti volatelných objektů.|
|[operator!=](../standard-library/functional-operators.md#op_neq)|Zakáže porovnávání nerovnosti volatelných objektů.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
