---
title: "Funkce obor názvů souběžnosti (AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
dev_langs: C++
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 26361befb1ca245a9efe8dd0db4ba4f30129bda6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-namespace-functions-amp"></a>Funkce obor názvů souběžnosti (AMP)
||||  
|-|-|-|  
|[all_memory_fence –](#all_memory_fence)|[amp_uninitialize –](#amp_uninitialize)|[atomic_compare_exchange –](#atomic_compare_exchange)|  
|[atomic_exchange – funkce (C++ AMP)](#atomic_exchange)|[atomic_fetch_add – funkce (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and – funkce (C++ AMP)](#atomic_fetch_and)|  
|[atomic_fetch_dec –](#atomic_fetch_dec)|[atomic_fetch_inc –](#atomic_fetch_inc)|[atomic_fetch_max –](#atomic_fetch_max)|  
|[atomic_fetch_min –](#atomic_fetch_min)|[atomic_fetch_or – funkce (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub – funkce (C++ AMP)](#atomic_fetch_sub)|  
|[atomic_fetch_xor – funkce (C++ AMP)](#atomic_fetch_xor)|[kopírování](#copy)|[copy_async –](#copy_async)|  
|[direct3d_abort –](#direct3d_abort)|[direct3d_errorf –](#direct3d_errorf)|[direct3d_printf –](#direct3d_printf)|  
|[global_memory_fence –](#global_memory_fence)|[parallel_for_each – funkce (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence –](#tile_static_memory_fence)|  
  
##  <a name="all_memory_fence"></a>all_memory_fence –  
 Bloky provádění všechna vlákna v dlaždici dokud byly dokončeny všechny přístupy paměti. To zajistí, že všechny přístupy paměti jsou viditelné pro jiná vlákna v dlaždici přístup z více vláken a jsou spouštěny v pořadí programu.  
  
```  
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Barrier`  
 A `tile_barrier` objektu.  
  
##  <a name="amp_uninitialize"></a>amp_uninitialize –  
 Uninitializes C++ AMP runtime. Je možné volání této funkce vícekrát během životního cyklu aplikací. Volání metody žádné C++ AMP API afer volání této funkce bude reinicializovat C++ AMP runtime. Všimněte si, že je neplatné použití objektů C++ AMP napříč volání této funkce, a to tak bude mít za následek nedefinované chování. Také souběžně volání této funkce a všechny ostatní rozhraní API AMP je neplatný a by způsobilo nedefinované chování.  
  
```  
void __cdecl amp_uninitialize();
```  
  
##  <a name="atomic_compare_exchange"></a>atomic_compare_exchange –  
 Atomicky porovná s hodnotou uloženou v paměti umístění určené v prvním argumentu rovnosti s hodnotou druhý argument zadaný, a pokud jsou hodnoty stejné, hodnota v umístění v paměti se změní na, aby třetí zadán argument.  
  
```  
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,  
    _Inout_ int* _Expected_value,  
    int value  
    ) restrict(amp)

 
inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,  
    _Inout_ unsigned int* _Expected_value,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Umístění, ze které z nich hodnot, který se má porovnat je pro čtení, a do které nová hodnota, pokud existuje, je k uložení.  
  
 `_Expected_value`  
 Umístění, ze kterého je druhá hodnota, která má být porovnána pro čtení.  
  
 `value`  
 Hodnota, která má být uložen do určeného v umístění v paměti `_Dest` Pokud `_Dest` rovná `_Expected_value`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byla operace úspěšná. v opačném `false`.  
  

##  <a name="atomic_exchange"></a>atomic_exchange – funkce (C++ AMP)  
 Nastaví hodnotu cílové umístění jako atomickou operaci.  
  
```  
inline int atomic_exchange(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)

 
inline float atomic_exchange(
    _Inout_ float* _Dest,  
    float value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Ukazatel na destionation umístění.  
  
 `value`  
 Nová hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnotu cílové umístění.  
  

##  <a name="atomic_fetch_add"></a>atomic_fetch_add – funkce (C++ AMP)  
 Atomicky přidejte hodnotu na hodnotu umístění v paměti.  
  
```  
inline int atomic_fetch_add(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Ukazatel na umístění v paměti.  
  
 `value`  
 Hodnota, která má být přidán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnotu umístění v paměti.  
  
##  <a name="atomic_fetch_and"></a>atomic_fetch_and – funkce (C++ AMP)  
 Provede atomicky bitové operace AND hodnotu a hodnotu umístění v paměti.  
  
```  
inline int atomic_fetch_and(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Ukazatel na umístění v paměti.  
  
 `value`  
 Hodnota k použití bitové operace AND výpočtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnotu umístění v paměti.  
  
##  <a name="atomic_fetch_dec"></a>atomic_fetch_dec –  
 Atomicky snižuje hodnota uložena v umístění zadané paměti.  
  
```  
inline int atomic_fetch_dec(_Inout_ int* _Dest  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Umístění v paměti hodnota, která má být odečte.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložena v umístění v paměti.  
  
##  <a name="atomic_fetch_inc"></a>atomic_fetch_inc –  
 Hodnota uložená v umístění zadaná paměťová atomicky zvýší.  
  
```  
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

 
inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Umístění v paměti hodnota, která má být zvýšena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložena v umístění v paměti.  
  
##  <a name="atomic_fetch_max"></a>atomic_fetch_max –  
 Atomicky vypočítá maximální hodnota mezi s hodnotou uloženou v paměti umístění, v prvním argumentu a hodnotou zadanou v druhý argument a uloží je na stejné umístění paměti.  
  
```  
inline int atomic_fetch_max(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Umístění, ze které z nich hodnot, který se má porovnat je pro čtení, a na které má být uložené maximálně dvě hodnoty.  
  
 `value`  
 Hodnota, který se má porovnat hodnotu do zadaného umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložena v umístění zadaném umístění.  
  
##  <a name="atomic_fetch_min"></a>atomic_fetch_min –  
 Atomicky vypočítá minimální hodnota mezi s hodnotou uloženou v paměti umístění, v prvním argumentu a hodnotou zadanou v druhý argument a uloží je na stejné umístění paměti.  
  
```  
inline int atomic_fetch_min(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Umístění, ze které z nich hodnot, který se má porovnat je pro čtení, a na které má být uložen minimálně dvě hodnoty.  
  
 `value`  
 Hodnota, který se má porovnat hodnotu do zadaného umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložena v umístění zadaném umístění.  
  
##  <a name="atomic_fetch_or"></a>atomic_fetch_or – funkce (C++ AMP)  
 Provede atomicky bitové operace OR s hodnota a hodnota umístění v paměti.  
  
```  
inline int atomic_fetch_or(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Ukazatel na umístění v paměti.  
  
 `value`  
 Hodnota k použití bitové operace OR výpočtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnotu umístění v paměti.  
  
##  <a name="atomic_fetch_sub"></a>atomic_fetch_sub – funkce (C++ AMP)  
 Atomicky odečte hodnotu z oblasti paměti.  
  
```  
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Ukazatel na destionation umístění.  
  
 `value`  
 Hodnota k odečítat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnotu umístění v paměti.  
  
##  <a name="atomic_fetch_xor"></a>atomic_fetch_xor – funkce (C++ AMP)  
 Atomicky peforms bitové operace XOR hodnota a umístění v paměti.  
  
```  
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Ukazatel na umístění v paměti.  
  
 `value`  
 Hodnota, která chcete použít pro výpočet XOR.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnotu umístění v paměti.  
  
##  <a name="copy"></a>kopírování  
 Zkopíruje C++ AMP objektu. Jsou splněny všechny požadavky na přenos synchronní údaje. Při spuštění kódu na akcelerátor, nejde zkopírovat data. Obecná forma tato funkce je `copy(src, dest)`.  
  
```  
template <typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,  
    array<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,
     OutputIterator _DestIter);

 
template <typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<const value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<const value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst, 
    InputIterator _SrcLast,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Objekt, který se má zkopírovat do.  
  
 `_DestIter`  
 Iterátor výstup do počáteční pozice v cílovém umístění.  
  
 `InputIterator`  
 Typ vstupu interator.  
  
 `OutputIterator`  
 Typ iterator výstup.  
  
 `_Rank`  
 Pořadí objekt, který chcete zkopírovat z nebo objekt, který chcete zkopírovat do.  
  
 `_Src`  
 Chcete-li objekt pro kopírování.  
  
 `_SrcFirst`  
 Začátek iterator do kontejneru zdroje.  
  
 `_SrcLast`  
 Koncová iterator do kontejneru zdroje.  
  
 `value_type`  
 Datový typ elementů, které jste zkopírovali.  
  
##  <a name="copy_async"></a>copy_async –  
 Zkopíruje objekt C++ AMP a vrátí [completion_future](completion-future-class.md) objekt, který může být čekali na. Při spuštění kódu na akcelerátor, nejde zkopírovat data.  Obecná forma tato funkce je `copy(src, dest)`.  
  
```  
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst,  
    array<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Objekt, který se má zkopírovat do.  
  
 `_DestIter`  
 Iterátor výstup do počáteční pozice v cílovém umístění.  
  
 `InputIterator`  
 Typ vstupu interator.  
  
 `OutputIterator`  
 Typ iterator výstup.  
  
 `_Rank`  
 Pořadí objekt, který chcete zkopírovat z nebo objekt, který chcete zkopírovat do.  
  
 `_Src`  
 Chcete-li objekt pro kopírování.  
  
 `_SrcFirst`  
 Začátek iterator do kontejneru zdroje.  
  
 `_SrcLast`  
 Koncová iterator do kontejneru zdroje.  
  
 `value_type`  
 Datový typ elementů, které jste zkopírovali.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `future<void>` , může být čekali.  
  
##  <a name="direct3d_abort"></a>direct3d_abort –  
 Zruší spuštění funkce s `restrict(amp)` klauzule omezení. Zjistí-li modul runtime AMP volání, vyvolá [runtime_exception](runtime-exception-class.md) výjimku s chybovou zprávou "umožňuje odkaz: shaderu abort podle instrukcí".  
  
```  
void direct3d_abort() restrict(amp);
```  
  
##  <a name="direct3d_errorf"></a>direct3d_errorf –  
 Vytiskne formátovaný řetězec do okna výstupu sady Visual Studio. Je volána z funkce s `restrict(amp)` klauzule omezení. Zjistí-li modul runtime AMP volání, vyvolá [runtime_exception](runtime-exception-class.md) výjimka se stejným formátování řetězce.  
  
```  
void direct3d_errorf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="direct3d_printf"></a>direct3d_printf –  
 Vytiskne formátovaný řetězec do okna výstupu sady Visual Studio. Je volána z funkce s `restrict(amp)` klauzule omezení.  
  
```  
void direct3d_printf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="global_memory_fence"></a>global_memory_fence –  
 Bloky provádění všechna vlákna v dlaždici, dokud všechny globální paměť přistupuje byly dokončeny. To zajistí, že globální paměť přístupů jsou viditelné pro jiná vlákna v dlaždici přístup z více vláken a jsou spouštěny v pořadí programu.  
  
```  
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Barrier`  
 Objekt tile_barrier  
  
##  <a name="parallel_for_each"></a>parallel_for_each – funkce (C++ AMP)  
 Spustí funkci napříč výpočetní doméně. Další informace najdete v tématu [přehled produktu C++ AMP](../../../parallel/amp/cpp-amp-overview.md).  
  
```  
template <int _Rank, typename _Kernel_type>  
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
     const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

 
template <int _Dim0, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Rank, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const extent<_Rank>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0>& _Compute_domain,  
    const _Kernel_type& _Kernel);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accl_view`  
 `accelerator_view` Objekt, který chcete spustit na paralelní výpočty.  
  
 `_Compute_domain`  
 `extent` Objekt, který obsahuje data pro výpočet.  
  
 `_Dim0`  
 Dimenzi `tiled_extent` objektu.  
  
 `_Dim1`  
 Dimenzi `tiled_extent` objektu.  
  
 `_Dim2`  
 Dimenzi `tiled_extent` objektu.  
  
 `_Kernel`  
 Objekt lambda nebo funkce, která přebírá argument typu "index\<_Rank >" a provede paralelní výpočty.  
  
 `_Kernel_type`  
 Lambda nebo functor.  
  
 `_Rank`  
 Pořadí v rozsahu.  
  
##  <a name="tile_static_memory_fence"></a>tile_static_memory_fence –  
 Blokování provádění všechna vlákna v dlaždici, dokud všechny zbývající `tile_static` dokončili paměti přístupů. To zajistí, že `tile_static` přístupů paměti jsou viditelné pro jiná vlákna v dlaždici přístup z více vláken a že přístupů, které jsou spouštěny v pořadí programu.  
  
```  
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Barrier`  
 Tile_barrier objekt.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
