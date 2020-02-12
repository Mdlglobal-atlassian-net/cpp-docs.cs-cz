---
title: texture – třída
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: f7a38c84c5def629c7a42b2c05bf1ed04441593b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127774"
---
# <a name="texture-class"></a>texture – třída

Textura je datová agregace na `accelerator_view` v rozsahu domény. Jedná se o kolekci proměnných, jednu pro každý prvek v doméně rozsahu. Každá proměnná obsahuje hodnotu odpovídající C++ primitivnímu typu (`unsigned int`, `int`, `float`, `double`), skalárního typu (`norm`nebo `unorm`) nebo typu krátkého vektoru.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename value_type,  int _Rank>
class texture;
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
|`scalar_type`|Skalární typy.|
|`value_type`|Typy hodnot.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Konstruktor textury](#ctor)|Inicializuje novou instanci třídy `texture`.|
|[~ Texture – destruktor](#ctor)|Odstraní objekt `texture`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[copy_to](#copy_to)|Zkopíruje objekt `texture` do cílového umístění tím, že provede hlubokou kopii.|
|[údajů](#data)|Vrátí ukazatel CPU na nezpracovaná data této textury.|
|[get](#get)|Vrátí hodnotu prvku na zadaném indexu.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, do kterého má být tato textura zkopírována.|
|[get_depth_pitch](#get_depth_pitch)|Vrátí počet bajtů mezi každou hloubkou řezu v trojrozměrné pracovní textuře na CPU.|
|[get_row_pitch](#get_row_pitch)|Vrátí počet bajtů mezi každým řádkem ve 2D nebo 3D pracovní textuře na CPU.|
|[set](#set)|Nastaví hodnotu prvku na zadaném indexu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator () – operátor](#operator_call)|Vrátí hodnotu prvku určenou parametry.|
|[operátor\[\]](#operator_at)|Vrátí prvek, který je na zadaném indexu.|
|[operátor =](#operator_eq)|Zkopíruje zadaný objekt [textury](texture-class.md) do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta Rank](#rank)|Získá pořadí objektu `texture`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, do kterého má být tato textura zkopírována.|
|[depth_pitch](#depth_pitch)|Získá počet bajtů mezi každou hloubkou řezu v trojrozměrné pracovní textuře na CPU.|
|[row_pitch](#row_pitch)|Získá počet bajtů mezi jednotlivými řádky v 2D nebo 3D pracovní textuře na CPU.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Texture_base`

`texture`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** Concurrency:: Graphics

## <a name="dtor"></a>~ textura

Odstraní objekt `texture`.

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Získá [accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, do kterého má být tato textura zkopírována.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Zkopíruje objekt `texture` do cílového umístění tím, že provede hlubokou kopii.

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Objekt, do kterého se má kopírovat.

*_Rank*<br/>
Rozměr textury.

*value_type*<br/>
Typ prvků v textuře.

## <a name="data"></a>údajů

Vrátí ukazatel CPU na nezpracovaná data této textury.

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná data textury.

## <a name="depth_pitch"></a>depth_pitch

Získá počet bajtů mezi každou hloubkou řezu v trojrozměrné pracovní textuře na CPU.

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a>Čtěte

Vrátí hodnotu prvku na zadaném indexu.

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index elementu

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku na zadaném indexu.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Vrátí accelerator_view, který je upřednostňovaným cílem, do kterého má být tato textura zkopírována.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

[Accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, do kterého má být tato textura zkopírována.

## <a name="get_depth_pitch"></a>get_depth_pitch

Vrátí počet bajtů mezi každou hloubkou řezu v trojrozměrné pracovní textuře na CPU.

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

Počet bajtů mezi každou hloubkou řezu v trojrozměrné pracovní textuře na CPU.

## <a name="get_row_pitch"></a>get_row_pitch

Vrátí počet bajtů mezi jednotlivými řádky v dvojrozměrné pracovní textuře, nebo mezi každým řádkem hloubkového řezu v trojrozměrné pracovní textuře.

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

Počet bajtů mezi jednotlivými řádky v dvojrozměrné pracovní textuře nebo mezi každým řádkem hloubkového řezu v trojrozměrné pracovní textuře.

## <a name="operator_call"></a>operator () – operátor

Vrátí hodnotu prvku určenou parametry.

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

*_I0*<br/>
Nejvýznamnější součást indexu.

*_I1*<br/>
Další důležitou součást indexu.

*_I2*<br/>
Nejméně významná součást indexu.

*_Rank*<br/>
Pořadí indexu.

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku, která je určena parametry.

## <a name="operator_at"></a>operator [] – operátor

Vrátí prvek, který je na zadaném indexu.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

*_I0*<br/>
Index.

### <a name="return-value"></a>Návratová hodnota

Element, který je na zadaném indexu.

## <a name="operator_eq"></a>operátor =

Zkopíruje zadaný objekt [textury](texture-class.md) do tohoto objektu.

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `texture`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `texture`.

## <a name="rank"></a>pořadí

Získá pořadí objektu `texture`.

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a>row_pitch

Získá počet bajtů mezi jednotlivými řádky v 2D nebo 3D pracovní textuře na CPU.

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a>stanovenými

Nastaví hodnotu prvku na zadaném indexu.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index elementu

*_Rank*<br/>
Pořadí indexu.

*value*<br/>
Nová hodnota elementu.

## <a name="ctor"></a>textury

Inicializuje novou instanci třídy `texture`.

```cpp
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>Parametry

*_Acc_view*<br/>
[Accelerator_view](accelerator-view-class.md) , která určuje umístění textury.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) , která určuje umístění textury.

*_Associated_av*<br/>
Accelerator_view, který určuje preferovaný cíl pro kopírování do nebo z této textury.

*_Bits_per_scalar_element*<br/>
Počet bitů na každý skalární prvek v základním skalárním typu textury. Obecně podporovaná hodnota je 8, 16, 32 a 64. Je-li zadána hodnota 0, je počet bitů stejný jako základní scalar_type. 64 je platná pouze pro dvojité textury.

*_Ext*<br/>
Rozsah v každé dimenzi textury.

*_E0*<br/>
Nejvýznamnější součást textury.

*_E1*<br/>
Další důležitou součást textury.

*_E2*<br/>
Nejméně významná komponenta rozsahu textury.

*_Input_iterator*<br/>
Typ vstupního iterátoru.

*_Mipmap_levels*<br/>
Počet úrovní mipmap v základní texturě. Pokud je zadána hodnota 0, bude mít textura plný rozsah mipmap úrovní až do nejmenší možné velikosti v zadaném rozsahu.

*_Rank*<br/>
Rozměr rozsahu.

*_Source*<br/>
Ukazatel na vyrovnávací paměť hostitele.

*_Src*<br/>
Pro texturu ke zkopírování.

*_Src_byte_size*<br/>
Počet bajtů ve zdrojové vyrovnávací paměti.

*_Src_first*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_Src_last*<br/>
Koncový iterátor do zdrojového kontejneru.

*_Other*<br/>
Jiný zdroj dat.

*_Rank*<br/>
Pořadí oddílu

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
