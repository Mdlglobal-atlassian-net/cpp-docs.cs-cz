---
title: writeonly_texture_view – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd92e403d9c83bf50bea2703cef6a4255c6245e3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414670"
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view – třída

Poskytuje přístup typu writeonly k textuře.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ prvků v textuře.

*_Rank*<br/>
Řád textury.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`scalar_type`||
|`value_type`|Typ prvků v textuře.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[writeonly_texture_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `writeonly_texture_view` třídy.|
|[~writeonly_texture_view Destructor](#ctor)|Odstraní `writeonly_texture_view` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[set](#set)|Nastaví hodnotu prvku na zadaném indexu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje zadaný `writeonly_texture_view` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RANK – konstanta](#rank)|Zjistí řád objektu `writeonly_texture_view` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** Concurrency::graphics

##  <a name="dtor"></a> ~ writeonly_texture_view

Odstraní `writeonly_texture_view` objektu.

```
~writeonly_texture_view() restrict(amp,cpu);
```

##  <a name="operator_eq"></a> operátor =

Zkopíruje zadaný `writeonly_texture_view` do tohoto objektu.

```
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`writeonly_texture_view` objekt bude kopírováno.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `writeonly_texture_view` objektu.

##  <a name="rank"></a> pořadí

Zjistí řád objektu `writeonly_texture_view` objektu.

```
static const int rank = _Rank;
```

##  <a name="set"></a> Nastavit

Nastaví hodnotu prvku na zadaném indexu.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku.

*value*<br/>
Nová hodnota prvku.

##  <a name="ctor"></a> writeonly_texture_view

Inicializuje novou instanci třídy `writeonly_texture_view` třídy.

```
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Řád textury.

*value_type*<br/>
Typ prvků v textuře.

*_Src*<br/>
Textury, který se používá k vytvoření `writeonly_texture_view`.

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
