---
title: '&lt;functional &gt;'
ms.date: 02/21/2019
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
ms.openlocfilehash: 67b2ccf70b4d3045cecd13d9096875f77c4cde9a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689624"
---
# <a name="ltfunctionalgt"></a>&lt;functional &gt;

Definuje C++ standardní funkce knihovny, které vám pomůžou vytvářet *objekty funkcí*, označované také jako *funktory*a jejich pořadače. Objekt funkce je objekt typu, který definuje `operator()`. Objekt funkce může být ukazatel na funkci, ale častěji tento objekt slouží k ukládání dalších informací, ke kterým lze získat přístup během volání funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<functional >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Algoritmy vyžadují dva typy objektů Functions: *unární* a *binární*. Jednočlenné objekty funkce vyžadují jeden argument a binární objekty funkce vyžadují dva argumenty. Objekt funkce a ukazatele na funkce mohou být předány jako predikát pro algoritmus, ale objekty funkcí jsou také upravitelné a zvyšují rozsah, flexibilitu a efektivitu C++ standardní knihovny. Například, pokud potřebná hodnota musí být navázána na funkci před předáním algoritmu, nelze ukazatel na funkci použít. Adaptéry funkce převádějí ukazatele na funkci na přizpůsobitelné objekty funkce, které lze navázat na hodnotu. Hlavička \<functional > také obsahuje adaptéry členské funkce, které umožňují volat členské funkce jako přizpůsobitelné objekty funkce. Funkce jsou přizpůsobitelné, pokud obsahují deklarace vnořených typů určující jejich argumenty a návratové typy. Objekty funkce a jejich adaptéry umožňují C++ standardní knihovně upgradovat stávající aplikace a pomáhat integrovat knihovnu do C++ programovacího prostředí.

Implementace objektů funkcí v \<functional > zahrnuje *funktory transparentního operátoru*. což jsou specializace standardních objektů funkcí a neobsahují žádné parametry šablony a provádějí dokonalé přesměrování argumentů funkce a dokonalého vrácení výsledku. Tyto specializace šablony nevyžadují určení typů argumentu při vyvolání aritmetických, relačních, logických a bitových operátorů funktorů. Lze přetěžovat aritmetické, relační, logické a bitové operátory vlastních typů nebo heterogenní kombinace typů, a potom použít funktory transparentního operátoru jako argumenty funkce. Například pokud váš typ *MyType* implementuje `operator<`, můžete volat `sort(my_collection.begin(), my_collection.end(), less<>())` namísto explicitního určení typu `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.

Do C++ 11, C++ 14 a C++ 17 jsou přidány následující funkce:

- *Signatura volání* je název návratového typu následovaný čárkou odděleným seznamem nula nebo více typů argumentů.

- Typ, který lze *volat* , je ukazatel na funkci, ukazatel na členskou funkci, ukazatel na Členská data nebo typ třídy, jejíž objekty se mohou objevit hned vlevo od operátoru volání funkce.

- Objekt, který se může *volat* , je objektem typu, který je k.

- *Typ obálky volání* je typ, který obsahuje volající objekt a podporuje operaci volání, která je předána tomuto objektu.

- *Obálka volání* je objekt typu obálky volání.

- *Cílový objekt* je volající objekt, který je držen objektem obálky volání.

Pseudofunkcí `INVOKE(f, t1, t2, ..., tN)` se rozumí jedna z následujících možností:

- `(t1.*f)(t2, ..., tN)`, je-li `f` ukazatel na členskou funkci třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z `T`.

- `((*t1).*f)(t2, ..., tN)`, je-li `f` ukazatel na členskou funkci třídy `T` a `t1` není jedním z typů popsaných v předchozí položce.

- `t1.*f`, když N = 1 a `f` je ukazatel na Členská data třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu% nebo odkaz na objekt typu odvozený. z `T`.

- `(*t1).*f`, když N = 1 a `f` je ukazatel na Členská data třídy `T` a `t1` není jedním z typů popsaných v předchozí položce.

- `f(t1, t2, ..., tN)` ve všech ostatních případech.

Pseudofunkce `INVOKE(f, t1, t2, ..., tN, R)` znamená `INVOKE(f, t1, t2, ..., tN)` implicitně převedenou na `R`.

Pokud má obálka volání *slabý typ výsledku*, typ jeho typu členu `result_type` je založen na typu `T` cílového objektu obálky, a to následujícím způsobem:

- Pokud je `T` ukazatel na funkci, je `result_type` synonymem návratového typu `T`.

- Pokud je `T` ukazatel na členskou funkci, je `result_type` synonymem návratového typu `T`.

- Pokud je `T` typ třídy, která obsahuje typ členu `result_type`, pak je `result_type` synonymem pro `T::result_type`.

- Jinak neexistuje žádný člen `result_type`.

Každá obálka volání má konstruktor přesunutí a konstruktor kopírování. *Jednoduchá obálka volání* je obálka volání, která má operátor přiřazení a jehož kopírovací konstruktor, konstruktor Move a operátor přiřazení nevyvolají výjimky. *Obálka přesměrování volání* je obálka volání, která může být volána pomocí libovolného seznamu argumentů a který doručuje argumenty zabaleného volajícího objektu jako odkazy. Všechny argumenty r-hodnot jsou dodávány jako odkazy r-hodnot a argumenty l-hodnot jsou dodávány jako odkazy l-hodnot.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[bad_function_call](../standard-library/bad-function-call-class.md)|Třída, která popisuje vyvolanou výjimku pro označení, že volání `operator()` objektu [funkce](../standard-library/function-class.md) se nezdařilo, protože objekt byl prázdný.|
|[binary_negate](../standard-library/binary-negate-class.md)|Šablona třídy poskytující členskou funkci, která negace návratové hodnoty zadané binární funkce.<br/> (Zastaralé v C++ 17.) |
|[binder1st –](../standard-library/binder1st-class.md)|Šablona třídy poskytující konstruktor, který převádí objekt binární funkce na unární objekt funkce navázáním prvního argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[binder2nd –](../standard-library/binder2nd-class.md)|Šablona třídy poskytující konstruktor, který převádí objekt binární funkce na unární objekt funkce navázáním druhého argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[boyer_moore_horspool_searcher](../standard-library/boyer-moore-horspool-searcher-class.md)||
|[boyer_moore_searcher](../standard-library/boyer-moore-searcher-class.md)||
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem reference.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem ukazatele.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která přijímá jeden argument, jako objekt binární funkce při inicializaci s argumentem reference.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která přijímá jeden argument, jako objekt binární funkce při inicializaci s argumentem ukazatele.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[default_searcher](../standard-library/default-searcher-class.md)||
|[slouží](../standard-library/function-class.md)|Třída, která obaluje volatelný objekt.|
|[kontrole](../standard-library/hash-class.md)|Třída, která vypočítá kód hash hodnoty.|
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|Třída, která testuje, zda je určitý typ generován voláním metody `bind`.|
|[is_placeholder](../standard-library/is-placeholder-class.md)|Třída, která testuje, zda je určitý typ zástupným symbolem.|
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Třída adaptéru umožňující `non_const` členskou funkci, která nepřijímá žádné argumenty, které se mají volat jako unární objekt funkce při inicializaci s argumentem odkazu.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Třída adaptéru, která `non_const` umožňuje, aby při inicializaci s argumentem ukazatele převolala žádné argumenty jako unární objekt funkce.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Třída adaptéru, která `non_const` umožňuje, aby byla při inicializaci s argumentem odkazu volána členská funkce, která přijímá jeden argument jako objekt binární funkce.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Třída adaptéru, která `non_const` umožňuje, aby byla při inicializaci s argumentem ukazatele volána členská funkce, která přijímá jeden argument jako objekt binární funkce.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|Převede ukazatel na binární funkci na přizpůsobitelnou binární funkci.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[reference_wrapper](../standard-library/reference-wrapper-class.md)|Třída, která obaluje referenci.|
|[unary_negate](../standard-library/unary-negate-class.md)|Šablona třídy poskytující členskou funkci, která negace návratové hodnoty zadané unární funkce.<br/> (Zastaralé v C++ 17.)  |

### <a name="functions"></a>Funkce

|||
|-|-|
|[zapisovat](../standard-library/functional-functions.md#bind)|Naváže argumenty na volatelný objekt.|
|[bind1st –](../standard-library/functional-functions.md#bind1st)|Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby prvního argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[bind2nd –](../standard-library/functional-functions.md#bind2nd)|Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby druhého argumentu binární funkce na zadanou hodnotu.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[bit_and](../standard-library/functional-functions.md#bit_and)|Vrátí bitový logický operátor AND (binární operátor &) dvou parametrů.|
|[bit_not](../standard-library/functional-functions.md#bit_not)|Vrací bitový logický doplněk (operátor ~) parametru.<br/> (Přidáno v C++ 14.) |
|[bit_or](../standard-library/functional-functions.md#bit_or)|Vrátí bitový logický operátor OR (operátor&#124;) dvou parametrů.|
|[bit_xor](../standard-library/functional-functions.md#bit_xor)|Vrací bitové logické XOR (operátor ^) dvou parametrů.|
|[cref](../standard-library/functional-functions.md#cref)|Z argumentu vytvoří konstantní `reference_wrapper`.|
|[Zavolejte](../standard-library/functional-functions.md#invoke)||
|[mem_fn](../standard-library/functional-functions.md#mem_fn)|Vygeneruje jednoduchou obálku volání.|
|[mem_fun](../standard-library/functional-functions.md#mem_fun)|Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů ukazatelů.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)|Pomocná funkce šablony použitá k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů reference.|
|[not1 –](../standard-library/functional-functions.md#not1)|Vrací doplněk jednočlenného predikátu.<br/> (Zastaralé v C++ 17.) |
|[not2 –](../standard-library/functional-functions.md#not2)|Vrací doplněk binárního predikátu.<br/> (Zastaralé v C++ 17.) |
|[not_fn](../standard-library/functional-functions.md#not_fn)|Vrátí KOMPLEMENT výsledku jeho objektu Function.<br/> (Přidáno v C++ 17.) |
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun)|Pomocná funkce šablony použitá k převedení ukazatelů na jednočlenné a binární funkce do jednočlenných a binárních přizpůsobitelných funkcí.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[ref](../standard-library/functional-functions.md#ref)|Vytvoří `reference_wrapper` z argumentu.|
|[adresu](../standard-library/functional-functions.md#swap)|Zamění dva objekty `function`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[binary_function](../standard-library/binary-function-struct.md)|Prázdná základní třída definující typy, které mohou být zděděny odvozenou třídou obsahující objekt binární funkce.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |
|[vydělí](../standard-library/divides-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace dělení na prvcích zadaného typu hodnoty.|
|[equal_to](../standard-library/equal-to-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu rovna jiné hodnotě tohoto typu.|
|[zvýšen](../standard-library/greater-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu větší než jiná hodnota tohoto typu.|
|[greater_equal](../standard-library/greater-equal-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu větší nebo rovna jiné hodnotě tohoto typu.|
|[tolik](../standard-library/less-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu menší než jiná hodnota tohoto typu.|
|[less_equal](../standard-library/less-equal-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu menší nebo rovna jiné hodnotě tohoto typu.|
|[logical_and](../standard-library/logical-and-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace konjunkce prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|
|[logical_not](../standard-library/logical-not-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace negace prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|
|[logical_or](../standard-library/logical-or-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace disjunkce prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|
|[symbol](../standard-library/minus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace odčítání na prvcích zadaného typu hodnoty.|
|[Modulus](../standard-library/modulus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace numerického zbytku (modulus) na prvcích zadaného typu hodnoty.|
|[vynásobí](../standard-library/multiplies-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace násobení na prvcích zadaného typu hodnoty.|
|[Negate](../standard-library/negate-struct.md)|Třída poskytující předdefinovaný objekt funkce, který vrací záporné hodnoty prvku.|
|[not_equal_to](../standard-library/not-equal-to-struct.md)|Binární predikát, který testuje, zda není hodnota zadaného typu rovna jiné hodnotě tohoto typu.|
|[i](../standard-library/plus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace sčítání na prvcích zadaného typu hodnoty.|
|[unary_function](../standard-library/unary-function-struct.md)|Prázdná základní třída definující typy, které mohou být zděděny odvozenou třídou obsahující objekt jednočlenné funkce.<br/> (Zastaralé v C++ 11, odebrané v C++ 17.) |

### <a name="objects"></a>Objekty

|||
|-|-|
|[_1.._M](../standard-library/1-object.md)|Zástupné symboly pro nahraditelné argumenty.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator = = – operátor](../standard-library/functional-operators.md#op_eq_eq)|Zakáže porovnávání rovnosti volatelných objektů.|
|[operator!=](../standard-library/functional-operators.md#op_neq)|Zakáže porovnávání nerovnosti volatelných objektů.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
