---
title: Obor názvů souběžnosti (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139372"
---
# <a name="concurrency-namespace-c-amp"></a>Obor názvů souběžnosti (C++ AMP)

Poskytuje třídy a funkce, které urychlují spouštění C++ kódu na datovém paralelním hardwaru. Další informace najdete v tématu [ C++ věnovaném amp Overview.](../cpp-amp-overview.md)

## <a name="syntax"></a>Syntaxe

```cpp
namespace Concurrency;
```

## <a name="members"></a>Členové

### <a name="namespaces"></a>Obory názvů

|Název|Popis|
|----------|-----------------|
|[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)|Poskytuje funkce, které podporují interoperabilitu rozhraní D3D. Umožňuje bezproblémové použití prostředků D3D k výpočtům v kódu AMP a používání prostředků vytvořených v AMP v kódu D3D bez vytváření redundantních pomocných kopií. Pomocí C++ amp můžete postupně zrychlit výpočetní a náročné oddíly aplikací rozhraní DirectX a použít rozhraní D3D API pro data vytvořená z výpočtů amp.|
|[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)|Funkce v oboru názvů `fast_math` nejsou kompatibilní s C99. K dispozici jsou pouze verze s jednoduchou přesností jednotlivých funkcí. Tyto funkce používají vnitřní funkce rozhraní DirectX, které jsou rychlejší než odpovídající funkce v oboru názvů `precise_math` a nevyžadují rozšířenou podporu s dvojitou přesností v akcelerátoru, ale jsou méně přesné. Existují dvě verze každé funkce pro kompatibilitu na úrovni zdroje s C99 kódem. obě verze přebírají a vracejí hodnoty s jednoduchou přesností.|
|[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)|Poskytuje typy a funkce navržené pro grafické programování.|
|[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)|Funkce v oboru názvů `precise_math` C99 kompatibilní. Součástí jsou i verze s jednoduchou přesností a dvojitou přesností jednotlivých funkcí. Tyto funkce – to zahrnuje funkce s jednoduchou přesností – vyžaduje rozšířenou podporu dvojité přesnosti v akcelerátoru.|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[accelerator – třída](accelerator-class.md)|Představuje abstrakci fyzického výpočetního uzlu optimalizovaného pro DP.|
|[accelerator_view – třída](accelerator-view-class.md)|Představuje abstrakci virtuálního zařízení v akcelerátoru C++ paralelního zpracování dat amp.|
|[accelerator_view_removed – třída](accelerator-view-removed-class.md)|Výjimka, která je vyvolána, když se podkladové volání rozhraní DirectX nepovede kvůli mechanismu detekce a obnovení časového limitu systému Windows.|
|[array – třída](array-class.md)|Agregace dat na `accelerator_view` v doméně mřížky. Jedná se o kolekci proměnných, jednu pro každý prvek v doméně mřížky. Každá proměnná obsahuje hodnotu, která odpovídá nějakému C++ typu.|
|[array_view – třída](array-view-class.md)|Představuje zobrazení dat v poli\<T, N >.|
|[completion_future – třída](completion-future-class.md)|Představuje budoucnost, která odpovídá asynchronní operaci C++ amp.|
|[extent – třída](extent-class.md)|Představuje vektor N celočíselných hodnot, které určují meze N-dimenzionálního prostoru, který má počátek 0. Hodnoty ve vektoru souřadnic jsou seřazeny od nejvýznamnější po nejméně významnou. Například v kartézském trojrozměrném prostoru představuje vektor rozsahu (7, 5, 3) mezeru, ve které souřadnice z v rozsahu od 0 do 7, souřadnice y se pohybuje od 0 do 5 a souřadnice x rozsahu od 0 do 3.|
|[index – třída](index-class.md)|Definuje N-dimenzionální bod indexu.|
|[invalid_compute_domain – třída](invalid-compute-domain-class.md)|Výjimka, která je vyvolána, když modul runtime nemůže spustit jádro pomocí výpočetní domény zadané na webu `parallel_for_each` volání.|
|[out_of_memory – třída](out-of-memory-class.md)|Výjimka, která je vyvolána, když je metoda neúspěšná z důvodu nedostatku paměti systému nebo zařízení.|
|[runtime_exception – třída](runtime-exception-class.md)|Základní typ pro výjimky v knihovně C++ amp.|
|[tile_barrier – třída](tile-barrier-class.md)|Třída schopností, která je určena pouze systémem a je předána na dlaždici `parallel_for_each` lambda jako součást parametru `tiled_index`. Poskytuje jednu metodu, `wait()`, jejichž účelem je synchronizovat spuštění vláken, která jsou spuštěna ve skupině vláken (dlaždice).|
|[tiled_extent – třída](tiled-extent-class.md)|Objekt `tiled_extent` je objekt `extent` jedné až tří dimenzí, který rozděluje rozsah prostoru na jednorozměrné, dvojrozměrné nebo trojrozměrné dlaždice.|
|[tiled_index – třída](tiled-index-class.md)|Poskytuje index do objektu `tiled_grid`. Tato třída má vlastnosti pro přístup k prvku vzhledem k původnímu zdroji dlaždice a relativnímu k globálnímu původu.|
|[uninitialized_object – třída](uninitialized-object-class.md)|Výjimka, která je vyvolána při použití neinicializovaného objektu.|
|[unsupported_feature – třída](unsupported-feature-class.md)|Výjimka, která je vyvolána při použití nepodporované funkce.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[Výčet access_type](concurrency-namespace-enums-amp.md#access_type)|Určuje typ přístupu k datům.|
|[Výčet queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)|Určuje režimy služby Řízení front, které jsou podporovány v akcelerátoru.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|--------------|-----------------|
|[operator = = – operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Určuje, zda jsou zadané datové struktury stejné.|
|[operator! = – operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator_neq)|Určuje, zda zadané datové struktury nejsou stejné.|
|[operator + – operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator_add)|Vypočítá součet zadaných argumentů ze součásti.|
|[operator-– operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator-)|Vypočítá rozdíl mezi zadanými argumenty v rámci součásti.|
|[operator * – operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator_star)|Vypočítá produkt určený argumenty v rámci součásti.|
|[operator/– operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator_div)|Vypočítá podíl zadaných argumentů v rámci součásti.|
|[operator% – operátorC++ (amp)](concurrency-namespace-operators-amp.md#operator_mod)|Vypočítá zbytky prvního zadaného argumentu druhým zadaným argumentem.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do paměti.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Zruší inicializaci modulu runtime C++ amp.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Přetíženo. Pokud hodnota uložená v zadaném umístění porovnává stejnou hodnotu jako první zadaná hodnota, bude druhá zadaná hodnota uložena ve stejném umístění jako atomická operace.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na součet dané hodnoty a zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na bitovou `and` této hodnoty a zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Přetíženo. Sníží hodnotu uloženou v zadaném umístění a uloží výsledek do stejného umístění jako atomická operace.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Přetíženo. Zvýší hodnotu uloženou v zadaném umístění a uloží výsledek do stejného umístění jako atomická operace.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na větší hodnotu a zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na menší hodnotu a zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na bitovou `or` této hodnoty a zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na rozdíl této hodnoty a zadanou hodnotu jako atomickou operaci.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na bitovou `xor` této hodnoty a zadanou hodnotu jako atomickou operaci.|
|[kopií](concurrency-namespace-functions-amp.md#copy)|Zkopíruje objekt C++ amp. Jsou splněné všechny požadavky synchronního přenosu dat. Data nelze kopírovat, pokud kód spouští kód v akcelerátoru. Obecná forma této funkce je `copy(src, dest)`.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Zkopíruje objekt C++ amp a vrátí [completion_future](completion-future-class.md) , které mohou být očekávány. Data nelze kopírovat, je-li kód spuštěn v akcelerátoru. Obecná forma této funkce je `copy(src, dest)`.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Přeruší provádění funkce, která má klauzuli omezení `restrict(amp)`.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Vytiskne formátovaný řetězec do okna **výstupu** sady Visual Studio a vyvolá výjimku [runtime_exception](runtime-exception-class.md) , která má stejný formátovací řetězec.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Vytiskne formátovaný řetězec do okna **výstupu** sady Visual Studio. Je volána z funkce, která má klauzuli omezení `restrict(amp)`.|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do globální paměti.|
|[parallel_for_each – funkceC++ (amp)](concurrency-namespace-functions-amp.md#parallel_for_each)|Spustí funkci napříč výpočetní doménou.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny přístupy do `tile_static` paměti.|

## <a name="constants"></a>Konstanty

|Název|Popis|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS konstanta](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Maximální počet vyrovnávacích pamětí povolených rozhraním DirectX.|
|[MODULENAME_MAX_LENGTH konstanta](concurrency-namespace-constants-amp.md#modulename_max_length)|Ukládá maximální délku názvu modulu. Tato hodnota musí být stejná pro kompilátor a modul runtime.|

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

## <a name="see-also"></a>Viz také

[Referenční dokumentace (C++ AMP)](reference-cpp-amp.md)
