---
title: writeonly_texture_view – třída
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 8978a548ed246c59d7e7f007f1180685c7343a14
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126237"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view – třída

Poskytuje přístup WriteOnly k textuře.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view;

template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ prvků v textuře.

*_Rank*<br/>
Rozměr textury.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`scalar_type`||
|`value_type`|Typ prvků v textuře.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[writeonly_texture_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `writeonly_texture_view`.|
|[~ writeonly_texture_view destruktor](#ctor)|Odstraní objekt `writeonly_texture_view`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[set](#set)|Nastaví hodnotu prvku na zadaném indexu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje zadaný objekt `writeonly_texture_view` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta Rank](#rank)|Získá pořadí objektu `writeonly_texture_view`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** Concurrency:: Graphics

## <a name="dtor"></a>~ writeonly_texture_view

Odstraní objekt `writeonly_texture_view`.

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator_eq"></a>operátor =

Zkopíruje zadaný objekt `writeonly_texture_view` do tohoto objektu.

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`writeonly_texture_view` objekt, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `writeonly_texture_view`.

## <a name="rank"></a>pořadí

Získá pořadí objektu `writeonly_texture_view`.

```cpp
static const int rank = _Rank;
```

## <a name="set"></a>stanovenými

Nastaví hodnotu prvku na zadaném indexu.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index elementu

*value*<br/>
Nová hodnota elementu.

## <a name="ctor"></a>writeonly_texture_view

Inicializuje novou instanci třídy `writeonly_texture_view`.

```cpp
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Rozměr textury.

*value_type*<br/>
Typ prvků v textuře.

*_Src*<br/>
Textura, která se používá k vytvoření `writeonly_texture_view`.

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
