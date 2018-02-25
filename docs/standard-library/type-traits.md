---
title: '&lt;type_traits&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <type_traits>
dev_langs:
- C++
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 932c30ade2e6aaf1f07c878a0f6ee8960e9c83d8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;
Definuje šablony, které poskytují kompilaci konstanty, které poskytují informace o vlastnostech jejich argumenty typu nebo vytvořit transformována typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <type_traits>  
```  
  
## <a name="remarks"></a>Poznámky  
 Třídy a šablon v nástroji `<type_traits>` slouží k podpoře odvození typu, klasifikace a transformace při kompilaci, ke zjištění chyby související s typem a které vám pomůžou optimalizovat obecném kódu. Tyto třídy a šablony zahrnují unární typové vlastnosti popisující vlastnost typu, binární typové vlastnosti, které popisují vztah mezi typy a transformaci vlastnosti, které upravují vlastnost typu.  
  
 Pro typové vlastnosti pomocná třída, podporu `integral_constant`, je definovaný. Obsahuje šablony specializací `true_type` a `false_type` , tvoří základní třídy pro typ predikáty. A *predikátem typu* je šablonu, která má jeden nebo více argumenty typu. Pokud predikát typ *platí*, je veřejně odvozený, přímo ani nepřímo, z [true_type –](../standard-library/type-traits-typedefs.md#true_type). Pokud predikát typ *obsahuje false*, je veřejně odvozený, přímo ani nepřímo, z [false_type –](../standard-library/type-traits-typedefs.md#false_type).  
  
 A *modifikátor typu* nebo *transformace znak* šablonu, která přijímá jeden nebo více argumentů šablony a má jednoho člena, `type`, což je synonymum pro změny typu.  
  
### <a name="alias-templates"></a>Alias šablony  
 Pro zjednodušení výrazy typu vlastnosti, [alias šablony](../cpp/aliases-and-typedefs-cpp.md) pro `typename some_trait<T>::type` jsou k dispozici, kde " `some_trait`" je název třídy šablony. Například [add_const](../standard-library/add-const-class.md) má šablonu alias pro tento typ `add_const_t`definovaná jako:  
  
```cpp  
template <class T>
using add_const_t = typename add_const<T>::type;
```  
  
|||||  
|-|-|-|-|  
|add_const_t|aligned_storage_t|make_signed_t|remove_pointer_t|  
|add_cv_t|aligned_union_t|make_unsigned_t|remove_reference_t|  
|add_lvalue_reference_t|common_type_t|remove_all_extents_t|remove_volatile_t|  
|add_pointer_t|conditional_t|remove_const_t|result_of_t|  
|add_rvalue_reference_t|decay_t|remove_cv_t|underlying_type_t|  
|add_volatile_t|enable_if_t|remove_extent_t||  
  
### <a name="classes"></a>Třídy  
 Pomocná třída a definice TypeDef  
  
|||  
|-|-|  
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Díky integrální konstanta z typu a hodnotu.|  
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Obsahuje integrální konstanta s hodnota true.|  
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Obsahuje integrální konstanta se hodnota false.|  
  
 Primární typ kategorie  
  
|||  
|-|-|  
|[is_void](../standard-library/is-void-class.md)|Kontroluje, zda je typ `void`.|  
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Kontroluje, zda je typ `std::nullptr_t`.|  
|[is_integral](../standard-library/is-integral-class.md)|Ověřuje, zda je nedílnou součástí typu.|  
|[is_floating_point](../standard-library/is-floating-point-class.md)|Ověřuje, zda je typ s plovoucí desetinnou čárkou.|  
|[is_array](../standard-library/is-array-class.md)|Ověřuje, zda je typ pole.|  
|[is_pointer](../standard-library/is-pointer-class.md)|Ověřuje, zda je ukazatel typu.|  
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Testy, pokud je typ odkazu lvalue.|  
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Testy, pokud je typ deklarátor odkazu.|  
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Ověřuje, zda je typ ukazatele na člena objekt.|  
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Ověřuje, zda je typ ukazatel na členské funkce.|  
|[is_enum](../standard-library/is-enum-class.md)|Ověřuje, zda je typ výčtu.|  
|[is_union](../standard-library/is-union-class.md)|Ověřuje, zda je typ spojení.|  
|[is_class](../standard-library/is-class-class.md)|Ověřuje, zda je typ třídy.|  
|[is_function](../standard-library/is-function-class.md)|Ověřuje, zda typ je typ funkce.|  
  
 Kategorie složeného typu  
  
|||  
|-|-|  
|[is_reference](../standard-library/is-reference-class.md)|Ověřuje, zda je typu odkaz.|  
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Ověřuje, zda je typ aritmetické.|  
|[is_fundamental](../standard-library/is-fundamental-class.md)|Kontroluje, zda je typ `void` nebo aritmetické.|  
|[is_object](../standard-library/is-object-class.md)|Ověřuje, zda typ je typ objektu.|  
|[is_scalar](../standard-library/is-scalar-class.md)|Ověřuje, zda je typ skalární.|  
|[is_compound](../standard-library/is-compound-class.md)|Ověřuje, zda typ není skalární.|  
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Ověřuje, zda je ukazatel na člena typu.|  
  
 Vlastnosti typu  
  
|||  
|-|-|  
|[is_const](../standard-library/is-const-class.md)|Kontroluje, zda je typ `const`.|  
|[is_volatile](../standard-library/is-volatile-class.md)|Kontroluje, zda je typ `volatile`.|  
|[is_trivial](../standard-library/is-trivial-class.md)|Ověřuje, zda je typ jednoduchá.|  
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Ověřuje, zda je typ trivially kopírovatelná.|  
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Testy, pokud typ je typ standardní rozložení.|  
|[is_pod](../standard-library/is-pod-class.md)|Ověřuje, zda je typ POD.|  
|[is_literal_type](../standard-library/is-literal-type-class.md)|Kontroluje, zda lze zadat `constexpr` proměnnou nebo používá `constexpr` funkce.|  
|[is_empty](../standard-library/is-empty-class.md)|Ověřuje, zda je typ prázdný třída.|  
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Ověřuje, zda typ není polymorfní třídy.|  
|[is_abstract](../standard-library/is-abstract-class.md)|Ověřuje, zda je typ abstraktní třída.|  
|[is_final](../standard-library/is-final-class.md)|Kontroluje, zda typ je typ třídy označena `final`.|  
|[is_signed](../standard-library/is-signed-class.md)|Ověřuje, zda typ se znaménkem.|  
|[is_unsigned](../standard-library/is-unsigned-class.md)|Ověřuje, zda je typ celé číslo bez znaménka.|  
|[is_constructible](../standard-library/is-constructible-class.md)|Ověřuje, zda je typ zkonstruovatelný pomocí zadané typy argumentů.|  
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Ověřuje, zda má tento typ výchozí konstruktor.|  
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Ověřuje, zda má tento typ konstruktor kopírování.|  
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Ověřuje, zda má tento typ konstruktor move.|  
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Ověřuje, zda je první typ lze přiřadit hodnotu druhého typu.|  
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Ověřuje, zda typ lze přiřadit hodnotu const odkaz typu.|  
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Ověřuje, zda typ lze přiřadit deklarátor odkazu hodnoty typu.|  
|[is_destructible](../standard-library/is-destructible-class.md)|Ověřuje, zda je typ zničitelné.|  
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Ověřuje, zda typ používá žádné netriviální operace-li vytvořená pomocí zadaným typům.|  
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Ověřuje, zda typ používá žádné netriviální operace-li výchozí vytvořená.|  
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Ověřuje, zda typ používá žádné netriviální operace-li kopie vytvořená.|  
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Ověřuje, zda typ používá žádné netriviální operace, při přesunutí zkonstruovat.|  
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Ověřuje, zda jsou typy Přiřaditelné a přiřazení používá žádné netriviální operace.|  
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Testy, zda je typ kopie přiřadit a přiřazení používá žádné netriviální operace.|  
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Testy, zda je typ přesunutí přiřadit a přiřazení používá žádné netriviální operace.|  
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Ověřuje, zda je typ zničitelné a destruktoru používá žádné netriviální operace.|  
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Ověřuje, zda je typ zkonstruovatelný a není znám výjimku při vytvářeny pomocí zadaným typům.|  
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Testy jestli je typ výchozí zkonstruovatelný a není znám výjimku při sestavený výchozí.|  
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Ověřuje, zda typ je kopie zkonstruovatelný a je zřejmé, že konstruktor copy není výjimku.|  
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Ověřuje, zda je typ přesunutí zkonstruovatelný a je zřejmé, že konstruktor move není výjimku.|  
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Ověřuje, zda je typ přiřadit pomocí zadaného typu a přiřazení není znám výjimku.|  
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Ověřuje, zda typ je kopie přiřadit a je zřejmé, že přiřazení není výjimku.|  
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Ověřuje, zda typ je přesunout přiřadit a je zřejmé, že přiřazení není výjimku.|  
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Ověřuje, zda je typ zničitelné a je zřejmé, že destruktoru není výjimku.|  
|[has_virtual_destructor](http://msdn.microsoft.com/en-us/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|Ověřuje, zda má tento typ virtuální destruktor.|  
  
 Dotazy na vlastnosti typu  
  
|||  
|-|-|  
|[alignment_of](../standard-library/alignment-of-class.md)|Získá zarovnání typu.|  
|[Pořadí](../standard-library/rank-class.md)|Získá počet rozměry pole.|  
|[extent](../standard-library/extent-class.md)|Získá počet elementů v dimenzi zadané pole.|  
  
 Vztahy typu  
  
|||  
|-|-|  
|[is_same](../standard-library/is-same-class.md)|Ověřuje, zda dva typy jsou stejné.|  
|[is_base_of](../standard-library/is-base-of-class.md)|Ověřuje, zda je jeden typ základní jiného.|  
|[is_convertible](../standard-library/is-convertible-class.md)|Ověřuje, zda je jeden typ převést do jiného.|  
  
 Úpravy const volatile  
  
|||  
|-|-|  
|[add_const](../standard-library/add-const-class.md)|Vytváří `const` typ z typu.|  
|[add_volatile](../standard-library/add-volatile-class.md)|Vytváří `volatile` typ z typu.|  
|[add_cv](../standard-library/add-cv-class.md)|Vytváří `const volatile` typ z typu.|  
|[remove_const](../standard-library/remove-const-class.md)|Vytvoří typ bez const z typu.|  
|[remove_volatile](../standard-library/remove-volatile-class.md)|Vytvoří typ stálé z typu.|  
|[remove_cv](../standard-library/remove-cv-class.md)|Vytvoří typ stálé bez const z typu.|  
  
 Referenční dokumentace úpravy  
  
|||  
|-|-|  
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Vytvoří odkaz na typ z typu.|  
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Vytvoří odkaz na typ z typu rvalue|  
|[remove_reference](../standard-library/remove-reference-class.md)|Vytvoří typu bez odkazu z typu.|  
  
 Úpravy přihlášení  
  
|||  
|-|-|  
|[make_signed](../standard-library/make-signed-class.md)|Vytvoří typ, pokud je podepsaný nebo nejmenší podepsaný typu větší než nebo rovna velikosti typu.|  
|[make_unsigned](../standard-library/make-unsigned-class.md)|Vytvoří typ, pokud je bez znaménka nebo nejmenší typu bez znaménka větší než nebo rovna velikosti typu.|  
  
 Pole úprav  
  
|||  
|-|-|  
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Vytvoří typ mimo pole z typu pole.|  
|[remove_extent](../standard-library/remove-extent-class.md)|Vytvoří typ element z typu pole.|  
  
 Úpravy ukazatele  
  
|||  
|-|-|  
|[add_pointer](../standard-library/add-pointer-class.md)|Vytvoří ukazatel na typ z typu.|  
|[remove_pointer](../standard-library/remove-pointer-class.md)|Vytvoří typ z ukazatel na typ.|  
  
 Další transformace  
  
|||  
|-|-|  
|[aligned_storage](../standard-library/aligned-storage-class.md)|Přidělí Neinicializovaný paměť pro typ zarovnaný.|  
|[aligned_union](../standard-library/aligned-union-class.md)|Zarovnaný – typ union netriviální konstruktor nebo destruktor přidělí neinicializované paměti.|  
|[common_type](../standard-library/common-type-class.md)|Vytvoří typ běžné všech typů sady parametrů.|  
|[Podmíněné](../standard-library/conditional-class.md)|Pokud je podmínka pravdivá, vytvoří první zadaný typ, jinak druhý zadaného typu.|  
|[decay](../standard-library/decay-class.md)|Vytvoří typ jako předaná hodnota. Díky – referenční dokumentace, bez const nebo stálé typ nebo je ukazatel typu.|  
|[enable_if](../standard-library/enable-if-class.md)|Pokud je podmínka pravdivá, vytváří zadaný typ, jinak žádný typ.|  
|[result_of](../standard-library/result-of-class.md)|Určuje návratový typ s typ, který má zadané typy argumentů.|  
|[underlying_type](../standard-library/underlying-type-class.md)|Vytvoří základní integrální typ pro typ výčtu.|  
  
## <a name="see-also"></a>Viz také  
 [\<funkční >](../standard-library/functional.md)



