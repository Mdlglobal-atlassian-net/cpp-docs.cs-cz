---
title: Funkce oboru názvů Concurrency (AMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba253744b7abc3cc37dfa765ebe15af49b89c0ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069141"
---
# <a name="concurrency-namespace-functions-amp"></a>Funkce oboru názvů Concurrency (AMP)
||||  
|-|-|-|  
|[all_memory_fence –](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|  
|[atomic_exchange – funkce (C++ AMP)](#atomic_exchange)|[atomic_fetch_add – funkce (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and – funkce (C++ AMP)](#atomic_fetch_and)|  
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|  
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or – funkce (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub – funkce (C++ AMP)](#atomic_fetch_sub)|  
|[atomic_fetch_xor – funkce (C++ AMP)](#atomic_fetch_xor)|[kopírování](#copy)|[copy_async](#copy_async)|  
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|  
|[global_memory_fence –](#global_memory_fence)|[parallel_for_each – funkce (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence –](#tile_static_memory_fence)|  
  
##  <a name="all_memory_fence"></a>  all_memory_fence –  
 Pozastaví spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do paměti. Tím se zajistí, že všechny přístupy do paměti viditelné pro ostatní vlákna v dlaždici vlákna a jsou provedeny v pořadí programu.  
  
```  
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
*_Barrier*<br/>
A `tile_barrier` objektu.  
  
##  <a name="amp_uninitialize"></a>  amp_uninitialize –  
 Zruší inicializaci modulu runtime C++ AMP. Je možné tuto funkci volat vícekrát během životního cyklu aplikace. Volání jakékoli C++ AMP API po volání této funkce spustí opětovnou inicializaci modulu runtime C++ AMP. Všimněte si, že není povoleno použití objektů C++ AMP mezi volání této funkce a to proto způsobí nedefinované chování. Také souběžné volání této funkce a jakékoliv jiné API AMP je neplatná a bude mít za následek nedefinované chování.  
  
```  
void __cdecl amp_uninitialize();
```  
  
##  <a name="atomic_compare_exchange"></a>  atomic_compare_exchange –  
 Atomicky porovná hodnotu uloženou v paměti umístění určené v prvním argumentu rovnosti s hodnotou druhého zadaného argumentu, a pokud jsou hodnoty stejné, hodnota v umístění v paměti se změní na, že ve třetím zadaném argumentu.  
  
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
*_Dest*<br/>
Čtení umístění, ze které jedna z porovnávaných hodnot, a ke kterému novou hodnotu, pokud existuje, se uloží.  
  
*_Expected_value*<br/>
Umístění, ze kterých je druhá hodnota, která se má porovnat číst.  
  
*value*<br/>
Hodnota, která má být uložena do umístění paměti zadaného parametrem `_Dest` Pokud `_Dest` rovná `_Expected_value`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je operace úspěšná. v opačném případě `false`.  
  

##  <a name="atomic_exchange"></a>  atomic_exchange – funkce (C++ AMP)  
 Nastaví hodnotu vlastnosti cílové umístění jako atomická operace.  
  
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
*_Dest*<br/>
Ukazatel na cílová umístění.  
  
*value*<br/>
Nová hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota cílové umístění.  
  

##  <a name="atomic_fetch_add"></a>  atomic_fetch_add – funkce (C++ AMP)  
 Atomicky přidá hodnotu do hodnoty vlastnosti umístění v paměti.  
  
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
*_Dest*<br/>
Ukazatel na umístění v paměti.  
  
*value*<br/>
Hodnota má být přidán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota umístění v paměti.  
  
##  <a name="atomic_fetch_and"></a>  atomic_fetch_and – funkce (C++ AMP)  
 Provádí atomicky bitové operace AND hodnotu a hodnotu umístění v paměti.  
  
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
*_Dest*<br/>
Ukazatel na umístění v paměti.  
  
*value*<br/>
Hodnota, která chcete použít bitový AND výpočtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota umístění v paměti.  
  
##  <a name="atomic_fetch_dec"></a>  atomic_fetch_dec –  
 Atomicky sníží hodnotu uloženou v zadaném umístění v paměti.  
  
```  
inline int atomic_fetch_dec(_Inout_ int* _Dest  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
*_Dest*<br/>
Umístění v paměti hodnota, která má být snížena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložená v umístění v paměti.  
  
##  <a name="atomic_fetch_inc"></a>  atomic_fetch_inc –  
 Atomicky zvýší hodnotu uloženou v zadaném umístění v paměti.  
  
```  
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

 
inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
*_Dest*<br/>
Umístění v paměti hodnota, která má být zvýšen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložená v umístění v paměti.  
  
##  <a name="atomic_fetch_max"></a>  atomic_fetch_max –  
 Atomicky vypočítá maximální hodnotu mezi hodnotou uloženou v paměti umístění zadaném v prvním argumentu a hodnotu zadanou ve druhém argumentu a uloží ji na stejné místo v paměti.  
  
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
*_Dest*<br/>
Čtení umístění, ze které jedna z porovnávaných hodnot, a do kterého má být uloženy maximálně dvě hodnoty.  
  
*value*<br/>
Hodnota, která se má porovnat s hodnotou v zadaném umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložená v uvedeném umístění.  
  
##  <a name="atomic_fetch_min"></a>  atomic_fetch_min –  
 Atomicky vypočítá minimální hodnotu mezi hodnotou uloženou v paměti umístění zadaném v prvním argumentu a hodnotu zadanou ve druhém argumentu a uloží ji na stejné místo v paměti.  
  
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
*_Dest*<br/>
Čtení umístění, ze které jedna z porovnávaných hodnot, a do kterého má být uloženy minimálně dvě hodnoty.  
  
*value*<br/>
Hodnota, která se má porovnat s hodnotou v zadaném umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota uložená v uvedeném umístění.  
  
##  <a name="atomic_fetch_or"></a>  atomic_fetch_or – funkce (C++ AMP)  
 Provádí atomicky bitová operace OR s hodnotu a hodnotu umístění v paměti.  
  
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
*_Dest*<br/>
Ukazatel na umístění v paměti.  
  
*value*<br/>
Hodnota, která chcete použít bitový OR výpočtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota umístění v paměti.  
  
##  <a name="atomic_fetch_sub"></a>  atomic_fetch_sub – funkce (C++ AMP)  
 Atomicky odečte hodnotu z umístění v paměti.  
  
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
*_Dest*<br/>
Ukazatel na cílová umístění.  
  
*value*<br/>
Hodnota určená k mít odečíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota umístění v paměti.  
  
##  <a name="atomic_fetch_xor"></a>  atomic_fetch_xor – funkce (C++ AMP)  
 Atomicky peforms bitové operace XOR hodnotu a umístění v paměti.  
  
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
*_Dest*<br/>
Ukazatel na umístění v paměti.  
  
*value*<br/>
Hodnoty pro výpočet XOR.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní hodnota umístění v paměti.  
  
##  <a name="copy"></a>  kopírování  
 Zkopíruje objekt jazyka C++ AMP. Jsou splněny všechny požadavky synchronního přenosu dat. Data nelze kopírovat, li kód spuštěn na akcelerátoru. Obecný tvar této funkce je `copy(src, dest)`.  
  
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
*_Dest*<br/>
Objekt, který chcete zkopírovat do.  
  
*_DestIter*<br/>
Výstupní iterátor na počáteční pozici cíle.  
  
*InputIterator*<br/>
Typ vstupního iterátoru.  
  
*OutputIterator*<br/>
Typ výstupního iterátoru.  
  
*_Rank*<br/>
Řád objektu, který chcete kopírovat z nebo objekt, který chcete zkopírovat.  
  
*_Src*<br/>
Kopírovaný objekt.  
  
*_SrcFirst*<br/>
Počáteční iterátor do zdrojového kontejneru.  
  
*_SrcLast*<br/>
Koncový iterátor do zdrojového kontejneru.  
  
*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.  
  
##  <a name="copy_async"></a>  copy_async –  
 Zkopíruje objekt jazyka C++ AMP a vrátí [completion_future](completion-future-class.md) objekt, který lze čekat. Data nelze kopírovat, li kód spuštěn na akcelerátoru.  Obecný tvar této funkce je `copy(src, dest)`.  
  
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
*_Dest*<br/>
Objekt, který chcete zkopírovat do.  
  
*_DestIter*<br/>
Výstupní iterátor na počáteční pozici cíle.  
  
*InputIterator*<br/>
Typ vstupního iterátoru.  
  
*OutputIterator*<br/>
Typ výstupního iterátoru.  
  
*_Rank*<br/>
Řád objektu, který chcete kopírovat z nebo objekt, který chcete zkopírovat.  
  
*_Src*<br/>
Kopírovaný objekt.  
  
*_SrcFirst*<br/>
Počáteční iterátor do zdrojového kontejneru.  
  
*_SrcLast*<br/>
Koncový iterátor do zdrojového kontejneru.  
  
*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `future<void>` , který lze čekat.  
  
##  <a name="direct3d_abort"></a>  direct3d_abort –  
 Zruší spuštění funkce se `restrict(amp)` podmínkou. Modulu runtime AMP zachytí volání, vyvolá [runtime_exception](runtime-exception-class.md) výjimka s chybovou zprávou "rasterizéru referenčního: shaderu přerušit přístupů k instrukci".  
  
```  
void direct3d_abort() restrict(amp);
```  
  
##  <a name="direct3d_errorf"></a>  direct3d_errorf –  
 Vytiskne formátovaný řetězec v okně výstupu sady Visual Studio. Je volána z funkce s `restrict(amp)` podmínkou. Modulu runtime AMP zachytí volání, vyvolá [runtime_exception](runtime-exception-class.md) výjimka se stejným formátovacím řetězcem.  
  
```  
void direct3d_errorf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="direct3d_printf"></a>  direct3d_printf –  
 Vytiskne formátovaný řetězec v okně výstupu sady Visual Studio. Je volána z funkce s `restrict(amp)` podmínkou.  
  
```  
void direct3d_printf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="global_memory_fence"></a>  global_memory_fence –  
 Pozastaví spuštění všech vláken v dlaždici, dokud nejsou všechny globální přístupy dokončeny. Tím se zajistí, že přístupy do globální paměti viditelné pro ostatní vlákna v dlaždici vlákna a jsou provedeny v pořadí programu.  
  
```  
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
*_Barrier*<br/>
Objekt tile_barrier  
  
##  <a name="parallel_for_each"></a>  parallel_for_each – funkce (C++ AMP)  
 Spustí funkci napříč výpočetní doménou. Další informace najdete v tématu [přehled modelu C++ AMP](../../../parallel/amp/cpp-amp-overview.md).  
  
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
*_Accl_view*<br/>
`accelerator_view` Objekt spouštět paralelní výpočet.  
  
*_Compute_domain*<br/>
`extent` Objekt, který obsahuje data pro výpočet.  
  
*_Dim0*<br/>
Dimenzi `tiled_extent` objektu.  
  
*_Dim1*<br/>
Dimenzi `tiled_extent` objektu.  
  
*_Dim2*<br/>
Dimenzi `tiled_extent` objektu.  
  
*_Kernel*<br/>
Výraz lambda nebo funkce objektu, který přebírá argument typu "index\<_Rank >" a provádí paralelní výpočet.  
  
*_Kernel_type*<br/>
Výraz lambda nebo funktor.  
  
*_Rank*<br/>
Řád rozsahu.  
  
##  <a name="tile_static_memory_fence"></a>  tile_static_memory_fence –  
 Pozastaví spuštění všech vláken v dlaždici, dokud všichni zbývající `tile_static` nejsou dokončeny přístupy do paměti. To zajistí, že `tile_static` jsou přístupy do paměti viditelné pro ostatní vlákna v dlaždici vlákna a že jsou provedeny v pořadí programu.  
  
```  
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
*_Barrier*<br/>
Objekt tile_barrier.  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
