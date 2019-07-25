---
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: 703038ed435de36d60fcf97aa5100197602e7130
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455052"
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;

Definuje šablony pro konstanty v době kompilace, které poskytují informace o vlastnostech svých argumentů typu nebo vytvářejí transformované typy.

## <a name="syntax"></a>Syntaxe

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Poznámky

Třídy a šablony v \<type_traits > slouží pro podporu odvození typu, klasifikace a transformaci v době kompilace. Používají se také ke zjišťování chyb souvisejících s typem a k optimalizaci obecného kódu. Vlastnosti unárního typu popisují vlastnost typu, vlastnosti binárního typu popisují relaci mezi typy a transformační vlastnosti upravují vlastnost typu.

Pomocná třída `integral_constant` a její `true_type` specializace šablony a `false_type` tvoří základní třídy pro predikáty typu. *Predikát typu* je šablona, která přijímá jeden nebo více argumentů typu. Pokud predikát typu *drží hodnotu true*, je veřejně odvozen přímo nebo nepřímo z [true_type](../standard-library/type-traits-typedefs.md#true_type). Pokud predikát typu *obsahuje hodnotu false*, je veřejně odvozen přímo nebo nepřímo z [false_type](../standard-library/type-traits-typedefs.md#false_type).

*Modifikátor typu* nebo *transformační* vlastnost je šablona, která přebírá jeden nebo více argumentů šablony a má jeden člen, `type`,, což je synonymum pro upravený typ.

### <a name="alias-templates"></a>Šablony aliasů

Chcete-li zjednodušit výrazy vlastností typu, `typename some_trait<T>::type` jsou k dispozici [šablony aliasů](../cpp/aliases-and-typedefs-cpp.md) , kde *some_trait* je název třídy šablony. Například [add_const](../standard-library/add-const-class.md) má šablonu alias pro svůj typ `add_const_t`, definován jako:

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

Jedná se o zadané aliasy pro `type` členy:

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

Pomocná třída a definice typedef

|||
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Provede celočíselnou konstantu z typu a hodnotu.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Obsahuje integrální konstantu s hodnotou true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Obsahuje integrální konstantu s hodnotou false.|

Kategorie primárního typu

|||
|-|-|
|[is_void](../standard-library/is-void-class.md)|Testuje, zda je typ **void**.|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Testuje, zda je `std::nullptr_t`typ.|
|[is_integral](../standard-library/is-integral-class.md)|Testuje, zda je typ integrální.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Testuje, zda je typ plovoucí desetinná čárka.|
|[is_array](../standard-library/is-array-class.md)|Testuje, zda je typ pole.|
|[is_pointer](../standard-library/is-pointer-class.md)|Testuje, zda je typ ukazatel.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Testuje, zda je typ odkaz l-hodnota.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Testuje, zda je typem odkaz rvalue.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Testuje, zda je typ ukazatel na členský objekt.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Testuje, zda je typ ukazatel na členskou funkci.|
|[is_enum](../standard-library/is-enum-class.md)|Testuje, zda je typ výčet.|
|[is_union](../standard-library/is-union-class.md)|Testuje, zda je typ sjednocení.|
|[is_class](../standard-library/is-class-class.md)|Testuje, zda je typ třída.|
|[is_function](../standard-library/is-function-class.md)|Testuje, zda je typ typu funkce.|

Kategorie složených typů

|||
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Testuje, zda je typ odkaz.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Testuje, zda je typ aritmetický.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Testuje, zda je typ **void** nebo aritmetický typ.|
|[is_object](../standard-library/is-object-class.md)|Testuje, zda se jedná o typ objektu.|
|[is_scalar](../standard-library/is-scalar-class.md)|Testuje, zda je typ skalární.|
|[is_compound](../standard-library/is-compound-class.md)|Testuje, zda typ není skalární.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Testuje, zda je typ ukazatel na člen.|

Vlastnosti typu

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|Testuje, zda je typ **const**.|
|[is_volatile](../standard-library/is-volatile-class.md)|Testuje, zda je typ **volatile**.|
|[is_trivial](../standard-library/is-trivial-class.md)|Testuje, zda je typ triviální.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Testuje, zda je typ triviální kopie.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Testuje, zda je typ standardní typ rozložení.|
|[is_pod](../standard-library/is-pod-class.md)|Testuje, zda je typ POD.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Testuje, zda může být `constexpr` typ proměnná nebo použit `constexpr` ve funkci.|
|[is_empty](../standard-library/is-empty-class.md)|Testuje, zda je typ prázdná třída.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Testuje, zda je typ polymorfní třídy.|
|[is_abstract](../standard-library/is-abstract-class.md)|Testuje, zda je typ abstraktní třída.|
|[is_final](../standard-library/is-final-class.md)|Testuje, zda je typ typu třídy označeno `final`.|
|[is_aggregate](../standard-library/is-aggregate-class.md)||
|[is_signed](../standard-library/is-signed-class.md)|Testuje, zda je typ celé číslo se znaménkem.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Testuje, zda je typ unsigned integer.|
|[is_constructible](../standard-library/is-constructible-class.md)|Testuje, zda je typ constructible pomocí zadaných typů argumentů.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Testuje, zda má typ výchozí konstruktor.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Testuje, zda má typ kopírovací konstruktor.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Testuje, zda typ obsahuje konstruktor Move.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Testuje, zda může být prvnímu typu přiřazena hodnota druhého typu.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Testuje, zda lze typu přiřadit hodnotu odkazu const typu.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Testuje, zda lze typu přiřadit odkaz rvalue typu.|
|[is_swappable](../standard-library/type-traits-functions.md#is_swappable)||
|[is_swappable_with](../standard-library/type-traits-functions.md#is_swappable_with)||
|[is_destructible](../standard-library/is-destructible-class.md)|Testuje, zda je typ zničitelné.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Testuje, zda typ používá žádné netriviální operace při sestavení pomocí zadaných typů.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Testuje, zda typ při použití výchozího sestavení používá žádné netriviální operace.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Testuje, zda typ při konstrukci kopírování nepoužívá žádné netriviální operace.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Testuje, zda typ při přemístění konstrukce nepoužívá žádné netriviální operace.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Testuje, zda lze typy přiřadit a přiřazení nepoužívá žádné netriviální operace.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Testuje, zda je typ zkopírován a přiřazení nepoužívá žádné netriviální operace.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Testuje, jestli je typ přiřazený k přesunutí a přiřazení nepoužívá žádné netriviální operace.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Testuje, zda je typ zničitelné a destruktor nepoužívá žádné netriviální operace.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Testuje, zda je typ constructible a je známo, že není vyvolána při sestavení pomocí zadaných typů.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Testuje, zda je typ výchozí constructible a že je známo, že se má vyvolávat při vygenerování výchozí hodnoty.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Testuje, zda je typ Copy constructible a kopírovací konstruktor je znám jako nevyvolávání.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Testuje, zda je typ přesunut constructible a konstruktor Move je známý jako nevyvolávání.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Testuje, zda je možné typ přiřadit pomocí zadaného typu a že je známo, že přiřazení není vyhozeno.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Testuje, zda je typ zkopírován a přiřazení je známo, že není vyvolána.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Testuje, zda je daný typ přesunut a přiřazení je známo, že není vyvolána.|
|[is_nothrow_swappable](../standard-library/type-traits-functions.md#is_nothrow_swappable)||
|[is_nothrow_swappable_with](../standard-library/type-traits-functions.md#is_nothrow_swappable_with)||
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Testuje, zda je typ zničitelné a destruktor je známý jako nevyvolávání.|
|`has_virtual_destructor`|Testuje, zda má typ virtuální destruktor.|
|`has_unique_object_representations`||
| [is_invocable](is-invocable-classes.md) | Testuje, zda lze volat typ s možnou metodou pomocí zadaných typů argumentů.<br/> Přidáno v C++ 17. |
| [is_invocable_r](is-invocable-classes.md) | Testuje, zda lze volat typ s použitím zadaných typů argumentů a výsledek je převeden na zadaný typ.<br/> Přidáno v C++ 17. |
| [is_nothrow_invocable](is-invocable-classes.md) | Testuje, zda lze volat typ s použitím zadaných typů argumentů a že je známo, že nevyvolává výjimky.<br/> Přidáno v C++ 17. |
| [is_nothrow_invocable_r](is-invocable-classes.md) | Testuje, zda lze volat typ s použitím zadaných typů argumentů a že je známo, že nevyvolává výjimky, a výsledek je převeden na zadaný typ.<br/> Přidáno v C++ 17. |

Dotazování vlastností typu

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Získá zarovnání typu.|
|[pořadí](../standard-library/rank-class.md)|Získá počet rozměrů pole.|
|[stavební](../standard-library/extent-class.md)|Získá počet prvků v zadané dimenzi pole.|

Vztahy typů

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|Testuje, zda jsou dva typy stejné.|
|[is_base_of](../standard-library/is-base-of-class.md)|Testuje, zda je jeden typ základem jiného typu.|
|[is_convertible](../standard-library/is-convertible-class.md)|Testuje, zda je jeden typ převoditelné na jiný typ.|

Změny const-volatile

|||
|-|-|
|[add_const](../standard-library/add-const-class.md)|Vytvoří typ **const** z typu.|
|[add_volatile](../standard-library/add-volatile-class.md)|Vytvoří typ **volatile** z typu.|
|[add_cv](../standard-library/add-cv-class.md)|Vytvoří typ **const volatile** z typu.|
|[remove_const](../standard-library/remove-const-class.md)|Vytvoří typ, který není const, z typu.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Vytvoří typ, který není volatile typu.|
|[remove_cv](../standard-library/remove-cv-class.md)|Vytvoří nekonstantní typ, který není typu volatile.|

Úpravy odkazů

|||
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Vytvoří odkaz na typ z typu.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Vytvoří odkaz rvalue na typ z typu.|
|[remove_reference](../standard-library/remove-reference-class.md)|Vytvoří neodkazový typ z typu.|

Změny v podpisech

|||
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Vytvoří typ, pokud je podepsán, nebo nejmenší podepsaný typ, který je větší nebo roven velikosti pro typ.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Vytvoří typ bez znaménka nebo nejmenší typ bez znaménka, který je větší nebo roven velikosti pro typ.|

Úpravy pole

|||
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Vytvoří typ bez pole z typu pole.|
|[remove_extent](../standard-library/remove-extent-class.md)|Vytvoří typ elementu z typu pole.|

Úpravy ukazatelů

|||
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Vytvoří ukazatel na typ z typu.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Vytvoří typ z ukazatele na typ.|

Další transformace

|||
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Přiděluje neinicializovaná paměť pro zarovnaný typ.|
|[aligned_union](../standard-library/aligned-union-class.md)|Přidělí neinicializované paměti pro sjednocení, které je bez triviálního konstruktoru nebo destruktoru.|
|[common_type](../standard-library/common-type-class.md)|Vytvoří společný typ všech typů balíčku parametrů.|
|[podmíněného](../standard-library/conditional-class.md)|Pokud je podmínka pravdivá, vytvoří první zadaný typ, jinak specifikovaný typ.|
|[Decay](../standard-library/decay-class.md)|Vytvoří typ jako předaný hodnotou. Provede neodkazující, nekonstantní nebo nestálý typ nebo vytvoří ukazatel na typ.|
|[enable_if](../standard-library/enable-if-class.md)|Pokud je podmínka pravdivá, vytvoří zadaný typ, jinak žádný typ.|
|[invoke_result](invoke-result-class.md)|Určuje návratový typ typu volat, který přebírá zadané typy argumentů. <br/>Přidáno v C++ 17. |
|[result_of](../standard-library/result-of-class.md)|Určuje návratový typ typu volat, který přebírá zadané typy argumentů. <br/>Přidáno v C++ 14, zastaralé v C++ 17. |
|[underlying_type](../standard-library/underlying-type-class.md)|Vytvoří základní celočíselný typ pro typ výčtu.|

Vlastnosti logického operátoru

|||
|-|-|
|[souvislosti](../standard-library/conjunction-class.md)||
|[disjunkce](../standard-library/disjunction-class.md)||
|[negace](../standard-library/negation-class.md)||

## <a name="see-also"></a>Viz také:

[\<funkční >](../standard-library/functional.md)
