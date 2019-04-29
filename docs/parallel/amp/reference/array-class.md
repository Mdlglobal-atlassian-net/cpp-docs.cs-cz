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
ms.openlocfilehash: 16d18d23c370a8a603ab6150fcee18455ae47c48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405505"
---
# <a name="array-class"></a>array – třída

Představuje datový kontejner, který se používá k přesunutí dat na akcelerátor.

## <a name="syntax"></a>Syntaxe

```
template <typename value_type, int _Rank>
friend class array;
```

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementu data.

*_Rank*<br/>
Řád objektu array.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Array – konstruktor](#ctor)|Inicializuje novou instanci třídy `array` třídy.|
|[~ array – destruktor](#dtor)|Odstraní `array` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[copy_to](#copy_to)|Zkopíruje obsah pole do jiného objektu array.|
|[data](#data)|Vrací ukazatel na nezpracovaná data objektu array.|
|[get_accelerator_view](#get_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) objekt, který představuje umístění, kde je přidělena pole. Tato vlastnost je přístupná pouze na CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který je předán jako parametr při zavolání pracovního konstruktoru pro vytvoření instance `array` objektu.|
|[get_cpu_access_type](#get_cpu_access_type)|Vrátí [access_type](concurrency-namespace-enums-amp.md#access_type) pole. Tato metoda je přístupná pouze na CPU.|
|[get_extent](#get_extent)|Vrátí [rozsahu](extent-class.md) objektu array.|
|[reinterpret_as](#reinterpret_as)|Vrátí jednorozměrné pole, která obsahuje všechny prvky `array` objektu.|
|[section](#section)|Vrátí dílčí část objektu `array` nacházející se na zadaném umístění a volitelně, který se zadaným rozsahem.|
|[view_as](#view_as)|Vrátí [array_view](array-view-class.md) objekt, který je vytvořen z `array` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor std::vector&lt;value_type&gt;](#operator_vec)|Používá `copy(*this, vector)` implicitně převést pole std::[vektoru](../../../standard-library/vector-class.md) objektu.|
|[operator()](#operator_call)|Vrátí hodnotu prvku určeného parametry.|
|[– Operátor\[\]](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `array` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RANK – konstanta](#rank)|Udržuje řád objektu pole.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) objekt, který představuje umístění, kde je přidělena pole. Tato vlastnost je přístupná pouze na CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který je předán jako parametr při zavolání pracovního konstruktoru pro vytvoření instance `array` objektu.|
|[cpu_access_type](#cpu_access_type)|Získá [access_type](concurrency-namespace-enums-amp.md#access_type) , která představuje, jak CPU může získat přístup k úložišti pole.|
|[rozsah](#extent)|Vrátí rozsah, který definuje tvar objektu array.|

## <a name="remarks"></a>Poznámky

Typ `array<T,N>` odpovídá hustému a běžné (nikoli roztřepenému) *N*-rozměrné pole, který je umístěný v určitém umístění, například akcelerátoru nebo procesoru. Datový typ prvků v poli je `T`, která musí být typu, který je kompatibilní s cílovým akcelerátorem. I když se přes řád je `N`, (z pole je určeno staticky a je součástí typu, rozsahu objektu array je určeno modulem runtime a je vyjádřeno pomocí třídy `extent<N>`.

Pole může mít libovolný počet dimenzí, i když některé funkce jsou specializované pro `array` objekty s hodností jeden, dva a tři. Pokud vynecháte argument dimenze, výchozí hodnota je 1.

Pole data uložena souvisle v paměti. Prvky, které se liší jednou nejméně významnou dimenzí v paměti sousedí.

Pole jsou logicky považovány za hodnotové typy, protože když objekt array zkopírován do jiného objektu array, provádí se hluboká kopie. Dva objekty Array nikdy neukazují na stejná data.

`array<T,N>` Typ se používá v několika situacích:

- Jako datový zásobník, který lze použít při výpočtech na akcelerátoru.

- Jako datový zásobník pro uložení paměti v procesoru hostitele (které je možné zkopírovat do a z jiných objektů Array).

- Jako pracovní objekt, který slouží jako rychlý zprostředkovatel při kopiích v hostitele do zařízení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`array`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Namespace:** Souběžnost

##  <a name="dtor"></a> ~ pole

Odstraní `array` objektu.

```
~array() restrict(cpu);
```

##  <a name="accelerator_view"></a> accelerator_view

Získá [accelerator_view](accelerator-view-class.md) objekt, který představuje umístění, kde je přidělena pole. Tato vlastnost je přístupná pouze na CPU.

```
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

##  <a name="ctor"></a> Pole

Inicializuje novou instanci třídy [array – třída](array-class.md). Neexistuje žádný výchozí konstruktor pro `array<T,N>`. Všechny konstruktory jsou spouštěny pouze na CPU. Nelze je spustit na cíli Direct3D.

```
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
Objekt typu accelerator_view určující preferované cílové umístění pole.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) objekt, který určuje umístění pole.

*_Cpu_access_type*<br/>
Požadovaný [access_type](concurrency-namespace-enums-amp.md#access_type) pro toto pole na CPU. Tento parametr má výchozí hodnotu `access_type_auto` byste museli opustit procesoru `access_type` určení modulu runtime. Aktuálního procesoru `access_type` pro pole může být dotázán pomocí `get_cpu_access_type` metody.

*_Extent*<br/>
Rozsah v každém rozměru pole.

*_E0*<br/>
Nejvýznamnější komponenta rozsahu tohoto oddílu.

*_E1*<br/>
Další na nejvýznamnější komponenta rozsahu tohoto oddílu.

*_E2*<br/>
Nejméně významná komponenta rozsahu tohoto oddílu.

*_InputIterator*<br/>
Typ vstupního iterátoru.

*_Src*<br/>
Kopírovaný objekt.

*_Src_first*<br/>
Počáteční iterátor do zdrojového kontejneru.

*_Src_last*<br/>
Koncový iterátor do zdrojového kontejneru.

*Ji_né*<br/>
Jiný zdroj dat.

*_Rank*<br/>
Řád oddílu.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

##  <a name="associated_accelerator_view"></a> associated_accelerator_view –

Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který je předán jako parametr při zavolání pracovního konstruktoru pro vytvoření instance `array` objektu.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to –

Zkopíruje obsah `array` do jiného `array`.

```
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
[Array_view](array-view-class.md) do kterého chcete zkopírovat.

##  <a name="cpu_access_type"></a> cpu_access_type

Získá access_type procesoru povolený pro toto pole.

```
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

##  <a name="data"></a> Data

Vrací ukazatel na nezpracovaná data `array`.

```
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná data objektu array.

##  <a name="extent"></a> rozsah

Získá [rozsahu](extent-class.md) objekt, který definuje tvar `array`.

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_accelerator_view"></a> get_accelerator_view –

Vrátí [accelerator_view](accelerator-view-class.md) objekt, který představuje umístění ve kterém `array` objektu je přiřazen. Tato vlastnost je přístupná pouze na CPU.

```
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Návratová hodnota

`accelerator_view` Objekt, který představuje umístění ve kterém `array` objektu je přiřazen.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který je předán jako parametr při zavolání pracovního konstruktoru pro vytvoření instance `array` objektu.

```
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Návratová hodnota

Druhá [accelerator_view](accelerator-view-class.md) předán objekt pracovního konstruktoru.

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

Vrátí access_type procesoru povolený pro toto pole.

```
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="get_extent"></a> get_extent –

Vrátí [rozsahu](extent-class.md) objektu `array`.

```
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

`extent` Objektu `array`.

##  <a name="operator_vec"></a> operátor std::vector&lt;value_type&gt;

Používá `copy(*this, vector)` implicitně převést pole na std::vector objektu.

```
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Datový typ prvků objektu vektoru.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `vector<T>` , který obsahuje kopii dat obsažených v poli.

##  <a name="operator_call"></a> Operator()

Vrátí hodnotu prvku určeného parametry.

```
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
Nejvýznamnější komponenta počátku tohoto oddílu.

*_I1*<br/>
Další na nejvýznamnější komponenta počátku tohoto oddílu.

*_I2*<br/>
Nejméně významná komponenta počátku tohoto oddílu.

*_I*<br/>
Umístění elementu.

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku určeného parametry.

##  <a name="operator_at"></a> Operator [].

Vrátí prvek, který je v zadaném indexu.

```
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

Prvek, který je v zadaném indexu.

##  <a name="operator_eq"></a> operátor =

Zkopíruje obsah zadaného `array` objektu.

```
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`array` Objektu, který chcete kopírovat.

*_Src*<br/>
`array` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `array` objektu.

##  <a name="rank"></a> pořadí

Udržuje řád objektu `array`.

```
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a> reinterpret_as

Opětovně interpretuje objekt array skrze jednorozměrný prvek array_view, který volitelně může mít typ jinou hodnotu než zdrojového pole.

### <a name="syntax"></a>Syntaxe

```
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Value_type2*<br/>
Datový typ vrácená data.

### <a name="return-value"></a>Návratová hodnota

Array_view nebo const objektu array_view, který je založen na poli, s typem elementu přetypovaným z T ElementType a řádem redukovaným z N na hodnotu 1.

### <a name="remarks"></a>Poznámky

Někdy je vhodné zobrazit vícerozměrné pole jako by byl lineární jednorozměrné pole, může mít typ jinou hodnotu než zdrojového pole. Tuto metodu můžete použít k dosažení tohoto cíle.
**Upozornění:** opětovná interpretace objektu array pomocí jiného typu hodnoty je potenciálně nebezpečná operace. Doporučujeme vám, že jste tuto funkci používat opatrně.

Následující kód obsahuje příklad.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> Oddíl

Vrátí dílčí část objektu `array` nacházející se na zadaném umístění a volitelně, který se zadaným rozsahem.

```
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
Nejvýznamnější komponenta rozsahu tohoto oddílu.

*_E1*<br/>
Další na nejvýznamnější komponenta rozsahu tohoto oddílu.

*_E2*<br/>
Nejméně významná komponenta rozsahu tohoto oddílu.

*_Ext*<br/>
[Rozsahu](extent-class.md) určující rozsah oddílu. Počátek je 0.

*_Idx*<br/>
[Index](index-class.md) určující umístění počátku. Dílčím oddílem je zbytek rozsahu.

*_I0*<br/>
Nejvýznamnější komponenta počátku tohoto oddílu.

*_I1*<br/>
Další na nejvýznamnější komponenta počátku tohoto oddílu.

*_I2*<br/>
Nejméně významná komponenta počátku tohoto oddílu.

*_Rank*<br/>
Řád oddílu.

*_Section_extent*<br/>
[Rozsahu](extent-class.md) určující rozsah oddílu.

*_Section_origin*<br/>
[Index](index-class.md) určující umístění počátku.

*value_type*<br/>
Datový typ prvků, které jsou zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí dílčí část objektu `array` nacházející se na zadaném umístění a volitelně, který se zadaným rozsahem. Když pouze `index` objektu je zadán, obsahuje dílčí část všechny prvky přidružené k mřížce, které mají indexy větší než indexy prvků v `index` objektu.

##  <a name="view_as"></a> view_as –

Opětovně interpretuje objekt toto pole jako [array_view](array-view-class.md) jiné hodnosti.

```
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_New_rank*<br/>
Řád objektu `extent` objekt předán jako parametr.

*_View_extent*<br/>
Rozsah, který se používá pro tvorbu nového [array_view](array-view-class.md) objektu.

*value_type*<br/>
Datový typ prvků v původním `array` objektu a ve vráceném `array_view` objektu.

### <a name="return-value"></a>Návratová hodnota

[Array_view](array-view-class.md) , který je vytvořen.

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
