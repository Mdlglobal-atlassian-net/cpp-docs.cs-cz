---
title: "&lt;funkční&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
dev_langs: C++
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f7b09ed7c4b52b45efee0708f65d8d2f3e24cd6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltfunctionalgt"></a>&lt;funkční&gt;
Definuje funkce standardní knihovny C++, které pomáhají při vytváření *funkce objekty*– taky známé jako functors – a jejich vazače. Objekt funkce je objekt typu, který definuje `operator()`. Objekt funkce může být ukazatel na funkci, ale častěji tento objekt slouží k ukládání dalších informací, ke kterým lze získat přístup během volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <functional>  
```  
  
## <a name="remarks"></a>Poznámky  
 Algoritmy vyžadují dva druhy objektů funkce, jednočlenné a binární. Jednočlenné objekty funkce vyžadují jeden argument a binární objekty funkce vyžadují dva argumenty. Objekt funkce a ukazatelů na funkce můžete předat jako predikát algoritmus, ale funkce objekty jsou také přizpůsobitelné a zvýšit oboru, flexibilitu a efektivitu standardní knihovny C++. Například, pokud potřebná hodnota musí být navázána na funkci před předáním algoritmu, nelze ukazatel na funkci použít. Adaptéry funkce převádějí ukazatele na funkci na přizpůsobitelné objekty funkce, které lze navázat na hodnotu. Záhlaví \<funkční > také obsahuje členské funkce adaptéry, umožňujících členské funkce, která se má volat jako objekty přizpůsobitelné funkce. Funkce jsou přizpůsobitelné, pokud obsahují deklarace vnořených typů určující jejich argumenty a návratové typy. Standard jazyka C++ vyžaduje, aby tato přizpůsobivost byla implementována všemi standardními třídami objektů dědícími ze základních tříd jednočlenné nebo binární funkce. Objekty funkcí a jejich adaptéry povolit standardní knihovna C++ upgradovat stávající aplikace a integrovat knihovny do C++ programovací prostředí.  
  
 Visual C++ implementace funkce objektů v \<funkční > zahrnuje *transparentní operátor functors*, které jsou specializací standardní funkce objekty a žádné parametry šablony a Proveďte ideální předávání argumenty funkce a ideální vraťte výsledku. Tato funkce je součástí návrhu specifikace standardu C++14. Tyto specializace šablony nevyžadují určení typů argumentu při vyvolání aritmetických, relačních, logických a bitových operátorů funktorů. Lze přetěžovat aritmetické, relační, logické a bitové operátory vlastních typů nebo heterogenní kombinace typů, a potom použít funktory transparentního operátoru jako argumenty funkce. Například pokud vaše typ *MyType* implementuje `operator<`, můžete volat `sort(my_collection.begin(), my_collection.end(), less<>())` místo explicitně zadat typ `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.  
  
## <a name="c11c14-implementation"></a>Implementace standardu C++11/C++14  
 Následující funkce byly přidány do implementace standardu C++11/C++14 v jazyce Visual C++:  
  
-   A *volání podpis* je název návratový typ a v závorce oddělené čárkami seznam nula nebo více typy argumentů.  
  
-   A *s typ* ukazatel do funkce, ukazatelem na funkci. člen, ukazatel na člena dat nebo typu třídy, jejichž objekty se mohou zobrazit okamžitě nalevo od operátor volání funkce.  
  
-   A *s objekt* je objekt s typu.  
  
-   A *obálku typ volání* je typ, který obsahuje objekt volatelná aplikacemi a podporuje volání operace, které přeposílá požadavky do tohoto objektu.  
  
-   A *volání obálku* je objekt typu obálku volání.  
  
-   A *cílový objekt* je možné volat objekt uchovávat objekt obálky volání.  
  
 Pseudofunkcí `INVOKE(f, t1, t2, ..., tN)` se rozumí jedna z následujících možností:  
  
- `(t1.*f)(t2, ..., tN)`, když je `f` ukazatel na členskou funkci třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z typu `T`.  
  
- `((*t1).*f)(t2, ..., tN)`, když je `f` ukazatel na členskou funkci třídy `T` a `t1` není jedním z typů uvedených v předchozí položce.  
  
- `t1.*f`, když N == 1 a `f` je ukazatel na členská data třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z typu `T`.  
  
- `(*t1).*f`, když N == 1 a `f` je ukazatel na datový člen třídy `T` a `t1` není jedním z typů uvedených v předchozí položce.  
  
- `f(t1, t2, ..., tN)` ve všech ostatních případech.  
  
 Pseudofunkce `INVOKE(f, t1, t2, ..., tN, R)` znamená `INVOKE(f, t1, t2, ..., tN)` implicitně převedenou na `R`.  
  
 Pokud má obálku volání *slabé výsledný typ*, typ jeho typ člena `result_type` je na základě typu `T` cílového objektu obálku, a to následujícím způsobem:  
  
-   Pokud je `T` ukazatel na funkci, je `result_type` synonymem návratového typu `T`.  
  
-   Pokud je `T` ukazatel na členskou funkci, je `result_type` synonymem návratového typu `T`.  
  
-   Pokud je `T` typ třídy, která obsahuje typ členu `result_type`, pak je `result_type` synonymem pro `T::result_type`.  
  
-   Jinak neexistuje žádný člen `result_type`.  
  
 Každá obálka volání má konstruktor přesunutí a konstruktor kopírování. A *jednoduché volání obálku* obálku volání, která má přiřazení operátor a jehož kopírovacího konstruktoru, konstruktor move a operátor přiřazení nevyvolá výjimku výjimky. A *předávání volání obálku* volání obálku, kterou lze volat pomocí seznam libovolný argumentů a který doručí argumenty k objektu zabalené s jako odkazy. Všechny argumenty r-hodnot jsou dodávány jako odkazy r-hodnot a argumenty l-hodnot jsou dodávány jako odkazy l-hodnot.  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[bad_function_call](../standard-library/bad-function-call-class.md)|Třídu, která popisuje výjimku vyvolána výjimka, která označuje, že volání `operator()` na [funkce](../standard-library/function-class.md) objektu se nezdařilo, protože objekt byl prázdný.|  
|[binary_negate –](../standard-library/binary-negate-class.md)|Třída šablony poskytující členské funkce, které negují návratovou hodnotu zadané binární funkce.|  
|[binder1st –](../standard-library/binder1st-class.md)|Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním prvního argumentu binární funkce na zadanou hodnotu.|  
|[binder2nd –](../standard-library/binder2nd-class.md)|Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním druhého argumentu binární funkce na zadanou hodnotu.|  
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem reference.|  
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem ukazatele.|  
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která přijímá jeden argument, jako objekt binární funkce při inicializaci s argumentem reference.|  
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Třída adaptéru umožňující volat konstantní členskou funkci, která přijímá jeden argument, jako objekt binární funkce při inicializaci s argumentem ukazatele.|  
|[funkce](../standard-library/function-class.md)|Třída, která obaluje volatelný objekt.|  
|[Hodnota hash](../standard-library/hash-class.md)|Třída, která vypočítá kód hash hodnoty.|  
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|Třída, která testuje, zda je určitý typ generován voláním metody `bind`.|  
|[is_placeholder](../standard-library/is-placeholder-class.md)|Třída, která testuje, zda je určitý typ zástupným symbolem.|  
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Třídu adaptér, který umožňuje **non_const** – členská funkce, které nepřijímá žádné argumenty, která se má volat jako objekt funkce unární při inicializaci s argumentem odkaz.|  
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Třídu adaptér, který umožňuje **non_const** – členská funkce, které nepřijímá žádné argumenty, která se má volat jako objekt funkce unární při inicializaci s argumentem ukazatele.|  
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Třídu adaptér, který umožňuje **non_const** – členská funkce, které přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem odkaz.|  
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Třídu adaptér, který umožňuje **non_const** – členská funkce, které přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem ukazatele.|  
|[pointer_to_binary_function –](../standard-library/pointer-to-binary-function-class.md)|Převede ukazatel na binární funkci na přizpůsobitelnou binární funkci.|  
|[pointer_to_unary_function –](../standard-library/pointer-to-unary-function-class.md)|Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci.|  
|[reference_wrapper –](../standard-library/reference-wrapper-class.md)|Třída, která obaluje referenci.|  
|[unary_negate –](../standard-library/unary-negate-class.md)|Třída šablony poskytující členské funkce, které negují návratovou hodnotu zadané jednočlenné funkce.|  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[vazby](../standard-library/functional-functions.md#bind)|Naváže argumenty na volatelný objekt.|  
|[bind1st –](../standard-library/functional-functions.md#bind1st)|Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby prvního argumentu binární funkce na zadanou hodnotu.|  
|[bind2nd –](../standard-library/functional-functions.md#bind2nd)|Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby druhého argumentu binární funkce na zadanou hodnotu.|  
|[bit_and –](../standard-library/functional-functions.md#bit_and)|Vrací bitové logické AND (binární operátor &) dvou parametrů.|  
|[bit_not –](../standard-library/functional-functions.md#bit_not)|Vrací bitový logický doplněk (operátor ~) parametru.|  
|[bit_or –](../standard-library/functional-functions.md#bit_or)|Vrátí logické bitová hodnota OR (operátor &#124;) z těchto parametrů.|  
|[bit_xor –](../standard-library/functional-functions.md#bit_xor)|Vrací bitové logické XOR (operátor ^) dvou parametrů.|  
|[cref –](../standard-library/functional-functions.md#cref)|Z argumentu vytvoří konstantní `reference_wrapper`.|  
|[mem_fn –](../standard-library/functional-functions.md#mem_fn)|Vygeneruje jednoduchou obálku volání.|  
|[mem_fun –](../standard-library/functional-functions.md#mem_fun)|Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů ukazatelů.|  
|[mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref)|Pomocná funkce šablony použitá k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů reference.|  
|[not1 –](../standard-library/functional-functions.md#not1)|Vrací doplněk jednočlenného predikátu.|  
|[not2 –](../standard-library/functional-functions.md#not2)|Vrací doplněk binárního predikátu.|  
|[ptr_fun –](../standard-library/functional-functions.md#ptr_fun)|Pomocná funkce šablony použitá k převedení ukazatelů na jednočlenné a binární funkce do jednočlenných a binárních přizpůsobitelných funkcí.|  
|[REF](../standard-library/functional-functions.md#ref)|Vytvoří `reference_wrapper` z argumentu.|  
|[swap](../standard-library/functional-functions.md#swap)|Prohození dva `function` objekty.|  
  
### <a name="structs"></a>Struktury  
  
|||  
|-|-|  
|[binary_function –](../standard-library/binary-function-struct.md)|Prázdná základní třída definující typy, které mohou být zděděny odvozenou třídou obsahující objekt binární funkce.|  
|[vydělí](../standard-library/divides-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace dělení na prvcích zadaného typu hodnoty.|  
|[equal_to](../standard-library/equal-to-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu rovna jiné hodnotě tohoto typu.|  
|[větší](../standard-library/greater-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu větší než jiná hodnota tohoto typu.|  
|[greater_equal –](../standard-library/greater-equal-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu větší nebo rovna jiné hodnotě tohoto typu.|  
|[menší](../standard-library/less-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu menší než jiná hodnota tohoto typu.|  
|[less_equal –](../standard-library/less-equal-struct.md)|Binární predikát, který testuje, zda je hodnota zadaného typu menší nebo rovna jiné hodnotě tohoto typu.|  
|[logical_and –](../standard-library/logical-and-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace konjunkce prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|  
|[logical_not –](../standard-library/logical-not-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace negace prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|  
|[logical_or –](../standard-library/logical-or-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí logické operace disjunkce prvků zadaného typu hodnoty a testuje pravdivost nebo nepravdivost výsledku.|  
|[minus](../standard-library/minus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace odčítání na prvcích zadaného typu hodnoty.|  
|[numerického zbytku](../standard-library/modulus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace numerického zbytku (modulus) na prvcích zadaného typu hodnoty.|  
|[multiplies –](../standard-library/multiplies-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace násobení na prvcích zadaného typu hodnoty.|  
|[negate –](../standard-library/negate-struct.md)|Třída poskytující předdefinovaný objekt funkce, který vrací záporné hodnoty prvku.|  
|[not_equal_to –](../standard-library/not-equal-to-struct.md)|Binární predikát, který testuje, zda není hodnota zadaného typu rovna jiné hodnotě tohoto typu.|  
|[Plus](../standard-library/plus-struct.md)|Třída poskytující předdefinovaný objekt funkce, který provádí aritmetické operace sčítání na prvcích zadaného typu hodnoty.|  
|[unary_function –](../standard-library/unary-function-struct.md)|Prázdná základní třída definující typy, které mohou být zděděny odvozenou třídou obsahující objekt jednočlenné funkce.|  
  
### <a name="objects"></a>Objekty  
  
|||  
|-|-|  
|[_1.._M](../standard-library/1-object.md)|Zástupné symboly replaceable argumenty.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator ==](../standard-library/functional-operators.md#op_eq_eq)|Zakáže porovnávání rovnosti volatelných objektů.|  
|[Operator! =](../standard-library/functional-operators.md#op_neq)|Zakáže porovnávání nerovnosti volatelných objektů.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)
