---
title: Namespace souběžnosti (C++ AMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b22650e87863a659ad3f36d6632776130bc6558
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396741"
---
# <a name="concurrency-namespace-c-amp"></a>Obor názvů souběžnosti (C++ AMP)

Poskytuje třídy a funkce urychlující spuštění kódu jazyka C++ na datově paralelním hardwaru. Další informace najdete v tématu [přehled modelu C++ AMP](../cpp-amp-overview.md)

## <a name="syntax"></a>Syntaxe

```
namespace Concurrency;
```

## <a name="members"></a>Členové

### <a name="namespaces"></a>Jmenné prostory

|Název|Popis|
|----------|-----------------|
|[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)|Poskytuje funkce podporující spolupráci rozhraní D3D. Umožňuje bezproblémové použití zdrojů rozhraní D3D pro výpočty v kódu AMP a využívání prostředků vytvořených v knihovně AMP v kódu D3D bez nutnosti vytvářet nadbytečné pomocné kopie. C++ AMP můžete postupně urychlovat provádění výpočetně náročných oddílů DirectX aplikace a použít rozhraní D3D API nad daty vytvořenými výpočty AMP.|
|[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)|Funkce v `fast_math` oboru názvů nejsou kompatibilní s normou C99. Jsou k dispozici pouze jednoduchou přesnost verze jednotlivých funkcí. Tyto funkce používají vnitřní funkce rozhraní DirectX, které jsou rychlejší než odpovídající funkce v `precise_math` obor názvů a nevyžadují rozšířenou podporu dvojité přesnosti v akcelerátoru, ale jsou méně přesné. Existují dvě verze jednotlivých funkcí pro kompatibilitu na úrovni zdroje s kódem C99; obě verze přebírají a vracejí hodnoty s jednoduchou přesností.|
|[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)|Poskytuje typy a funkce, které jsou navržené pro grafické programování.|
|[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)|Funkce v `precise_math` obor názvů jsou kompatibilní s normou C99. Verze jednoduchou a dvojitou přesností jednotlivých funkcí jsou zahrnuty. Tyto funkce – to zahrnuje funkce jednoduchou přesností, vyžadují rozšířenou podporu dvojité přesnosti v akcelerátoru.|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[accelerator – třída](accelerator-class.md)|Představuje abstrakcí fyzického DP-optimalizovaného výpočetního uzlu.|
|[accelerator_view – třída](accelerator-view-class.md)|Představuje abstrakci virtuálního zařízení v akcelerátoru paralelních dat knihovny C++ AMP.|
|[accelerator_view_removed – třída](accelerator-view-removed-class.md)|Výjimka, která je vyvolána, když podkladové volání rozhraní DirectX selže z důvodu vypršení časového limitu detekce – obnovení mechanismus Windows.|
|[array – třída](array-class.md)|Souhrn dat na `accelerator_view` v doméně mřížky. Jde o kolekci proměnných, jedna pro každý prvek v doméně mřížky. Každá proměnná obsahuje hodnotu odpovídající některému typu jazyka C++.|
|[array_view – třída](array-view-class.md)|Představuje pohled na data v poli\<T, N >.|
|[completion_future – třída](completion-future-class.md)|Představuje budoucí odpovídající asynchronní operaci C++ AMP.|
|[extent – třída](extent-class.md)|Představuje vektor N celočíselných hodnot určujících hranice N-rozměrný prostoru s počátkem 0. Hodnoty ve vektoru souřadnic jsou seřazeny od nejvýznamnější po nejméně významnou. Například v Kartézském 3rozměrného prostoru představuje vektor rozsahu (7,5,3) prostor, v němž souřadnice z rozsahu od 0 do 7, souřadnice y rozsahu od 0 do 5, a souřadnice x rozsahu od 0 do 3.|
|[index – třída](index-class.md)|Definuje N-rozměrný bod indexu.|
|[invalid_compute_domain – třída](invalid-compute-domain-class.md)|Výjimka, která je vyvolána, když modul runtime nemůže spustit jádro za použití výpočetní domény určené na `parallel_for_each` lokalitu volání.|
|[out_of_memory – třída](out-of-memory-class.md)|Výjimka, která je vyvolána výjimka, jestliže metoda selže z důvodu nedostatku paměti systém nebo zařízení.|
|[runtime_exception – třída](runtime-exception-class.md)|Základní typ výjimky v knihovně C++ AMP.|
|[tile_barrier – třída](tile-barrier-class.md)|Třída, která je možné vytvořit v systému a je předána do dlaždicového `parallel_for_each` lambda jako součást `tiled_index` parametru. Poskytuje jednu metodu `wait()`, jehož účelem je synchronizovat provádění vláken spuštěných ve skupině vláken (bloku).|
|[tiled_extent – třída](tiled-extent-class.md)|A `tiled_extent` je objekt `extent` objekt dimenze jedné do tří, který rozděluje rozsah prostoru do jednorozměrných, dvourozměrných nebo třírozměrných dlaždic.|
|[tiled_index – třída](tiled-index-class.md)|Poskytuje index do `tiled_grid` objektu. Tato třída obsahuje vlastnosti pro přístup k elementu vzhledem k místnímu původu bloku a ke globálnímu původu.|
|[uninitialized_object – třída](uninitialized-object-class.md)|Výjimka, která je vyvolána při použití neinicializovaného objektu.|
|[unsupported_feature – třída](unsupported-feature-class.md)|Výjimka, která je vyvolána při použití nepodporované funkce.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[access_type – výčet](concurrency-namespace-enums-amp.md#access_type)|Určuje typ přístupu k datům.|
|[queuing_mode – výčet](concurrency-namespace-enums-amp.md#queuing_mode)|Určuje režimy zařazování do fronty, které jsou podporovány v akcelerátoru.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|--------------|-----------------|
|[Operator == – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Určuje, zda zadané datové struktury jsou stejné.|
|[Operator! = – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|Určuje, zda zadané datové struktury nestejné.|
|[Operator + – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|Vypočítá součet zadaných argumentů podle komponent.|
|[Operator-– operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|Vypočítá rozdíl mezi zadanými argumenty podle komponent.|
|[Operator * – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|Vypočítá součin zadaných argumentů.|
|[Operator / – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|Vypočítá podíl zadaných argumentů podle komponent.|
|[Operator % – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|Vypočítá zbytek z prvního zadaného argumentu pomocí druhého zadaného argumentu.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[all_memory_fence –](concurrency-namespace-functions-amp.md#all_memory_fence)|Pozastaví spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do paměti.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Zruší inicializaci modulu runtime C++ AMP.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Přetíženo. Pokud hodnotu uloženou v zadaném umístění při porovnání rovna první zadané hodnotě, tak druhá zadaná hodnota je uložená ve stejném umístění jako atomická operace.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na součet dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[atomic_fetch_and –](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na bitové `and` z dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Přetíženo. Sníží hodnotu uloženou v zadaném umístění a výsledek je uložen na stejném umístění jako atomická operace.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Přetíženo. Zvýší hodnotu uloženou v zadaném umístění a výsledek je uložen na stejném umístění jako atomická operace.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na větší z dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na menší z dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na bitové `or` z dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na rozdíl dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na bitové `xor` z dané hodnoty a určitou hodnotu jako atomickou operaci.|
|[kopírování](concurrency-namespace-functions-amp.md#copy)|Zkopíruje objekt jazyka C++ AMP. Jsou splněny všechny požadavky synchronního přenosu dat. Data nelze kopírovat, pokud kód spouští kód na akcelerátoru. Obecný tvar této funkce je `copy(src, dest)`.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Zkopíruje objekt jazyka C++ AMP a vrátí [completion_future](completion-future-class.md) , který lze čekat. Data nelze kopírovat, pokud je kód spuštěn na akcelerátoru. Obecný tvar této funkce je `copy(src, dest)`.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Zruší spuštění funkce, která má `restrict(amp)` podmínkou.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Vytiskne formátovaný řetězec pro Visual Studio **výstup** okno a vyvolá [runtime_exception](runtime-exception-class.md) výjimku, která má stejné formátování řetězce.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Vytiskne formátovaný řetězec pro Visual Studio **výstup** okna. Je volána z funkce, která má `restrict(amp)` podmínkou.|
|[global_memory_fence –](concurrency-namespace-functions-amp.md#global_memory_fence)|Pozastaví spuštění všech vláken v dlaždici, dokud nejsou všechny globální přístupy dokončeny.|
|[parallel_for_each – funkce (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|Spustí funkci napříč výpočetní doménou.|
|[tile_static_memory_fence –](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Pozastaví spuštění všech vláken v bloku, dokud `tile_static` nejsou dokončeny přístupy do paměti.|

## <a name="constants"></a>Konstanty

|Název|Popis|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS Constant](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Maximální počet vyrovnávacích pamětí povolených rozhraním DirectX.|
|[MODULENAME_MAX_LENGTH – konstanta](concurrency-namespace-constants-amp.md#modulename_max_length)|Ukládá maximální délku názvu modulu. Tato hodnota musí být stejná v kompilátoru a modulu runtime.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

## <a name="see-also"></a>Viz také

[Referenční dokumentace (C++ AMP)](reference-cpp-amp.md)

