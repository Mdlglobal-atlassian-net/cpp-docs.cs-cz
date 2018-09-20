---
title: Funkce oboru názvů Concurrency::Graphics | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_graphics/Concurrency::fast_math::copy_async
- amp_graphics/Concurrency::fast_math::copy
dev_langs:
- C++
ms.assetid: ace01cd5-29d3-4356-930e-c81a61c5f934
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa9c59a190a0fdcc8c6d7557feea4bc19061480
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397998"
---
# <a name="concurrencygraphics-namespace-functions"></a>Funkce oboru názvů Concurrency::Graphics

|||
|-|-|
|[kopírování](#copy)|[copy_async](#copy_async)|

##  <a name="copy"></a>  copy – funkce (Namespace Concurrency::graphics)

Zkopíruje zdrojovou texturu do cílové vyrovnávací paměti, nebo zkopíruje zdrojovou vyrovnávací paměť do cílové vyrovnávací paměti. Obecný tvar této funkce je `copy(src, dest)`.

```
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
Rozsah oddílu textury ke kopírování.

*_Dst*<br/>
Objekt, který chcete zkopírovat do.

*_Dst_byte_size*<br/>
Počet bajtů v cíli.

*_Dst_type*<br/>
Typ cílového objektu.

*_Dst_offset*<br/>
Posun na požadované místo, kam chcete začít kopírovat.

*InputIterator*<br/>
Typ vstupního iterátoru.

*OutputIterator*<br/>
Typ výstupního iterátoru.

*_Src*<br/>
Kopírovaný objekt.

*_Src_byte_size*<br/>
Počet bajtů ve zdroji.

*_Src_type*<br/>
Typ zdrojového objektu.

*_Src_offset*<br/>
Posun do zdroje, ze kterého chcete začít kopírovat.

*první*<br/>
Počáteční iterátor do zdrojového kontejneru.

*poslední*<br/>
Koncový iterátor do zdrojového kontejneru.

##  <a name="copy_async"></a>  copy_async – funkce (Namespace Concurrency::graphics)

Asynchronně zkopíruje zdrojovou texturu do cílové vyrovnávací paměti, nebo zkopíruje zdrojovou vyrovnávací paměť do cílové vyrovnávací paměti a vrátí [completion_future](completion-future-class.md) objekt, který lze čekat. Data nelze kopírovat, pokud je kód spuštěn na akcelerátoru. Obecný tvar této funkce je `copy(src, dest)`.

```
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
Rozsah oddílu textury ke kopírování.

*_Dst*<br/>
Objekt, který chcete zkopírovat do.

*_Dst_byte_size*<br/>
Počet bajtů v cíli.

*_Dst_type*<br/>
Typ cílového objektu.

*_Dst_offset*<br/>
Posun na požadované místo, kam chcete začít kopírovat.

*InputIterator*<br/>
Typ vstupního iterátoru.

*OutputIterator*<br/>
Typ výstupního iterátoru.

*_Src*<br/>
Kopírovaný objekt.

*_Src_byte_size*<br/>
Počet bajtů ve zdroji.

*_Src_type*<br/>
Typ zdrojového objektu.

*_Src_offset*<br/>
Posun do zdroje, ze kterého chcete začít kopírovat.

*první*<br/>
Počáteční iterátor do zdrojového kontejneru.

*poslední*<br/>
Koncový iterátor do zdrojového kontejneru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** Concurrency::graphics

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
