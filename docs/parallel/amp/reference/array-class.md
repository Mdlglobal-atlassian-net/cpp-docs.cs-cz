---
title: array – třída
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127109"
---
# <a name="array-class"></a>array – třída

Představuje datový kontejner, který slouží k přesunu dat do akcelerátoru.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementu dat.

*_Rank*<br/>
Rozměr pole.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Array – konstruktor](#ctor)|Inicializuje novou instanci třídy `array`.|
|[~ Array – destruktor](#dtor)|Odstraní objekt `array`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[copy_to](#copy_to)|Zkopíruje obsah pole do jiného pole.|
|[údajů](#data)|Vrátí ukazatel na nezpracovaná data pole.|
|[get_accelerator_view](#get_accelerator_view)|Vrátí objekt [accelerator_view](accelerator-view-class.md) , který představuje umístění, kde je pole přiděleno. Tato vlastnost je k dispozici pouze na CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Získá druhý objekt [accelerator_view](accelerator-view-class.md) , který je předán jako parametr při volání pracovního konstruktoru pro vytvoření instance objektu `array`.|
|[get_cpu_access_type](#get_cpu_access_type)|Vrátí [access_type](concurrency-namespace-enums-amp.md#access_type) pole. Tato metoda je k dispozici pouze na CPU.|
|[get_extent](#get_extent)|Vrátí objekt [rozsahu](extent-class.md) pole.|
|[reinterpret_as](#reinterpret_as)|Vrátí jednorozměrné pole, které obsahuje všechny prvky v objektu `array`.|
|[section](#section)|Vrátí dílčí část objektu `array`, která se nachází na zadaném umístění, a volitelně, která má zadaný rozsah.|
|[view_as](#view_as)|Vrátí objekt [array_view](array-view-class.md) , který je vytvořen z objektu `array`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor std:: Vector&lt;value_type&gt;](#operator_vec)|Používá `copy(*this, vector)` k implicitnímu převodu pole na objekt std::[Vector](../../../standard-library/vector-class.md) .|
|[operator () – operátor](#operator_call)|Vrátí hodnotu prvku určenou parametry.|
|[operátor\[\]](#operator_at)|Vrátí prvek, který je na zadaném indexu.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `array` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta Rank](#rank)|Ukládá rozměr pole.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Získá objekt [accelerator_view](accelerator-view-class.md) , který představuje umístění, kde je pole přiděleno. Tato vlastnost je k dispozici pouze na CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Získá druhý objekt [accelerator_view](accelerator-view-class.md) , který je předán jako parametr při volání pracovního konstruktoru pro vytvoření instance objektu `array`.|
|[cpu_access_type](#cpu_access_type)|Získá [access_type](concurrency-namespace-enums-amp.md#access_type) , který představuje, jak má procesor získat přístup k úložišti daného pole.|
|[stavební](#extent)|Získá rozsah definující tvar pole.|

## <a name="remarks"></a>Poznámky

Typ `array<T,N>` představuje husté a běžné (nezubaté) *N*-dimenzionální pole, které je umístěno v konkrétním umístění, například akcelerátoru nebo procesoru. Datový typ prvků v poli je `T`, který musí být typu, který je kompatibilní s cílovým akcelerátorem. I když je pořadí, `N`(pole je určeno staticky a je součástí typu, je rozsah pole určen modulem runtime a je vyjádřen pomocí `extent<N>`třídy.

Pole může mít libovolný počet rozměrů, i když některé funkce jsou specializované pro `array` objekty s pořadím jedna, dvě a tři. Vynecháte-li argument dimenze, výchozí hodnota je 1.

Data pole jsou rozložena souvisle v paměti. Prvky, které se liší v nejméně významném rozměru, jsou sousední v paměti.

Pole jsou logicky považovány za typy hodnot, protože když je pole zkopírováno do jiného pole, je provedena hluboká kopie. Dvě pole nikdy neodkazují na stejná data.

Typ `array<T,N>` se používá v několika scénářích:

- Jako kontejner dat, který lze použít v výpočtech v akcelerátoru.

- Jako datový kontejner pro ukládání paměti na CPU hostitele (který lze použít ke kopírování do a z jiných polí).

- Jako pracovní objekt, který bude fungovat jako rychlý prostředník při kopiích z hostitelů na zařízení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`array`

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="dtor"></a>~ pole

Odstraní objekt `array`.

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

Získá objekt [accelerator_view](accelerator-view-class.md) , který představuje umístění, kde je pole přiděleno. Tato vlastnost je k dispozici pouze na CPU.

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>skupin

Inicializuje novou instanci [třídy Array](array-class.md). Pro `array<T,N>`není k dispozici žádný výchozí konstruktor. Všechny konstruktory jsou spuštěny pouze na CPU. Nelze je spustit na cíli Direct3D.

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Associated_Av*<br/>
Accelerator_view, která určuje preferované cílové umístění pole.

*_Av*<br/>
Objekt [accelerator_view](accelerator-view-class.md) , který určuje umístění pole.

*_Cpu_access_type*<br/>
Požadovaná [access_type](concurrency-namespace-enums-amp.md#access_type) pro pole na procesoru. Tento parametr má výchozí hodnotu `access_type_auto` opustit procesor `access_type` určení modulu runtime. Skutečný `access_type` procesoru pro pole lze dotazovat pomocí metody `get_cpu_access_type`.

*_Extent*<br/>
Rozsah v každé dimenzi pole.

*_E0*<br/>
Nejvýznamnější součást rozsahu této části.

*_E1*<br/>
Další nejvýznamnější součást rozsahu této části...

*_E2*<br/>
Nejméně významná komponenta rozsahu tohoto oddílu.

*_InputIterator*<br/>
Typ vstupního iterátoru.

*_Src*<br/>
Do objektu ke zkopírování.

*_Src_first*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_Src_last*<br/>
Koncový iterátor do zdrojového kontejneru.

*_Other*<br/>
Jiný zdroj dat.

*_Rank*<br/>
Pořadí oddílu

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Získá druhý objekt [accelerator_view](accelerator-view-class.md) , který je předán jako parametr při volání pracovního konstruktoru pro vytvoření instance objektu `array`.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Zkopíruje obsah `array` do jiného `array`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Objekt [array_view](array-view-class.md) ke zkopírování.

## <a name="cpu_access_type"></a>cpu_access_type

Získá access_type pro toto pole povolený procesor.

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>údajů

Vrátí ukazatel na nezpracovaná data `array`.

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná data pole.

## <a name="extent"></a>stavební

Získá objekt [rozsahu](extent-class.md) , který definuje tvar `array`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

Vrátí objekt [accelerator_view](accelerator-view-class.md) , který představuje umístění, kde je objekt `array` přidělen. Tato vlastnost je k dispozici pouze na CPU.

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt `accelerator_view`, který představuje umístění, kde je přidělen objekt `array`.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Získá druhý objekt [accelerator_view](accelerator-view-class.md) , který je předán jako parametr při volání pracovního konstruktoru pro vytvoření instance objektu `array`.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Návratová hodnota

Druhý objekt [accelerator_view](accelerator-view-class.md) předaný pracovnímu konstruktoru.

## <a name="get_cpu_access_type"></a>get_cpu_access_type

Vrátí access_type procesoru, který je povolený pro toto pole.

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

## <a name="get_extent"></a>get_extent

Vrátí objekt [rozsahu](extent-class.md) `array`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Objekt `extent` `array`

## <a name="operator_vec"></a>operátor std:: Vector&lt;value_type&gt;

Používá `copy(*this, vector)` k implicitnímu převodu pole na objekt std:: vector.

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Datový typ prvků vektoru.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `vector<T>` obsahující kopii dat, která je obsažena v poli.

## <a name="operator_call"></a>operator () – operátor

Vrátí hodnotu prvku určenou parametry.

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Umístění elementu.

*_I0*<br/>
Nejvýznamnější součást počátku této části.

*_I1*<br/>
Další důležitou součást počátku této části.

*_I2*<br/>
Nejméně významná součást počátku této části.

*_I*<br/>
Umístění elementu.

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku zadaná parametry.

## <a name="operator_at"></a>operator [] – operátor

Vrátí prvek, který je na zadaném indexu.

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

*_I*<br/>
Index.

### <a name="return-value"></a>Návratová hodnota

Element, který je na zadaném indexu.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu `array`.

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `array`, ze kterého se má kopírovat.

*_Src*<br/>
Objekt `array`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `array`.

## <a name="rank"></a>pořadí

Ukládá pořadí `array`.

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

Znovu interpretuje pole pomocí jednorozměrného array_view, který volitelně může mít jiný typ hodnoty než zdrojové pole.

### <a name="syntax"></a>Syntaxe

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Value_type2*<br/>
Datový typ vrácených dat.

### <a name="return-value"></a>Návratová hodnota

Objekt array_view array_view nebo const, který je založen na poli, s typem prvku, který je překládán z T na ElementType a pořadím sníženým od N do 1.

### <a name="remarks"></a>Poznámky

Někdy je vhodné zobrazit multidimenzionální pole, jako by se jedná o lineární jednorozměrné pole, které může mít jiný typ hodnoty než zdrojové pole. Tuto metodu můžete dosáhnout pomocí této metody.
**Upozornění** Přeinterpretace objektu Array pomocí jiného typu hodnoty je potenciálně nebezpečná operace. Tuto funkci doporučujeme používat pečlivě.

Následující kód poskytuje příklad.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>section

Vrátí dílčí část objektu `array`, která se nachází na zadaném umístění, a volitelně, která má zadaný rozsah.

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_E0*<br/>
Nejvýznamnější součást rozsahu této části.

*_E1*<br/>
Další nejvýznamnější součást rozsahu této části...

*_E2*<br/>
Nejméně významná komponenta rozsahu tohoto oddílu.

*_Ext*<br/>
Objekt [rozsahu](extent-class.md) , který určuje rozsah oddílu. Počátek je 0.

*_Idx*<br/>
Objekt [indexu](index-class.md) , který určuje umístění původu. Dílčí část je zbývající část rozsahu.

*_I0*<br/>
Nejvýznamnější součást počátku této části.

*_I1*<br/>
Další důležitou součást počátku této části.

*_I2*<br/>
Nejméně významná součást počátku této části.

*_Rank*<br/>
Pořadí oddílu

*_Section_extent*<br/>
Objekt [rozsahu](extent-class.md) , který určuje rozsah oddílu.

*_Section_origin*<br/>
Objekt [indexu](index-class.md) , který určuje umístění původu.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí dílčí část objektu `array`, která se nachází na zadaném umístění, a volitelně, která má zadaný rozsah. Je-li zadán pouze objekt `index`, obsahuje dílčí část všechny prvky v přidružené mřížce, které mají indexy větší než indexy prvků v objektu `index`.

## <a name="view_as"></a>view_as

Přeloží toto pole jako [array_view](array-view-class.md) jiného pořadí.

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_New_rank*<br/>
Pořadí objektu `extent` předaného jako parametr.

*_View_extent*<br/>
Rozsah, který se používá k vytvoření nového objektu [array_view](array-view-class.md) .

*value_type*<br/>
Datový typ prvků v původním objektu `array` a vráceném objektu `array_view`.

### <a name="return-value"></a>Návratová hodnota

Objekt [array_view](array-view-class.md) , který je vytvořen.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
