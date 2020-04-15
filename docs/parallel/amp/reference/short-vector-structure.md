---
title: short_vector – struktura
ms.date: 11/04/2016
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
ms.openlocfilehash: fc2864477da80885b18dabb08b9ccbee30f31387
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374754"
---
# <a name="short_vector-structure"></a>short_vector – struktura

short_vector poskytuje metaprogramovací definice, které jsou užitečné pro programování krátkých vektorů obecně.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename _Scalar_type,
    int _Size
>
struct short_vector;
template<>
struct short_vector<unsigned int, 1>;
template<>
struct short_vector<unsigned int, 2>;
template<>
struct short_vector<unsigned int, 3>;
template<>
struct short_vector<unsigned int, 4>;
template<>
struct short_vector<int, 1>;
template<>
struct short_vector<int, 2>;
template<>
struct short_vector<int, 3>;
template<>
struct short_vector<int, 4>;
template<>
struct short_vector<float, 1>;
template<>
struct short_vector<float, 2>;
template<>
struct short_vector<float, 3>;
template<>
struct short_vector<float, 4>;
template<>
struct short_vector<unorm, 1>;
template<>
struct short_vector<unorm, 2>;
template<>
struct short_vector<unorm, 3>;
template<>
struct short_vector<unorm, 4>;
template<>
struct short_vector<norm, 1>;
template<>
struct short_vector<norm, 2>;
template<>
struct short_vector<norm, 3>;
template<>
struct short_vector<norm, 4>;
template<>
struct short_vector<double, 1>;
template<>
struct short_vector<double, 2>;
template<>
struct short_vector<double, 3>;
template<>
struct short_vector<double, 4>;
```

### <a name="parameters"></a>Parametry

*_Scalar_type*<br/>

*_Size*<br/>

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[short_vector::short_vector konstruktor](#ctor)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`short_vector`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors.h

**Obor názvů:** Souběžnost::grafiky

## <a name="short_vectorshort_vector-constructor"></a><a name="ctor"></a>short_vector::short_vector konstruktor

```cpp
short_vector();
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
