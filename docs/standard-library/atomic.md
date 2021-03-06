---
title: '&lt;atomic&gt;'
description: Popisuje typy a funkce, které jsou k dispozici v atomické C++ hlavičce standardní knihovny.
ms.date: 12/06/2019
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
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
ms.openlocfilehash: d11e8bf2067c1c8525725ae74e713ac834d89ec4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991163"
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

Definuje třídy a šablony tříd, které se použijí k vytváření typů, které podporují atomické operace.

## <a name="syntax"></a>Syntaxe

```cpp
#include <atomic>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován pomocí [/clr: Pure](../build/reference/clr-common-language-runtime-compilation.md), je tato hlavička zablokována. Možnosti **/clr: Pure** a **/clr: Safe** jsou v aplikaci Visual Studio 2017 a novějších verzích zastaralé.

Atomická operace má dvě klíčové vlastnosti, které vám pomůžou použít více vláken pro správné manipulaci s objektem bez použití zámků mutex.

- Vzhledem k tomu, že atomická operace je nedělitelná, druhá atomická operace na stejném objektu z jiného vlákna může získat stav objektu pouze před nebo po první atomickou operaci.

- Na základě jeho [memory_orderho](../standard-library/atomic-enums.md#memory_order_enum) argumentu vytváří atomická operace požadavky na řazení pro viditelnost účinků jiných atomických operací ve stejném vlákně. V důsledku toho znemožňuje optimalizace kompilátoru, které porušují požadavky na řazení.

Na některých platformách nemusí být možné efektivně implementovat atomické operace pro některé typy bez použití zámků `mutex`. Atomický typ je *bez zámku* , pokud žádné atomické operace na tomto typu nepoužívají zámky.

**C++ 11**: v obslužných rutinách signálu můžete provádět atomické operace s objektem `obj`, pokud jsou hodnoty `obj.is_lock_free()` nebo `atomic_is_lock_free(x)` pravdivé.

Třída [atomic_flag](../standard-library/atomic-flag-structure.md) poskytuje minimální atomická typ, který obsahuje příznak **bool** . Jeho operace jsou vždycky bez zámků.

Šablona třídy `atomic<T>` ukládá objekt jeho typu argumentu `T` a poskytuje atomický přístup k této uložené hodnotě. Můžete vytvořit instanci pomocí libovolného typu, který lze kopírovat pomocí [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) a testovat pro rovnost pomocí [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md). Konkrétně jej můžete použít s uživatelsky definovanými typy, které splňují tyto požadavky, a v mnoha případech s typy s plovoucí desetinnou čárkou.

Šablona má také sadu specializací pro celočíselné typy a částečnou specializaci pro ukazatele. Tyto specializace poskytují další operace, které nejsou k dispozici prostřednictvím primární šablony.

## <a name="pointer-specializations"></a>Specializace ukazatelů

`atomic<T *>` částečné specializace se vztahují na všechny typy ukazatelů. Poskytují metody pro aritmetický ukazatel.

## <a name="integral-specializations"></a>Celočíselné specializace

`atomic<integral>` specializace se vztahují na všechny celočíselné typy. Poskytují další operace, které nejsou k dispozici prostřednictvím primární šablony.

Každý typ `atomic<integral>` má odpovídající makro, které lze použít v `if directive` k určení v době kompilace, zda jsou operace s tímto typem bez zámků. Pokud je hodnota makra nula, operace s typem nejsou bez zámku. Pokud je hodnota 1, operace můžou být bez zámků a je nutná kontrolní doba. Pokud je hodnota 2, operace se zablokují bez zámků. Funkci `atomic_is_lock_free` lze použít k určení za běhu, zda jsou operace s typem bez zámku.

Pro každý z celočíselných typů existuje odpovídající pojmenovaný typ Atom, který spravuje objekt daného integrálního typu. Každý typ `atomic_integral` má stejnou sadu členských funkcí jako odpovídající instance `atomic<T>` a může být předán do kterékoli nečlenské atomické funkce.

|Typ `atomic_integral`|Celočíselný typ|`atomic_is_lock_free` – makro|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|**char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_schar`|**signed char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_uchar`|**znak bez znaménka**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_char16_t`|`char16_t`|ATOMIC_CHAR16_T_LOCK_FREE|
|`atomic_char32_t`|`char32_t`|ATOMIC_CHAR32_T_LOCK_FREE|
|`atomic_wchar_t`|**wchar_t**|ATOMIC_WCHAR_T_LOCK_FREE|
|`atomic_short`|**short**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_ushort`|**krátký unsigned**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_int`|**int**|ATOMIC_INT_LOCK_FREE|
|`atomic_uint`|**unsigned int**|ATOMIC_INT_LOCK_FREE|
|`atomic_long`|**long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_ulong`|**unsigned long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_llong`|**Long Long**|ATOMIC_LLONG_LOCK_FREE|
|`atomic_ullong`|**dlouhý unsigned long**|ATOMIC_LLONG_LOCK_FREE|

Názvy typedef existují pro specializace šablony atomie pro některé typy, které jsou definovány v hlavičce \<inttypes. h >.

|Typ atomické|Název typedef|
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

|Name|Popis|
|----------|-----------------|
|[atomic – struktura](../standard-library/atomic-structure.md)|Popisuje objekt, který provádí atomické operace s uloženou hodnotou.|
|[atomic_flag – struktura](../standard-library/atomic-flag-structure.md)|Popisuje objekt, který atomicky nastavuje a maže příznak **bool** .|

## <a name="enums"></a>Výčty

|Name|Popis|
|----------|-----------------|
|[Výčet memory_order](../standard-library/atomic-enums.md#memory_order_enum)|Poskytuje symbolické názvy pro operace synchronizace v paměťových místech. Tyto operace ovlivní, jak budou přiřazení v jednom vlákně viditelná v jiném.|

## <a name="functions"></a>Funkce

V následujícím seznamu funkce, které nekončí `_explicit` mají sémantiku odpovídající `_explicit`, s tím rozdílem, že mají implicitní [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty `memory_order_seq_cst`.

|Name|Popis|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|Provádí operaci *atomické porovnání a výměny* .|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|Provádí operaci *atomické porovnání a výměny* .|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|Provede *slabě atomická operace porovnání a výměny* .|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|Provede *slabě atomická operace porovnání a výměny* .|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|Nahradí uloženou hodnotu.|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|Nahradí uloženou hodnotu.|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|Přidá zadanou hodnotu do existující uložené hodnoty.|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|Přidá zadanou hodnotu do existující uložené hodnoty.|
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|Provede bitovou `and` na zadané hodnotě a existující uloženou hodnotu.|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|Provede bitovou `and` na zadané hodnotě a existující uloženou hodnotu.|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|Provede bitovou `or` na zadané hodnotě a existující uloženou hodnotu.|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|Provede bitovou `or` na zadané hodnotě a existující uloženou hodnotu.|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|Odečte zadanou hodnotu od stávající uložené hodnoty.|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|Odečte zadanou hodnotu od stávající uložené hodnoty.|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|Provede bitovou `exclusive or` na zadané hodnotě a existující uloženou hodnotu.|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|Provede bitovou `exclusive or` na zadané hodnotě a existující uloženou hodnotu.|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|Nastaví příznak v objektu `atomic_flag` na **hodnotu false**.|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|Nastaví příznak v objektu `atomic_flag` na **hodnotu false**.|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|Nastaví příznak v objektu `atomic_flag` na **hodnotu true**.|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|Nastaví příznak v objektu `atomic_flag` na **hodnotu true**.|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|Nastaví uloženou hodnotu v objektu `atomic`.|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|Určuje, zda jsou atomické operace se zadaným objektem bez zámku.|
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|Atomicky načte hodnotu.|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|Atomicky načte hodnotu.|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|Slouží jako *plot* , který vytváří požadavky na řazení paměti mezi ploty ve volajícím vlákně, které má obslužné rutiny signálu provedeny ve stejném vlákně.|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|Atomicky ukládá hodnotu.|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|Atomicky ukládá hodnotu.|
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|Funguje jako *ochranná* paměť, která vytváří požadavky na řazení paměti s ohledem na jiné ploty.|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|Rozdělí možný řetěz závislostí.|

## <a name="see-also"></a>Viz také:

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
