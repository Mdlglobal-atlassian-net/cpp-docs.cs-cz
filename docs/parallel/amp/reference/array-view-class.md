---
title: array_view – třída
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: bd13fbef1b335b6a2fde1f16a59ddf11d489cdde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501696"
---
# <a name="arrayview-class"></a>array_view – třída

Představuje N-rozměrné zobrazení nad daty udržovanými v jiném kontejneru.

## <a name="syntax"></a>Syntaxe

```
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Datový typ prvků v `array_view` objektu.

*_Rank*<br/>
Řád objektu `array_view` objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[array_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `array_view` třídy. Neexistuje žádný výchozí konstruktor pro `array<T,N>`. Všechny konstruktory jsou spuštěny pouze na CPU a nelze ho provést na cíli Direct3D.|
|[~ array_view – destruktor](#ctor)|Odstraní `array_view` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[copy_to](#copy_to)|Zkopíruje obsah `array_view` objektu do určeného cíle voláním `copy(*this, dest)`.|
|[data](#data)|Vrací ukazatel na nezpracovaná data `array_view`.|
|[discard_data](#discard_data)|Zahodí aktuální data tohoto zobrazení.|
|[get_extent](#get_extent)|Vrátí objekt extent objektu array_view.|
|[get_ref](#get_ref)|Vrátí odkaz na indexovaný prvek.|
|[get_source_accelerator_view](#get_source_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) kde zdroj dat `array_view` nachází.|
|[Aktualizace](#refresh)|Upozorní `array_view` objekt, který jemu přidružená paměť byla upravena mimo `array_view` rozhraní. Volání tato metoda vykreslí všechny informace uložené v mezipaměti zastaralá.|
|[reinterpret_as](#reinterpret_as)|Vrátí jednorozměrné pole, která obsahuje všechny prvky `array_view` objektu.|
|[section](#section)|Vrátí dílčí část objektu `array_view` nacházející se na zadaném umístění a volitelně, který se zadaným rozsahem.|
|[synchronize](#synchronize)|Synchronizuje všechny změny provedené `array_view` objekt jeho zdrojovými daty.|
|[synchronize_async](#synchronize_async)|Asynchronně synchronizuje všechny změny provedené `array_view` objekt jeho zdrojovými daty.|
|[synchronize_to](#synchronize_to)|Synchronizuje všechny změny provedené `array_view` objekt do zadané [accelerator_view](accelerator-view-class.md).|
|[synchronize_to_async](#synchronize_to_async)|Asynchronně synchronizuje všechny změny provedené `array_view` objekt do zadané [accelerator_view](accelerator-view-class.md).|
|[view_as](#view_as)|Vytvoří `array_view` objektu jiného řádu za použití `array_view` dat tohoto objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator()](#operator_call)|Vrátí hodnotu prvku určeného parametrem nebo parametry.|
|[Operator [].](#operator_at)|Vrátí hodnotu prvku určeného parametry.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `array_view` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RANK – konstanta](#rank)|Udržuje řád objektu `array_view` objektu.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[rozsah](#extent)|Získá `extent` objekt, který definuje tvar `array_view` objektu.|
|[source_accelerator_view](#source_accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) kde zdroj dat `array_view` nachází|
|[value_type](#value_type)|Typ hodnoty `array_view` a vázaného pole.|

## <a name="remarks"></a>Poznámky

`array_view` Třída představuje pohled data, která je součástí [pole](array-class.md) objektu nebo dílčí část objektu `array` objektu.

Můžete přistupovat `array_view` objektu (místně) se nachází zdroj dat nebo na jiném akcelerátoru nebo doméně koherence (vzdáleně). Při přístupu k objektu vzdáleně, jsou zobrazení zkopírovat a uložit do mezipaměti podle potřeby. Kromě účinků automatického ukládání do mezipaměti `array_view` objekty mají podobný profil výkonu `array` objekty. Při přístupu k datům prostřednictvím zobrazení je snížení výkonu.

Existují tři scénáře použití vzdáleného přístupu:

- Zobrazení ukazatele systémové paměti je předáno [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) volání akcelerátoru a zpřístupněno v akcelerátoru.

- Zobrazení pole umístěného v akcelerátoru je předáno `parallel_for_each` volání jiného akcelerátoru a zpřístupněno.

- Zobrazení pole umístěného v akcelerátoru je zpřístupněno na CPU.

V některém z těchto scénářích jsou odkazovaná zobrazení zkopírovaná modulem runtime do vzdáleného umístění a pokud autor volání `array_view` objektu, zkopírovány zpět na místní umístění. Modul runtime může optimalizovat proces kopírování změn zpět, může zkopírovat pouze změněné prvky nebo může být také zkopírovat části beze změny. Překrývající se `array_view` objektů v jednom zdroji dat nemají zaručenu referenční integritu ze vzdáleného umístění.

Je nutné synchronizovat všechny vícevláknové přístupy ke stejnému zdroji dat.

Modul runtime zaručuje následující skutečnosti týkající se ukládání do mezipaměti dat v `array_view` objekty:

- Všechny dobře synchronizované přístupy k `array` objektu a `array_view` sériovým jeho objektu v pořadí programu se stane-před vztah.

- Všechny dobře synchronizované přístupy k překrývajícím `array_view` objekty ve stejném akcelerátoru v rámci jednoho `array` mají zaveden alias přes objekt `array` objektu. Vyvolávají celkový dochází-před vztah, který dodržuje pořadí programu. Neexistuje žádné ukládání do mezipaměti. Pokud `array_view` objekty jsou spuštěny v různých akcelerátorech, není pořadí přístupu definováno, časování.

Při vytváření `array_view` objektu použití ukazatele do systémové paměti, je nutné změnit zobrazení `array_view` pouze prostřednictvím objektu `array_view` ukazatele. Alternativně lze zavolat `refresh()` na jednom z `array_view` objekty, které jsou připojeny k systémovému ukazateli, je-li příslušná nativní paměť změněna přímo namísto prostřednictvím `array_view` objektu.

Obě akce upozorní `array_view` objektu, že se změní příslušné nativní paměti a že všechny kopie umístěné v akcelerátoru jsou již zastaralé. Pokud budete postupovat podle těchto pokynů, jsou stejné jako ty poskytována pro zobrazení polí paralelních dat. zobrazení založená na ukazatel.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~ array_view

Odstraní `array_view` objektu.

```
~array_view()restrict(amp,cpu);
```

##  <a name="ctor"></a> array_view

Inicializuje novou instanci třídy `array_view` třídy.

```
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);

```

### <a name="parameters"></a>Parametry

*_Arr_type*<br/>
Typ elementu pole stylu C, ze které pochází data.

*_Container*<br/>
Argument šablony, který musí specifikovat lineární kontejner podporující `data()` a `size()` členy.

*_E0*<br/>
Nejvýznamnější komponenta rozsahu tohoto oddílu.

*_E1*<br/>
Další na nejvýznamnější komponenta rozsahu tohoto oddílu.

*_E2*<br/>
Nejméně významná komponenta rozsahu tohoto oddílu.

*_Extent*<br/>
Rozsah v každé dimenzi tohoto objektu `array_view`.

*Ji_né*<br/>
Objekt typu `array_view<T,N>` ze kterého je inicializován nový `array_view`.

*_Velikost*<br/>
Velikost pole stylu C, ze které pochází data.

*_Src*<br/>
Ukazatel na zdrojová data, která budou zkopírovány do nového pole.

##  <a name="copy_to"></a> copy_to –

Zkopíruje obsah `array_view` do zadaného cílového objektu voláním `copy(*this, dest)`.

```
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Objekt, který chcete zkopírovat do.

##  <a name="data"></a> Data

Vrací ukazatel na nezpracovaná data `array_view`.

```
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná data objektu `array_view`.

##  <a name="discard_data"></a> discard_data

Zahodí aktuální data tohoto zobrazení. Jedná se optimalizaci nápovědu pro modul runtime používá pro zabránění kopírování aktuálního obsahu zobrazení do cílového `accelerator_view` , který je přístupný na a použití náznaku je doporučeno, pokud není existující obsah zapotřebí. Tato metoda je no-op. při použití v kontextu restrict(amp) operaci

```
void discard_data() const restrict(cpu);
```

##  <a name="extent"></a> rozsah

Získá `extent` objekt, který definuje tvar `array_view` objektu.

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_extent"></a> get_extent –

Vrátí [rozsahu](extent-class.md) objektu `array_view` objektu.

```
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>Návratová hodnota

`extent` Objektu `array_view` objektu

##  <a name="get_ref"></a> get_ref

Získejte odkaz na prvek indexovaný pomocí _Index. Na rozdíl od jiných operátorů indexování pro přístup do zobrazení array_view v procesoru tato metoda není implicitně synchronizována s obsahem array_view procesoru. Po přístupu k objektu array_view ve vzdáleném umístění nebo provedení operace kopie zahrnující tento pohled array_view jsou uživatelé za explicitní synchronizaci objektu array_view s Procesorem před voláním této metody. Pokud tak neučiníte způsobí nedefinované chování.

```
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek indexovaný pomocí _Index

##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view

Vrátí accelerator_view, kde se nachází zdroj dat pro array_view. Pokud array_view nemá zdroj dat, toto rozhraní API vyvolá runtime_exception

```
accelerator_view get_source_accelerator_view() const;

```

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_call"></a> Operator()

Vrátí hodnotu prvku určeného parametrem nebo parametry.

```
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Umístění elementu.

*_I0*<br/>
Index prvního rozměru.

*_I1*<br/>
Index druhého rozměru.

*_I2*<br/>
Index třetího rozměru.

*_I*<br/>
Umístění elementu.

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku určeného parametrem nebo parametry.

##  <a name="operator_at"></a> Operator [].

Vrátí hodnotu prvku určeného parametry.

```
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

*_I*<br/>
Index.

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu v indexu, nebo `array_view` projektovaná v nejvýznamnější dimenzi.

##  <a name="operator_eq"></a> operátor =

Zkopíruje obsah zadaného `array_view` do tohoto objektu.

```
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`array_view` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `array_view` objektu.

##  <a name="rank"></a> pořadí

Udržuje řád objektu `array_view` objektu.

```
static const int rank = _Rank;
```

##  <a name="refresh"></a> Aktualizace

Upozorní `array_view` objekt, který jemu přidružená paměť byla upravena mimo `array_view` rozhraní. Volání tato metoda vykreslí všechny informace uložené v mezipaměti zastaralá.

```
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a> reinterpret_as –

Opětovně interpretuje objekt array_view skrze jednorozměrný prvek array_view, který případně může mít typ jinou hodnotu než zdrojový prvek array_view.

### <a name="syntax"></a>Syntaxe

```
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Value_type2*<br/>
Datový typ nového `array_view` objektu.

### <a name="return-value"></a>Návratová hodnota

`array_view` Nebo objekt konstanty `array_view` objekt, který je na základě toho `array_view`, s typem elementu převést z `T` k `_Value_type2`, a řádem redukovaným z *N* na hodnotu 1.

### <a name="remarks"></a>Poznámky

Někdy je vhodné zobrazit vícerozměrné pole jako lineární jednorozměrné pole, která může mít typ jinou hodnotu než zdrojového pole. Lze toho dosáhnout na `array_view` tímto způsobem.

**Upozornění** opětovná interpretace objektu array_view pomocí jiného typu hodnoty je potenciálně nebezpečná operace. Tato funkce by měla být používána opatrně.

Tady je příklad:

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> Oddíl

Vrátí dílčí část objektu `array_view` nacházející se na zadaném umístění a volitelně, který se zadaným rozsahem.

```
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
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

### <a name="return-value"></a>Návratová hodnota

Dílčí část objektu `array_view` nacházející se na zadaném umístění a volitelně, který se zadaným rozsahem. Když pouze `index` objektu je zadán, obsahuje dílčí část všechny prvky přidruženého rozsahu, které mají indexy větší než indexy prvků v `index` objektu.

##  <a name="source_accelerator_view"></a> source_accelerator_view

Získá zdroj accelerator_view, který je přidružený tento pohled array_view.

```
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

##  <a name="synchronize"></a> Synchronizovat

Synchronizuje všechny změny provedené `array_view` objekt jeho zdrojovými daty.

```
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Access_type*<br/>
Určené [access_type](concurrency-namespace-enums-amp.md#access_type) na cíli [accelerator_view](accelerator-view-class.md). Tento parametr má výchozí hodnotu `access_type_read`.

##  <a name="synchronize_async"></a> synchronize_async

Asynchronně synchronizuje všechny změny provedené `array_view` objekt jeho zdrojovými daty.

```
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Access_type*<br/>
Určené [access_type](concurrency-namespace-enums-amp.md#access_type) na cíli [accelerator_view](accelerator-view-class.md). Tento parametr má výchozí hodnotu `access_type_read`.

### <a name="return-value"></a>Návratová hodnota

Objekt future, na který se má čekat na dokončení operace.

##  <a name="synchronize_to"></a> synchronize_to

Synchronizuje všechny změny provedené pro tento pohled array_view pro zadaný accelerator_view.

```
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Cílové zobrazení accelerator_view pro synchronizaci.

*_Access_type*<br/>
Požadovaný access_type v cílovém accelerator_view. Tento parametr má výchozí hodnotu access_type_read.

##  <a name="synchronize_to_async"></a> synchronize_to_async

Asynchronně synchronizuje všechny změny provedené pro tento pohled array_view pro zadaný accelerator_view.

```
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Cílové zobrazení accelerator_view pro synchronizaci.

*_Access_type*<br/>
Požadovaný access_type v cílovém accelerator_view. Tento parametr má výchozí hodnotu access_type_read.

### <a name="return-value"></a>Návratová hodnota

Objekt future, na který se má čekat na dokončení operace.

##  <a name="value_type"></a> value_type

Typ hodnoty array_view a vázaného pole.

```
typedef typenamevalue_type value_type;
```

##  <a name="view_as"></a> view_as –

Opětovně interpretuje toto pole `array_view` jako `array_view` jiné hodnosti.

```
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_New_rank*<br/>
Řád nového `array_view` objektu.

*_View_extent*<br/>
Měnící tvar `extent`.

*value_type*<br/>
Datový typ prvků v původním [pole](array-class.md) objektu a ve vráceném `array_view` objektu.

### <a name="return-value"></a>Návratová hodnota

`array_view` , Který je vytvořen.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
