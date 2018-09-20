---
title: Texture – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ae251ace53f8a2a591a311cd389f7084099988e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420120"
---
# <a name="texture-class"></a>texture – třída

Textura je souhrn dat na `accelerator_view` v rozšířené doméně. Jde o kolekci proměnných, jedna pro každý prvek v rozšířené doméně. Každá proměnná obsahuje hodnotu odpovídající primitivnímu typu jazyka C++ ( `unsigned int`, `int`, `float`, `double`), skalární typu ( `norm`, nebo `unorm`), nebo typu short vector.

## <a name="syntax"></a>Syntaxe

```
template <typename value_type,  int _Rank>
class texture;
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
|`scalar_type`|Skalární typy.|
|`value_type`|Typy hodnot.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Texture – konstruktor](#ctor)|Inicializuje novou instanci třídy `texture` třídy.|
|[~ texture – destruktor](#ctor)|Odstraní `texture` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[copy_to](#copy_to)|Kopie `texture` na cíl provedením hluboké kopie.|
|[data](#data)|Vrátí ukazatel CPU na nezpracovaná data této textury.|
|[get](#get)|Vrátí hodnotu prvku na zadaném indexu.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, zkopírovány do této textury.|
|[get_depth_pitch](#get_depth_pitch)|Vrátí počet bajtů mezi každou hloubkou řezu v pracovní 3D textuře na CPU.|
|[get_row_pitch](#get_row_pitch)|Vrátí počet bajtů mezi každým řádkem ve 2D nebo 3D pracovní textuře na CPU.|
|[set](#set)|Nastaví hodnotu prvku na zadaném indexu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator()](#operator_call)|Vrátí hodnotu prvku určeného parametry.|
|[Operator [].](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[operátor =](#operator_eq)|Zkopíruje zadaný [textury](texture-class.md) do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RANK – konstanta](#rank)|Zjistí řád objektu `texture` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, zkopírovány do této textury.|
|[depth_pitch](#depth_pitch)|Získá počet bajtů mezi každou hloubkou řezu v pracovní 3D textuře na CPU.|
|[row_pitch](#row_pitch)|Získá počet bajtů mezi každým řádkem ve 2D nebo 3D pracovní textuře na CPU.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Texture_base`

`texture`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** Concurrency::graphics

##  <a name="dtor"></a> ~ textury

Odstraní `texture` objektu.

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view –

Získá [accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, zkopírovány do této textury.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to –

Kopie `texture` na cíl provedením hluboké kopie.

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Objekt, který chcete zkopírovat do.

*_Rank*<br/>
Řád textury.

*value_type*<br/>
Typ prvků v textuře.

##  <a name="data"></a> Data

Vrátí ukazatel CPU na nezpracovaná data této textury.

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná data textury.

##  <a name="depth_pitch"></a> depth_pitch

Získá počet bajtů mezi každou hloubkou řezu v pracovní 3D textuře na CPU.

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> získat

Vrátí hodnotu prvku na zadaném indexu.

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku.

### <a name="return-value"></a>Návratová hodnota

Hodnotu prvku na zadaném indexu.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view –

Vrátí accelerator_view, který je upřednostňovaným cílem, do kterého má být zkopírován do tato textura.

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

[Accelerator_view](accelerator-view-class.md) , který je upřednostňovaným cílem, zkopírovány do této textury.

##  <a name="get_depth_pitch"></a> get_depth_pitch

Vrátí počet bajtů mezi každou hloubkou řezu v pracovní 3D textuře na CPU.

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

Počet bajtů mezi každou hloubkou řezu v pracovní 3D textuře na CPU.

##  <a name="get_row_pitch"></a> get_row_pitch

Vrátí počet bajtů mezi každým řádkem ve 2 trojrozměrné pracovní textuře, nebo mezi každým řádkem hloubkou řezu v trojrozměrné 3 pracovní textuře.

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

Počet bajtů mezi každým řádkem ve 2 trojrozměrné pracovní textuře, nebo mezi každým řádkem hloubkou řezu v trojrozměrné 3 pracovní textuře.

##  <a name="operator_call"></a> Operator()

Vrátí hodnotu prvku určeného parametry.

```
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
Nejvýznamnější komponenta indexu.

*_I1*<br/>
Další na nejvýznamnější komponenta indexu.

*_I2*<br/>
Nejméně významná komponenta indexu.

*_Rank*<br/>
Řád indexu.

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku určeného parametry.

##  <a name="operator_at"></a> Operator [].

Vrátí prvek, který je v zadaném indexu.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

*_I0*<br/>
Index.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je v zadaném indexu.

##  <a name="operator_eq"></a> operátor =

Zkopíruje zadaný [textury](texture-class.md) do tohoto objektu.

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`texture` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `texture` objektu.

##  <a name="rank"></a> pořadí

Zjistí řád objektu `texture` objektu.

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

Získá počet bajtů mezi každým řádkem ve 2D nebo 3D pracovní textuře na CPU.

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> Nastavit

Nastaví hodnotu prvku na zadaném indexu.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku.

*_Rank*<br/>
Řád indexu.

*value*<br/>
Nová hodnota prvku.

##  <a name="ctor"></a> Textury

Inicializuje novou instanci třídy `texture` třídy.

```
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
Accelerator_view, který určuje upřednostňovaný cíl pro kopie do nebo z této textury.

*_Bits_per_scalar_element*<br/>
Počet bitů na každý skalární prvek v základním skalárním typu textury. Obecně jsou podporovány hodnoty 8, 16, 32 a 64. Pokud zadáte hodnotu 0, počet bitů je stejný jako základní scalar_type. 64 je platná pouze pro double textury.

*_Ext*<br/>
Rozsah v každé dimenzi textury.

*_E0*<br/>
Nejdůležitější součást textury.

*_E1*<br/>
Další na nejvýznamnější komponenta textury.

*_E2*<br/>
Nejméně významná komponenta rozsahu textury.

*_Input_iterator*<br/>
Typ vstupního iterátoru.

*_Mipmap_levels*<br/>
Počet úrovní mipmap u podkladové textury. Pokud zadáte hodnotu 0, bude mít textura plný rozsah úrovní mipmap na nejmenší možnou hodnotu pro zadaný rozsah.

*_Rank*<br/>
Řád rozsahu.

*_Zdroj*<br/>
Ukazatel do vyrovnávací paměti hostitele.

*_Src*<br/>
Chcete-li kopírovat texturu.

*_Src_byte_size*<br/>
Počet bajtů ve zdrojové vyrovnávací paměti.

*_Src_first*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_Src_last*<br/>
Koncový iterátor do zdrojového kontejneru.

*Ji_né*<br/>
Jiný zdroj dat.

*_Rank*<br/>
Řád oddílu.

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
