---
title: Funkce oboru názvů Concurrency::graphics
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::fast_math::copy_async
- amp_graphics/Concurrency::fast_math::copy
ms.assetid: ace01cd5-29d3-4356-930e-c81a61c5f934
ms.openlocfilehash: 776f715f72d2e3b6b3841856323a52953e9c5344
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376329"
---
# <a name="concurrencygraphics-namespace-functions"></a>Funkce oboru názvů Concurrency::graphics

|||
|-|-|
|[Kopírovat](#copy)|[copy_async](#copy_async)|

## <a name="copy-function-concurrencygraphics-namespace"></a><a name="copy"></a>funkce kopírování (souběžnost::grafický obor názvů)

Zkopíruje zdrojovou texturu do cílové vyrovnávací paměti nebo zkopíruje zdrojovou vyrovnávací paměť do cílové vyrovnávací paměti. Obecná forma této funkce `copy(src, dest)`je .

```cpp
template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type>
>
void copy (
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size,
    _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>void copy(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent, OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture,
    void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>Parametry

*_Copy_extent*<br/>
Rozsah části textury, která má být zkopírována.

*_Dst*<br/>
Objekt, do který chcete kopírovat.

*_Dst_byte_size*<br/>
Počet bajtů v cíli.

*_Dst_type*<br/>
Typ cílového objektu.

*_Dst_offset*<br/>
Posun do cíle, ve kterém chcete začít kopírování.

*Vstupní iterátor*<br/>
Typ vstupního iterátoru.

*Výstupní iterátor*<br/>
Typ výstupního iterátoru.

*_Src*<br/>
Chcete-li objekt kopírovat.

*_Src_byte_size*<br/>
Počet bajtů ve zdroji.

*_Src_type*<br/>
Typ zdrojového objektu.

*_Src_offset*<br/>
Posun do zdroje, ze kterého chcete začít kopírování.

*První*<br/>
Počáteční iterátor do zdrojového kontejneru.

*Poslední*<br/>
Koncový iterátor do zdrojového kontejneru.

## <a name="copy_async-function-concurrencygraphics-namespace"></a><a name="copy_async"></a>funkce copy_async (souběžnost::grafický obor názvů)

Asynchronně zkopíruje zdrojovou texturu do cílové vyrovnávací paměti nebo zkopíruje zdrojovou vyrovnávací paměť do cílové vyrovnávací paměti a potom vrátí [completion_future](completion-future-class.md) objekt, na který lze čekat. Data nelze zkopírovat, pokud je kód spuštěn na akcelerátoru. Obecná forma této funkce `copy(src, dest)`je .

```cpp
template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type &_Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>Parametry

*_Copy_extent*<br/>
Rozsah části textury, která má být zkopírována.

*_Dst*<br/>
Objekt, do který chcete kopírovat.

*_Dst_byte_size*<br/>
Počet bajtů v cíli.

*_Dst_type*<br/>
Typ cílového objektu.

*_Dst_offset*<br/>
Posun do cíle, ve kterém chcete začít kopírování.

*Vstupní iterátor*<br/>
Typ vstupního iterátoru.

*Výstupní iterátor*<br/>
Typ výstupního iterátoru.

*_Src*<br/>
Chcete-li objekt kopírovat.

*_Src_byte_size*<br/>
Počet bajtů ve zdroji.

*_Src_type*<br/>
Typ zdrojového objektu.

*_Src_offset*<br/>
Posun do zdroje, ze kterého chcete začít kopírování.

*První*<br/>
Počáteční iterátor do zdrojového kontejneru.

*Poslední*<br/>
Koncový iterátor do zdrojového kontejneru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Obor názvů:** Souběžnost::grafiky

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
