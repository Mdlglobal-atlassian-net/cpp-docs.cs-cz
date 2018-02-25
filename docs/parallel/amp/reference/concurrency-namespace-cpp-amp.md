---
title: "Namespace souběžnosti (C++ AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a9f82baade21cdbde41fc49fd0bfe6163c0f6af
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="concurrency-namespace-c-amp"></a>Obor názvů souběžnosti (C++ AMP)
Poskytuje třídy a funkce, které urychlit spuštění kódu C++ na data paralelní hardwaru. Další informace najdete v tématu [přehled produktu C++ AMP](../cpp-amp-overview.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="namespaces"></a>Jmenné prostory  
  
|Název|Popis|  
|----------|-----------------|  
|[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)|Poskytuje funkce, které podporují D3D interoperability. Umožňuje bezproblémové použití D3D prostředků pro výpočet v kódu AMP a využívat prostředky vytvořené v AMP v kódu D3D bez vytvoření zprostředkující redundantní kopie. C++ AMP můžete přírůstkově urychlit části náročné DirectX aplikací a použít rozhraní API D3D na dat vytvářených z AMP výpočty.|  
|[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)|Funkce `fast_math` nejsou kompatibilní se standardem C99 oboru názvů. Pouze jednoduchou přesností verze jednotlivé funkce jsou k dispozici. Vnitřní funkce DirectX, které jsou rychlejší než odpovídající funkce v použít tyto funkce `precise_math` obor názvů a nevyžadují rozšířené podpory dvojitou přesností na akcelerátor, ale je méně přesné. Existují dvě verze jednotlivé funkce pro zdroj úroveň kompatibility s kódem C99; obě verze trvat a návratové hodnoty jednoduchou přesností.|  
|[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)|Poskytuje typy a funkce, které jsou určené pro programováním grafiky.|  
|[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)|Funkce `precise_math` obor názvů jsou C99 kompatibilní. Jednoduchou přesností a dvojitou přesností verzích jednotlivé funkce jsou zahrnuty. Tyto funkce – to zahrnuje funkce jednoduchou přesností – vyžadují rozšířené podpory dvojitou přesností na akcelerátor.|  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[accelerator – třída](accelerator-class.md)|Představuje abstrakci uzlu fyzické výpočetní optimalizované distribučního bodu.|  
|[accelerator_view – třída](accelerator-view-class.md)|Představuje virtuální zařízení abstrakce na akcelerátor C++ AMP paralelní data.|  
|[accelerator_view_removed – třída](accelerator-view-removed-class.md)|Výjimka, která se vyvolá, když je základní DirectX volání selže z důvodu vypršení časového limitu detekce a zotavení mechanismus Windows.|  
|[array – třída](array-class.md)|Agregační na data `accelerator_view` v doméně mřížky. Jedná se o kolekci proměnných, jednu pro každý prvek v doméně mřížky. Každá proměnná obsahuje hodnotu, která odpovídá některé C++ typu.|  
|[array_view – třída](array-view-class.md)|Představuje pohled na data v pole\<T, N >.|  
|[completion_future – třída](completion-future-class.md)|Představuje budoucnost, která odpovídá C++ AMP asynchronní operaci.|  
|[extent – třída](extent-class.md)|Představuje vektor N celočíselné hodnoty, které určují hranice N dimenzí místa, která má počátek 0. Hodnoty v souřadnic vektor seřazeni z nejvýznamnějších k nejméně významný. V kartézských 3 dimenzí místo, například rozsah vektoru (7,5,3) představuje místa, ve kterém souřadnice v rozsahu od 0 do 7, rozsahy na souřadnici y od 0 do 5, a souřadnici x rozsah od 0 do 3.|  
|[index – třída](index-class.md)|Definuje bod dimenzí N index.|  
|[invalid_compute_domain – třída](invalid-compute-domain-class.md)|Výjimka, která se vyvolá, když modul runtime nelze spustit jádra pomocí zadané v doméně výpočetní `parallel_for_each` volání lokality.|  
|[out_of_memory – třída](out-of-memory-class.md)|Výjimka, která se vyvolá, když metoda selže z důvodu nedostatku paměti systému nebo zařízení.|  
|[runtime_exception – třída](runtime-exception-class.md)|Základní typ pro výjimky v knihovně C++ AMP.|  
|[tile_barrier – třída](tile-barrier-class.md)|Funkce třídu, která je jenom vytvořitelné systémem a je předána vedle sebe `parallel_for_each` lambda jako součást `tiled_index` parametr. Poskytuje jednu metodu `wait()`, jejichž účelem je synchronizovat provádění vláken, která běží ve skupině přístup z více vláken (dlaždice).|  
|[tiled_extent – třída](tiled-extent-class.md)|A `tiled_extent` objekt `extent` objekt jednu až tři dimenzí, který rozděluje prostor rozsah do jednorozměrné, dvourozměrná nebo trojrozměrné dlaždice.|  
|[tiled_index – třída](tiled-index-class.md)|Poskytuje index do `tiled_grid` objektu. Tato třída obsahuje vlastnosti pro přístup k elementu relativně ke zdroji místní dlaždice a relativně ke zdroji globální.|  
|[uninitialized_object – třída](uninitialized-object-class.md)|Výjimka, která se vyvolá, když se používá k neinicializovanému objektu.|  
|[unsupported_feature – třída](unsupported-feature-class.md)|Výjimka, která se vyvolá, když se používá nepodporované funkce.|  
  
### <a name="enumerations"></a>Výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[access_type – výčet](concurrency-namespace-enums-amp.md#access_type)|Určuje datový typ přístupu.|  
|[queuing_mode – výčet](concurrency-namespace-enums-amp.md#queuing_mode)|Určuje režimů služby Řízení front, které jsou podporovány na akcelerátor.|  
  
### <a name="operators"></a>Operátory  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Operator == – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Určuje, zda zadaná data struktury jsou stejné.|  
|[Operator! = – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|Určuje, zda zadaný datové struktury nerovné.|  
|[Operator + – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|Vypočítá component-wise součet jsou zadané argumenty.|  
|[Operator-– operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|Vypočítá component-wise rozdíl mezi zadanými argumenty.|  
|[Operator * – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|Vypočítá component-wise produkt jsou zadané argumenty.|  
|[Operator / – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|Vypočítá component-wise podíl jsou zadané argumenty.|  
|[Operator % – operátor (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|Vypočítá zbytek z první argument zadaný ve druhém zadaného argumentu.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Bloky provádění všechna vlákna v dlaždici dokud byly dokončeny všechny přístupy paměti.|  
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Uninitializes C++ AMP runtime.|  
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Přetíženo. Pokud stejná jako první zadaná hodnota porovná s hodnotou uloženou v zadaném umístění, druhý zadaná hodnota je uložena ve stejném umístění jako atomickou operaci.|  
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění jako atomickou operaci se zadanou hodnotou.|  
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění součtu tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění bitové hodnotě `and` tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Přetíženo. Sníží hodnotu uloží do zadaného umístění a výsledek je uložen ve stejném umístění jako atomickou operaci.|  
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Přetíženo. Zvýší s hodnotou uloženou v zadaném umístění a výsledek je uložen ve stejném umístění jako atomickou operaci.|  
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění se větší tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění na menší tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění bitové hodnotě `or` tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění rozdílu tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Přetíženo. Nastaví hodnotu uloženou v zadaném umístění bitové hodnotě `xor` tuto hodnotu a zadanou hodnotu jako atomickou operaci.|  
|[Kopírování](concurrency-namespace-functions-amp.md#copy)|Zkopíruje C++ AMP objektu. Jsou splněny všechny požadavky na přenos synchronní údaje. Data nelze kopírovat, pokud kód je spuštění kódu na akcelerátoru. Obecná forma tato funkce je `copy(src, dest)`.|  
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Zkopíruje objekt C++ AMP a vrátí [completion_future](completion-future-class.md) , může být čekali. Data nelze kopírovat, pokud kód běží na akcelerátoru. Obecná forma tato funkce je `copy(src, dest)`.|  
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Zruší provádění funkci, která má `restrict(amp)` klauzule omezení.|  
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Vytiskne formátovaný řetězec k sadě Visual Studio **výstup** okno a vyvolá [runtime_exception](runtime-exception-class.md) výjimka, která má stejné formátování řetězce.|  
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Vytiskne formátovaný řetězec k sadě Visual Studio **výstup** okno. Je volána z funkce, která má `restrict(amp)` klauzule omezení.|  
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Bloky provádění všechna vlákna v dlaždici, dokud všechny globální paměť přistupuje byly dokončeny.|  
|[parallel_for_each – funkce (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|Spustí funkci napříč výpočetní doméně.|  
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Blokování provádění všechna vlákna v dlaždici až `tile_static` dokončili paměti přístupů.|  
  
## <a name="constants"></a>Konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[HLSL_MAX_NUM_BUFFERS Constant](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Maximální počet povolený DirectX vyrovnávací paměti.|  
|[Modulename_max_length – konstanta](concurrency-namespace-constants-amp.md#modulename_max_length)|Ukládá maximální délka názvu modulu. Tato hodnota musí být stejný v kompilátoru a modulu runtime.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace (C++ AMP)](reference-cpp-amp.md)



