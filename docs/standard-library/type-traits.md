---
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: c80629fd8771206d193b53aa7c32073de0ba45dd
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006720"
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;

Definuje šablony pro konstanty z doby kompilace, které poskytují informace o vlastnostech jejich argumenty typu, nebo vytvořit transformovaný typy.

## <a name="syntax"></a>Syntaxe

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Poznámky

Třídy a šablon v \<type_traits > se používá pro podporu odvození typu proměnné, klasifikace a transformace v době kompilace. Také se používají ke zjištění chyby související s typem a které vám pomůžou optimalizovat obecný kód. Unární vlastností s typem popisu vlastnosti typu, vlastností s typem binární popisují vztah mezi typy a vlastnosti transformace změnit vlastnost typu.

Pomocná třída `integral_constant` a jeho specializace šablony `true_type` a `false_type` tvoří základní třídy pro predikáty typu. A *predikát typu* je šablona, která přijímá jeden nebo více argumentů typu. Pokud predikát typu *platí*, veřejně odvozené, přímo nebo nepřímo ze [true_type](../standard-library/type-traits-typedefs.md#true_type). Pokud predikát typu *obsahuje hodnotu false*, veřejně odvozené, přímo nebo nepřímo ze [false_type](../standard-library/type-traits-typedefs.md#false_type).

A *modifikátor typu* nebo *transformace vlastností* je šablona, která přijímá jeden nebo více argumentů šablony a má jeden člen `type`, což je synonymum pro typ změny.

### <a name="alias-templates"></a>Šablony aliasů

Pro zjednodušení výrazy typu vlastnosti, [šablony aliasů](../cpp/aliases-and-typedefs-cpp.md) pro `typename some_trait<T>::type` jsou k dispozici, kde *some_trait* je název třídy šablony. Například [add_const –](../standard-library/add-const-class.md) má šabloně aliasů pro daný typ `add_const_t`definovaná jako:

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

Toto jsou zadaná aliasy pro `type` členy:

||||
|-|-|-|
| add_const_t | add_cv_t | add_lvalue_reference_t |
| add_pointer_t | add_rvalue_reference_t | add_volatile_t |
| aligned_storage_t | aligned_union_t | common_type_t |
| conditional_t | decay_t | enable_if_t |
| invoke_result_t | make_signed_t | make_unsigned_t |
| remove_all_extents_t | remove_const_t | remove_cv_t |
| remove_extent_t | remove_pointer_t | remove_reference_t |
| remove_volatile_t | result_of_t | underlying_type_t |

### <a name="classes"></a>Třídy

Pomocná třída a definice TypeDef

|||
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Díky integrální konstantní typ a hodnotu.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Obsahuje integrální konstantou, jehož hodnota je true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Obsahuje integrální konstanta s hodnotou false.|

Primární typ kategorie

|||
|-|-|
|[is_void](../standard-library/is-void-class.md)|Testuje, jestli je typ **void**.|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Testuje, jestli je typ `std::nullptr_t`.|
|[is_integral](../standard-library/is-integral-class.md)|Ověřuje, zda celočíselného typu.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Ověřuje, zda je typ s plovoucí desetinnou čárkou.|
|[is_array](../standard-library/is-array-class.md)|Ověřuje, zda je typ pole.|
|[is_pointer](../standard-library/is-pointer-class.md)|Ověřuje, zda je typ ukazatele.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Testuje, zda je typ reference na lvalue.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Testuje, zda je typ odkaz rvalue.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Ověřuje, zda typ ukazatel na člena objektu.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Ověřuje, zda typ ukazatel na členskou funkci.|
|[is_enum](../standard-library/is-enum-class.md)|Ověřuje, zda typ výčtu.|
|[is_union](../standard-library/is-union-class.md)|Ověřuje, zda je typ sjednocení.|
|[is_class](../standard-library/is-class-class.md)|Ověřuje, zda typ třídy.|
|[is_function](../standard-library/is-function-class.md)|Ověřuje, zda typ je typ funkce.|

Složený typ kategorie

|||
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Ověřuje, zda je typ odkaz.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Ověřuje, zda aritmetického typu.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Testuje, jestli je typ **void** nebo aritmetické.|
|[is_object](../standard-library/is-object-class.md)|Ověřuje, zda typ je typ objektu.|
|[is_scalar](../standard-library/is-scalar-class.md)|Ověřuje, zda typ není skalární.|
|[is_compound](../standard-library/is-compound-class.md)|Ověřuje, zda zadaný typ není skalární.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Ověřuje, zda typ ukazatel na člen.|

Typ vlastnosti

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|Testuje, jestli je typ **const**.|
|[is_volatile](../standard-library/is-volatile-class.md)|Testuje, jestli je typ **volatile**.|
|[is_trivial](../standard-library/is-trivial-class.md)|Ověřuje, zda typ jednoduchého dotazu.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Ověřuje, zda je typ snadno kopírovatelná.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Testuje, zda je typ je typ standardního rozložení.|
|[is_pod](../standard-library/is-pod-class.md)|Ověřuje, zda je typ POD.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Ověřuje, zda lze zadat `constexpr` proměnné nebo se používají v `constexpr` funkce.|
|[is_empty](../standard-library/is-empty-class.md)|Ověřuje, zda typ prázdnou třídu.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Ověřuje, zda typ polymorfní třídy.|
|[is_abstract](../standard-library/is-abstract-class.md)|Ověřuje, zda typ je abstraktní třída.|
|[is_final](../standard-library/is-final-class.md)|Ověřuje, zda typ není typem třídy označené `final`.|
|[is_signed](../standard-library/is-signed-class.md)|Ověřuje, zda typ celé číslo se znaménkem.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Ověřuje, zda typ celé číslo bez znaménka.|
|[is_constructible](../standard-library/is-constructible-class.md)|Ověřuje, zda typ constructible pomocí zadanými typy argumentu.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Ověřuje, zda má typ výchozí konstruktor.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Ověřuje, zda typ má konstruktor kopie.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Ověřuje, zda typ má konstruktor move.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Ověřuje, zda první typ lze přiřadit hodnotu druhého typu.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Ověřuje, zda je možné přiřadit typ konstantní odkaz na hodnotu typu.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Ověřuje, zda je možné přiřadit typ odkaz rvalue typu.|
|[is_destructible –](../standard-library/is-destructible-class.md)|Ověřuje, zda typ zničitelné.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Ověřuje, zda typ používá žádné netriviální operace při použití zadaného typů.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Ověřuje, zda typ používá žádné netriviální operace při vytvořen výchozí.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Ověřuje, zda typ používá žádné netriviální operace při kopírování.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Ověřuje, zda typ používá žádné netriviální operace při přesunu.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Testuje, jestli jsou tyto typy Přiřaditelné a přiřazení používá žádné netriviální operace.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Testuje, jestli je typ přiřaditelný kopírování a přiřazení používá žádné netriviální operace.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Testuje, jestli je typ přiřaditelný přesunutí a přiřazení používá žádné netriviální operace.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Testuje, jestli je typ zničitelné a používá žádné operace netriviální destruktor.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Ověřuje, zda je typ constructible a se ví, že výjimku při vytvářeny pomocí zadané typy.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Testy, jestli je typ výchozí constructible a se ví, že výjimku při vytvořen výchozí.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Ověřuje, zda typ je kopírovací a kopírovací konstruktor se ví, že výjimku.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Testuje, jestli typ constructible přesunutí a konstruktor přesunu se ví, že výjimku.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Testuje, jestli je typ přiřaditelný pomocí zadaného typu a přiřazení se ví, že výjimku.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Testuje, jestli je typ přiřaditelný kopírování a přiřazení se ví, že výjimku.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Testuje, jestli je typ přiřaditelný přesunutí a přiřazení se ví, že výjimku.|
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Testuje, jestli je typ zničitelné a destruktor se ví, že výjimku.|
|`has_virtual_destructor`|Ověřuje, zda typ má virtuální destruktor.|
| [is_invocable](is-invocable-classes.md) | Ověřuje, zda volatelného typu lze vyvolat pomocí zadanými typy argumentu.<br/> Přidáno v C ++ 17. |
| [is_invocable_r](is-invocable-classes.md) | Testuje, zda volatelného typu lze vyvolat pomocí zadanými typy argumentu a výsledek je lze převést na zadaný typ.<br/> Přidáno v C ++ 17. |
| [is_nothrow_invocable](is-invocable-classes.md) | Testy, jestli je možné vyvolat volatelného typu pomocí zadaného argumentu typů a není znám vyvolávat výjimky.<br/> Přidáno v C ++ 17. |
| [is_nothrow_invocable_r](is-invocable-classes.md) | Testuje, zda volatelného typu lze vyvolat pomocí zadanými typy argumentu a se ví, že vyvolat výjimky a výsledek je lze převést na zadaný typ.<br/> Přidáno v C ++ 17. |

Dotazy na vlastnosti typu

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Získá zarovnání typu.|
|[pořadí](../standard-library/rank-class.md)|Získá počet rozměrů pole.|
|[rozsah](../standard-library/extent-class.md)|Získá počet elementů v zadaném poli dimenzi.|

Typ relace

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|Ověřuje, zda dva typy jsou stejné.|
|[is_base_of](../standard-library/is-base-of-class.md)|Ověřuje, zda je jeden typ základ jiného.|
|[is_convertible](../standard-library/is-convertible-class.md)|Ověřuje, zda je jeden typ lze převést na jiný.|

Úpravy const-volatile

|||
|-|-|
|[add_const](../standard-library/add-const-class.md)|Vytvoří **const** typ z typu.|
|[add_volatile](../standard-library/add-volatile-class.md)|Vytvoří **volatile** typ z typu.|
|[add_cv](../standard-library/add-cv-class.md)|Vytvoří **const volatile** typ z typu.|
|[remove_const](../standard-library/remove-const-class.md)|Vytvoří nekonstantní typ z typu.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Vytvoří stálé typ z typu.|
|[remove_cv](../standard-library/remove-cv-class.md)|Vytvoří nekonstantní typ není typu volatile z typu.|

Odkaz na úpravy

|||
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Vytvoří odkaz na typ z typu.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Vytvoří odkaz rvalue na typ z typu|
|[remove_reference](../standard-library/remove-reference-class.md)|Vytvoří typ bez odkazu z typu.|

Úpravy přihlašování

|||
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Vytvoří typu, pokud je podepsaný nebo nejmenší typ se znaménkem větší než nebo rovno velikosti typu.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Vytvoří typu, pokud je bez znaménka nebo nejmenší typu bez znaménka větší než nebo rovno velikosti typu.|

Pole úprav

|||
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Vytvoří typ bez pole z typu pole.|
|[remove_extent](../standard-library/remove-extent-class.md)|Vytvoří typ prvku z typu pole.|

Úpravy ukazatele

|||
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Vytvoří ukazatel na typ z typu.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Vytvoří typ z ukazatele na typ.|

Další transformace

|||
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Neinicializované paměti přidělí zarovnaný typu.|
|[aligned_union](../standard-library/aligned-union-class.md)|Neinicializované paměti přidělí pro zarovnané sjednocení s netriviálními konstruktor nebo destruktor.|
|[common_type](../standard-library/common-type-class.md)|Vytvoří společný typ všechny typy balíček parametrů.|
|[Podmíněné](../standard-library/conditional-class.md)|Pokud je podmínka pravdivá, vytvoří první zadaný typ, jinak druhého zadaného typu.|
|[decay](../standard-library/decay-class.md)|Vytvoří typ jako předán podle hodnoty. Vytvoří typ bez odkazu, nekonstantní nebo není typu volatile nebo vytvoří ukazatel na typ.|
|[enable_if](../standard-library/enable-if-class.md)|Pokud je podmínka pravdivá, vytváří zadaný typ, jinak bez typu.|
|[invoke_result](invoke-result-class.md)|Určuje návratový typ volatelného typu, který přijímá zadanými typy argumentu. <br/>Přidáno v C ++ 17. |
|[result_of](../standard-library/result-of-class.md)|Určuje návratový typ volatelného typu, který přijímá zadanými typy argumentu. <br/>Přidáno v C ++ 14, zastaralé v C ++ 17. |
|[underlying_type](../standard-library/underlying-type-class.md)|Vytvoří základní celočíselného typu pro typ výčtu.|

## <a name="see-also"></a>Viz také:

[\<funkční >](../standard-library/functional.md)<br/>
