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
ms.openlocfilehash: 90a23ce111f7307610de3f0ad4bcec05d8de27df
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126893"
---
# <a name="concurrency-namespace-functions-amp"></a>Funkce oboru názvů Concurrency (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange – funkceC++ (amp)](#atomic_exchange)|[atomic_fetch_add – funkceC++ (amp)](#atomic_fetch_add)|[atomic_fetch_and – funkceC++ (amp)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or – funkceC++ (amp)](#atomic_fetch_or)|[atomic_fetch_sub – funkceC++ (amp)](#atomic_fetch_sub)|
|[atomic_fetch_xor – funkceC++ (amp)](#atomic_fetch_xor)|[kopií](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each – funkceC++ (amp)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a>all_memory_fence

Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do paměti. Tím se zajistí, že všechny přístupy do paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a jsou spouštěny v pořadí programu.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Objekt `tile_barrier`.

## <a name="amp_uninitialize"></a>amp_uninitialize

Zruší inicializaci modulu runtime C++ amp. Je právním voláním této funkce během života aplikací několikrát volat. Volání všech C++ rozhraní API amp po volání této funkce způsobí opětovnou C++ inicializaci modulu runtime amp. Všimněte si, že je nedovoleno používat C++ v volání této funkce objekty amp a v důsledku toho dojde k nedefinovanému chování. Také souběžné volání této funkce a všech dalších rozhraní API AMP je neplatné a by mohlo vést k nedefinovanému chování.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a>atomic_compare_exchange

Atomicky porovnává hodnotu uloženou v paměťovém umístění určeném v prvním argumentu pro rovnost s hodnotou druhého zadaného argumentu, a pokud jsou hodnoty stejné, hodnota v umístění paměti je změněna na hodnotu třetího zadaného argumentu.

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
Umístění, ze kterého se má porovnat jedna z hodnot, a do které se má uložit nová hodnota (pokud nějaká je).

*_Expected_value*<br/>
Umístění, ze kterého se má porovnat druhá hodnota, je čtena.

*value*<br/>
Hodnota, která má být uložena do umístění v paměti určené v parametru `_Dest`, pokud je `_Dest` rovna `_Expected_value`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je operace úspěšná; v opačném případě **false**.

## <a name="atomic_exchange"></a>atomic_exchange – funkceC++ (amp)

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

*value*<br/>
Nová hodnota.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota cílového umístění.

## <a name="atomic_fetch_add"></a>atomic_fetch_add – funkceC++ (amp)

Atomicky přidejte hodnotu do hodnoty umístění v paměti.

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
Ukazatel na umístění v paměti.

*value*<br/>
Hodnota, která má být přidána.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění v paměti.

## <a name="atomic_fetch_and"></a>atomic_fetch_and – funkceC++ (amp)

Atomicky provádí bitové a operace s hodnotou a hodnotou umístění v paměti.

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
Ukazatel na umístění v paměti.

*value*<br/>
Hodnota, která má být použita v bitovém a výpočtovém.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění v paměti.

## <a name="atomic_fetch_dec"></a>atomic_fetch_dec

Atomicky snižuje hodnotu uloženou v zadaném umístění v paměti.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Umístění v paměti hodnoty, která se má snížit

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v umístění v paměti.

## <a name="atomic_fetch_inc"></a>atomic_fetch_inc

Atomicky zvýší hodnotu uloženou v zadaném umístění v paměti.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Umístění v paměti hodnoty, která se má zvýšit.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v umístění v paměti.

## <a name="atomic_fetch_max"></a>atomic_fetch_max

Atomicky vypočítá maximální hodnotu mezi hodnotou uloženou v umístění v paměti zadaném v prvním argumentu a hodnotou zadanou ve druhém argumentu a uloží ji na stejné místo v paměti.

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
Umístění, ze kterého se má porovnat jedna z hodnot, a do kterých se mají uložit maximum ze dvou hodnot.

*value*<br/>
Hodnota, která má být porovnána s hodnotou v zadaném umístění.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v zadaném umístění.

## <a name="atomic_fetch_min"></a>atomic_fetch_min

Atomicky vypočítá minimální hodnotu mezi hodnotou uloženou v umístění v paměti zadaném v prvním argumentu a hodnotou zadanou ve druhém argumentu a uloží ji na stejné místo v paměti.

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
Umístění, ze kterého se má porovnat jedna z hodnot, a do kterých se budou ukládat minimální hodnoty dvou hodnot.

*value*<br/>
Hodnota, která má být porovnána s hodnotou v zadaném umístění.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota uložená v zadaném umístění.

## <a name="atomic_fetch_or"></a>atomic_fetch_or – funkceC++ (amp)

Atomicky provádí bitové operace nebo operaci s hodnotou a hodnotou umístění v paměti.

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
Ukazatel na umístění v paměti.

*value*<br/>
Hodnota, která má být použita v bitovém nebo výpočtovém.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění v paměti.

## <a name="atomic_fetch_sub"></a>atomic_fetch_sub – funkceC++ (amp)

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

*value*<br/>
Hodnota, která má být odečtena.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění v paměti.

## <a name="atomic_fetch_xor"></a>atomic_fetch_xor – funkceC++ (amp)

Atomicky provádí operaci bitové operace XOR hodnoty a umístění v paměti.

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
Ukazatel na umístění v paměti.

*value*<br/>
Hodnota, která se má použít při výpočtu XOR.

### <a name="return-value"></a>Návratová hodnota

Původní hodnota umístění v paměti.

## <a name="copy"></a>kopií

Zkopíruje objekt C++ amp. Jsou splněné všechny požadavky synchronního přenosu dat. Data nelze kopírovat při spuštění kódu v akcelerátoru. Obecná forma této funkce je `copy(src, dest)`.

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
Objekt, do kterého se má kopírovat.

*_DestIter*<br/>
Výstupní iterátor na počáteční pozici v cíli.

*InputIterator*<br/>
Typ vstupního iterátoru.

*OutputIterator*<br/>
Typ výstupního iterátoru.

*_Rank*<br/>
Pořadí objektu, ze kterého se má kopírovat, nebo objekt, do kterého se mají kopírovat.

*_Src*<br/>
Do objektu ke zkopírování.

*_SrcFirst*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_SrcLast*<br/>
Koncový iterátor do zdrojového kontejneru.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

## <a name="copy_async"></a>copy_async

Zkopíruje objekt C++ amp a vrátí objekt [completion_future](completion-future-class.md) , na kterém může být očekáváno. Data nelze kopírovat při spuštění kódu v akcelerátoru.  Obecná forma této funkce je `copy(src, dest)`.

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
Objekt, do kterého se má kopírovat.

*_DestIter*<br/>
Výstupní iterátor na počáteční pozici v cíli.

*InputIterator*<br/>
Typ vstupního iterátoru.

*OutputIterator*<br/>
Typ výstupního iterátoru.

*_Rank*<br/>
Pořadí objektu, ze kterého se má kopírovat, nebo objekt, do kterého se mají kopírovat.

*_Src*<br/>
Do objektu ke zkopírování.

*_SrcFirst*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_SrcLast*<br/>
Koncový iterátor do zdrojového kontejneru.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

### <a name="return-value"></a>Návratová hodnota

`future<void>`, na které může být očekáváno.

## <a name="direct3d_abort"></a>direct3d_abort

Přeruší provádění funkce s klauzulí omezení `restrict(amp)`. Když modul runtime AMP detekuje volání, vyvolá výjimku [runtime_exception](runtime-exception-class.md) s chybovou zprávou "rastrový obraz odkazu: volání metody přerušení shaderu".

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a>direct3d_errorf

Vytiskne formátovaný řetězec do okna výstupu sady Visual Studio. Je volána z funkce s klauzulí omezení `restrict(amp)`. Když modul runtime AMP detekuje volání, vyvolá výjimku [runtime_exception](runtime-exception-class.md) se stejným formátovacím řetězcem.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a>direct3d_printf

Vytiskne formátovaný řetězec do okna výstupu sady Visual Studio. Je volána z funkce s klauzulí omezení `restrict(amp)`.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a>global_memory_fence

Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do globální paměti. Tím se zajistí, že globální přístup k paměti bude viditelný pro ostatní vlákna v dlaždici vlákna a spustí se v pořadí programu.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Objekt tile_barrier

## <a name="parallel_for_each"></a>parallel_for_each – funkceC++ (amp)

Spustí funkci napříč výpočetní doménou. Další informace najdete v tématu [ C++ věnovaném amp Overview](../../../parallel/amp/cpp-amp-overview.md).

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
Objekt `accelerator_view` pro spuštění paralelního výpočtu.

*_Compute_domain*<br/>
Objekt `extent`, který obsahuje data pro výpočet.

*_Dim0*<br/>
Dimenze objektu `tiled_extent`.

*_Dim1*<br/>
Dimenze objektu `tiled_extent`.

*_Dim2*<br/>
Dimenze objektu `tiled_extent`.

*_Kernel*<br/>
Výraz lambda nebo objekt funkce, který přebírá argument typu index\<_Rank > a provádí paralelní výpočet.

*_Kernel_type*<br/>
Lambda nebo funktor.

*_Rank*<br/>
Rozměr rozsahu.

## <a name="tile_static_memory_fence"></a>tile_static_memory_fence

Blokuje spuštění všech vláken v dlaždici, dokud nebudou dokončeny všechny zbývající `tile_static` přístupy k paměti. Tím je zajištěno, že přístup `tile_static` paměti je viditelný pro ostatní vlákna v dlaždici vlákna a že se k nim budou spouštět v pořadí programu.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Barrier*<br/>
Objekt tile_barrier.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
