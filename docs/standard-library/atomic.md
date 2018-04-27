---
title: '&lt;Atomic&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
dev_langs:
- C++
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94a83c31b4e6e1d192d86961cb3ae7ee88f6ef24
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

Definuje třídy a třídy šablony sloužící k vytvoření typy, které podporují atomické operací.

## <a name="syntax"></a>Syntaxe

```cpp
#include <atomic>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který se zkompiluje pomocí **/CLR**, tuto hlavičku je blokovaný.

Atomická operace má dva klíčové vlastnosti, které vám pomůžou správně pracovat s objektu bez použití mutex zámky pomocí více vláken.

- Vzhledem k tomu, že nedělitelných atomická operace se druhá atomická operace na stejný objekt z jiného vlákna můžete získat stav objektu pouze před nebo po první atomické operace.

- Na základě jeho [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) argument, atomická operace vytvoří ve stejném vlákně, v řazení požadavky pro viditelnost důsledky další atomických operacích. V důsledku toho omezuje optimalizace kompilátoru, která porušují řazení požadavky.

Na některých platformách, nemusí být možné efektivně implementovat atomické operací pro některé typy bez použití `mutex` zámky. Atomickým typem je *uvolnění zámku* Pokud žádné atomické operací na daný typ používat zámky.

**C ++ 11**: V signál-obslužné rutiny můžete provádět atomické operací na objekt `obj` Pokud `obj.is_lock_free()` nebo `atomic_is_lock_free(x)` hodnotu true.

Třída [atomic_flag –](../standard-library/atomic-flag-structure.md) poskytuje minimální atomic typ, který obsahuje `bool` příznak. Jeho operace jsou vždy bez zámku.

Šablony třídy `atomic<T>` uloží objekt daného typu argument `T` a poskytuje atomic přístup k této uložené hodnoty. Můžete vytvořit instanci ho pomocí žádný typ, který je možné zkopírovat pomocí [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) a testovat rovnosti pomocí [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md). Konkrétně můžete ho s uživatelem definované typy, které tyto požadavky splňují a v mnoha případech s typy s plovoucí desetinnou čárkou.

Šablona má také sadu specializací pro integrální typy a částečná specializace pro ukazatele. Tyto specializací poskytují další operace, které nejsou k dispozici prostřednictvím primární šablony.

## <a name="pointer-specializations"></a>Specializací ukazatele

`atomic<T *>` Částečné specializací platí pro všechny typy ukazatelů. Poskytuje metody pro aritmetika ukazatele.

## <a name="integral-specializations"></a>Integrální specializací

`atomic<integral>` Specializací platí pro všechny integrální typy. Poskytují další operace, které nejsou k dispozici prostřednictvím primární šablony.

Každý `atomic<integral>` typ má odpovídající makro, které můžete použít v `if directive` k určení v době kompilace, zda jsou operací na daný typ uvolnění zámku. Pokud je hodnota makra nula, operace na typu nejsou uvolnění zámku. Pokud je hodnota 1, operace může být uvolnění zámku a modul runtime je vyžadována kontrola. Pokud je hodnota 2, jsou operace uvolnění zámku. Můžete použít funkci `atomic_is_lock_free` určit za běhu, zda jsou operací na typ uvolnění zámku.

Pro každou z celočíselných typů neexistuje odpovídající atomic typ s názvem, který spravuje objekt integrální typy. Každý `atomic_integral` typ má stejnou sadu členské funkce jako odpovídající instance `atomic<T>` a mohou být předána do žádné třetí atomic funkcí.

|`atomic_integral` Typ|Integrální typ.|`atomic_is_lock_free` – Makro|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|

Názvy typu TypeDef existovat pro specializací atomic šablony pro některé typy, které jsou definovány v hlavičce \<inttypes.h >.

|Atomickým typem.|Název definice TypeDef|
|-----------------|------------------|
|`atomic_int8_t`|`atomic<int8_t>`|
|`atomic_uint8_t`|`atomic<uint8_t>`|
|`atomic_int16_t`|`atomic<int16_t>`|
|`atomic_uint16_t`|`atomic<uint16_t>`|
|`atomic_int32_t`|`atomic<int32_t>`|
|`atomic_uint32_t`|`atomic<uint32_t>`|
|`atomic_int64_t`|`atomic<int64_t>`|
|`atomic_uint64_t`|`atomic<uint64_t>`|
|`atomic_int_least8_t`|`atomic<int_least8_t>`|
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|
|`atomic_int_least16_t`|`atomic<int_least16_t>`|
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|
|`atomic_int_least32_t`|`atomic<int_least32_t>`|
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|
|`atomic_int_least64_t`|`atomic<int_least64_t>`|
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|
|`atomic_intptr_t`|`atomic<intptr_t>`|
|`atomic_uintptr_t`|`atomic<uintptr_t>`|
|`atomic_size_t`|`atomic<size_t>`|
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|
|`atomic_intmax_t`|`atomic<intmax_t>`|
|`atomic_uintmax_t`|`atomic<uintmax_t>`|

## <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[atomic – struktura](../standard-library/atomic-structure.md)|Popisuje objekt, který provádí atomické operací na uložené hodnoty.|
|[atomic_flag – struktura](../standard-library/atomic-flag-structure.md)|Popisuje, objektu, která atomicky nastaví a vymaže `bool` příznak.|

## <a name="enums"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[memory_order – výčet](../standard-library/atomic-enums.md#memory_order_enum)|Poskytuje symbolické názvy pro operace synchronizace v umístění v paměti. Tyto operace ovlivňují, jak budou zobrazeny v jiném přiřazení v jedno vlákno.|

## <a name="functions"></a>Funkce

V následujícím seznamu funkcí, které nekončí v `_explicit` mít sémantika odpovídající `_explicit`kromě toho, že mají implicitní [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) argumenty `memory_order_seq_cst`.

|Název|Popis|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|Provede *atomic porovnání a exchange* operaci.|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|Provede *atomic porovnání a exchange* operaci.|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|Provede *weak atomic porovnat a exchange* operaci.|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|Provede *weak atomic porovnat a exchange* operaci.|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|Nahradí hodnotu uložené.|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|Nahradí hodnotu uložené.|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|Přidá zadanou hodnotu do existující uložené hodnoty.|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|Přidá zadanou hodnotu do existující uložené hodnoty.|
|[atomic_fetch_and –](../standard-library/atomic-functions.md#atomic_fetch_and)|Provede bitové `and` na zadanou hodnotu a existující uložené hodnoty.|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|Provede bitové `and` na zadanou hodnotu a existující uložené hodnoty.|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|Provede bitové `or` na zadanou hodnotu a existující uložené hodnoty.|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|Provede bitové `or` na zadanou hodnotu a existující uložené hodnoty.|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|Odečte zadanou hodnotu z existující uložené hodnoty.|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|Odečte zadanou hodnotu z existující uložené hodnoty.|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|Provede bitové `exclusive or` na zadanou hodnotu a existující uložené hodnoty.|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|Provede bitové `exclusive or` na zadanou hodnotu a existující uložené hodnoty.|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|Nastaví příznak `atomic_flag` do objektu `false`.|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|Nastaví příznak `atomic_flag` do objektu `false`.|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|Nastaví příznak `atomic_flag` do objektu `true`.|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|Nastaví příznak `atomic_flag` do objektu `true`.|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|Nastaví hodnotu uloženou v `atomic` objektu.|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|Určuje, zda jsou atomické operací na zadaný objekt bez zámku.|
|[atomic_load –](../standard-library/atomic-functions.md#atomic_load)|Atomicky načte hodnotu.|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|Atomicky načte hodnotu.|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|Funguje jako *ochranná* , vytváří paměti řazení mezi ochranné v volání vláken, která má obslužné rutiny signál provést ve stejném vlákně.|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|Atomicky ukládá hodnotu.|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|Atomicky ukládá hodnotu.|
|[atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence)|Funguje jako *ochranná* , vytváří řazení požadavky s ohledem na ostatní ochranné paměti.|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|Dělí řetězec možných závislostí.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
