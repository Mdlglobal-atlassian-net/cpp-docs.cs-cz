---
title: Funkce oboru názvů Concurrency (AMP)
ms.date: 11/04/2016
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
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: 1187b745a6d8c903c22958185be8d98a6e3d0204
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376354"
---
# <a name="concurrency-namespace-functions-amp"></a>Funkce oboru názvů Concurrency (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[funkce atomic_exchange (C++ AMP)](#atomic_exchange)|[funkce atomic_fetch_add (C++ AMP)](#atomic_fetch_add)|[funkce atomic_fetch_and (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or funkce (C++ AMP)](#atomic_fetch_or)|[funkce atomic_fetch_sub (C++ AMP)](#atomic_fetch_sub)|
|[funkce atomic_fetch_xor (C++ AMP)](#atomic_fetch_xor)|[Kopírovat](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each funkce (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a>all_memory_fence

Blokuje provádění všech podprocesů v dlaždici, dokud nebudou dokončeny všechny přístupy k paměti. Tím je zajištěno, že všechny přístupy k paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a jsou prováděny v pořadí programu.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Objekt. `tile_barrier`

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize

Uninitializes C++ AMP runtime. Je legální volat tuto funkci vícekrát během životnosti aplikace. Volání libovolného rozhraní API AMP c++ po volání této funkce znovu inicializuje runtime C++ AMP. Všimněte si, že je nezákonné používat objekty C++ AMP napříč volání této funkce a tím bude mít za následek nedefinované chování. Souběžné volání této funkce a dalších minpu API je také nezákonné a by mělo za následek nedefinované chování.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange

Atomicky porovná hodnotu uloženou v umístění paměti zadané v prvním argumentu pro rovnost s hodnotou druhého zadaného argumentu a pokud jsou hodnoty stejné, hodnota v umístění paměti se změní na hodnotu třetího zadaného argumentu.

```cpp
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
Umístění, ze kterého je přečtena jedna z hodnot, které mají být porovnány, a do kterého má být uložena nová hodnota, pokud existuje.

*_Expected_value*<br/>
Umístění, ze kterého je přečtena druhá hodnota, ze které má být porovnána.

*Hodnotu*<br/>
Hodnota, která má být uložena `_Dest` do `_Dest` umístění `_Expected_value`paměti určeného v aplikaci if is equal to .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je operace úspěšná; jinak **false**.

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a>funkce atomic_exchange (C++ AMP)

Nastaví hodnotu cílového umístění jako atomickou operaci.

```cpp
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
Ukazatel na cílové umístění.

*Hodnotu*<br/>
Nová hodnota.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota cílového umístění.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a>funkce atomic_fetch_add (C++ AMP)

Atomicky přidat hodnotu k hodnotě umístění v paměti.

```cpp
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
Ukazatel na umístění paměti.

*Hodnotu*<br/>
Hodnota, která má být přidána.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění paměti.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a>funkce atomic_fetch_and (C++ AMP)

Atomicky provádí bitové a operace hodnoty a hodnota umístění paměti.

```cpp
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
Ukazatel na umístění paměti.

*Hodnotu*<br/>
Hodnota, která má být používána ve výpočtu Bitwise AND.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění paměti.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec

Atomicky sníží hodnotu uloženou v zadaném umístění paměti.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Umístění v paměti hodnoty, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v umístění v paměti.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc

Atomicky zintáží hodnotu uloženou v zadaném umístění paměti.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Umístění v paměti hodnoty, která má být přírůstá.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v umístění v paměti.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a>atomic_fetch_max

Atomicky vypočítá maximální hodnotu mezi hodnotou uloženou v umístění paměti zadané v prvním argumentu a hodnotou zadanou v druhém argumentu a uloží ji do stejného umístění v paměti.

```cpp
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
Umístění, ze kterého je čtena jedna z hodnot, které mají být porovnány, a do kterého má být uloženo maximum z těchto dvou hodnot.

*Hodnotu*<br/>
Hodnota, která má být porovnána s hodnotou v zadaném umístění.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v zadaném umístění.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a>atomic_fetch_min

Atomicky vypočítá minimální hodnotu mezi hodnotou uloženou v umístění paměti zadané v prvním argumentu a hodnotou zadanou v druhém argumentu a uloží ji do stejného umístění v paměti.

```cpp
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
Umístění, ze kterého je čtena jedna z hodnot, které mají být porovnány, a do kterého má být uloženo minimum těchto dvou hodnot.

*Hodnotu*<br/>
Hodnota, která má být porovnána s hodnotou v zadaném umístění.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v zadaném umístění.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a>atomic_fetch_or funkce (C++ AMP)

Atomicky provádí bitovou operaci OR s hodnotou a hodnotou umístění v paměti.

```cpp
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
Ukazatel na umístění paměti.

*Hodnotu*<br/>
Hodnota, která má být v bitovém výpočtu OR.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění paměti.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a>funkce atomic_fetch_sub (C++ AMP)

Atomicky odečte hodnotu z umístění v paměti.

```cpp
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
Ukazatel na cílové umístění.

*Hodnotu*<br/>
Hodnota, která má být odečtena.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění paměti.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a>funkce atomic_fetch_xor (C++ AMP)

Atomicky provádí bitovou operaci XOR hodnoty a umístění paměti.

```cpp
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
Ukazatel na umístění paměti.

*Hodnotu*<br/>
Hodnota, která má být používána ve výpočtu XOR.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění paměti.

## <a name="copy"></a><a name="copy"></a>Kopírovat

Zkopíruje objekt C++ AMP. Jsou splněny všechny požadavky na přenos synchronních dat. Při spuštění kódu na akcelerátoru nelze kopírovat data. Obecná forma této funkce `copy(src, dest)`je .

```cpp
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
Objekt, do který chcete kopírovat.

*_DestIter*<br/>
Výstupní iterátor do počáteční polohy v cílovém umístění.

*Vstupní iterátor*<br/>
Typ vstupního iterátoru.

*Výstupní iterátor*<br/>
Typ výstupního iterátoru.

*_Rank*<br/>
Pořadí objektu, ze který chcete kopírovat, nebo objekt, do který chcete kopírovat.

*_Src*<br/>
Chcete-li objekt kopírovat.

*_SrcFirst*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_SrcLast*<br/>
Koncový iterátor do zdrojového kontejneru.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

## <a name="copy_async"></a><a name="copy_async"></a>copy_async

Zkopíruje objekt C++ AMP a vrátí [completion_future](completion-future-class.md) objekt, na který lze čekat. Při spuštění kódu na akcelerátoru nelze kopírovat data.  Obecná forma této funkce `copy(src, dest)`je .

```cpp
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
Objekt, do který chcete kopírovat.

*_DestIter*<br/>
Výstupní iterátor do počáteční polohy v cílovém umístění.

*Vstupní iterátor*<br/>
Typ vstupního iterátoru.

*Výstupní iterátor*<br/>
Typ výstupního iterátoru.

*_Rank*<br/>
Pořadí objektu, ze který chcete kopírovat, nebo objekt, do který chcete kopírovat.

*_Src*<br/>
Chcete-li objekt kopírovat.

*_SrcFirst*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_SrcLast*<br/>
Koncový iterátor do zdrojového kontejneru.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

### <a name="return-value"></a>Návratová hodnota

A, `future<void>` na který se dá čekat.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a>direct3d_abort

Přeruší provádění funkce s `restrict(amp)` klauzulí omezení. Když běhový běh AMP zjistí volání, vyvolá [výjimku runtime_exception](runtime-exception-class.md) s chybovou zprávou "Reference Rasterizer: Shader abort instruction hit".

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a>direct3d_errorf

Vytiskne formátovaný řetězec do výstupního okna sady Visual Studio. Je volána z funkce `restrict(amp)` s klauzulí omezení. Když běhový běh AMP zjistí volání, vyvolá [výjimku runtime_exception](runtime-exception-class.md) se stejným formátovacím řetězcem.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a>direct3d_printf

Vytiskne formátovaný řetězec do výstupního okna sady Visual Studio. Je volána z funkce `restrict(amp)` s klauzulí omezení.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a>global_memory_fence

Blokuje provádění všech vláken v dlaždici, dokud nebudou dokončeny všechny přístupy ke globální paměti. Tím je zajištěno, že přístupy globální paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a jsou prováděny v pořadí programu.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Tile_barrier objekt

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a>parallel_for_each funkce (C++ AMP)

Spustí funkci napříč výpočetní doménou. Další informace naleznete v tématu [Přehled zesilovače C++](../../../parallel/amp/cpp-amp-overview.md).

```cpp
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
Objekt `accelerator_view` spustit paralelní výpočtu na.

*_Compute_domain*<br/>
Objekt, `extent` který obsahuje data pro výpočtu.

*_Dim0*<br/>
Rozměr objektu. `tiled_extent`

*_Dim1*<br/>
Rozměr objektu. `tiled_extent`

*_Dim2*<br/>
Rozměr objektu. `tiled_extent`

*_Kernel*<br/>
Lambda nebo objekt funkce, který přebírá\<argument typu "index _Rank>" a provádí paralelní výpočty.

*_Kernel_type*<br/>
Lambda nebo functor.

*_Rank*<br/>
Pořadí rozsahu.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence

Blokuje provádění všech podprocesů v dlaždici, dokud nebudou dokončeny všechny přístupy k nevyřízené `tile_static` paměti. Tím je `tile_static` zajištěno, že přístupy k paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a že přístupy jsou prováděny v pořadí programu.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Objekt tile_barrier.

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
