---
title: short_vector_traits – struktura
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: d743f74deaea5cb31cd609ece90891c8cfe2258f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374737"
---
# <a name="short_vector_traits-structure"></a>short_vector_traits – struktura

short_vector_traits umožňuje načtení základní délky vektoru a skalárního typu krátkého vektorového typu nebo skalárního typu

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

### <a name="parameters"></a>Parametry

`T`

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[short_vector_traits::short_vector_traits konstruktor](#ctor)||

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[short_vector_traits::Konstanta velikosti](#size)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`short_vector_traits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors.h

**Obor názvů:** Souběžnost::grafiky

## <a name="short_vector_traitsshort_vector_traits-constructor"></a><a name="ctor"></a>short_vector_traits::short_vector_traits konstruktor

```cpp
short_vector_traits();
```

## <a name="short_vector_traitssize-constant"></a><a name="size"></a>short_vector_traits::Konstanta velikosti

```cpp
static int const size = 1;
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
