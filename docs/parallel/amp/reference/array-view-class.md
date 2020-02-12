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
ms.openlocfilehash: 2aef75eedcde2a2064fe12815d9afd21fee2c293
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127134"
---
# <a name="array_view-class"></a>array_view – třída

Představuje N-dimenzionální zobrazení nad daty uchovávanými v jiném kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
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

### <a name="parameters"></a>Parametry

*value_type*<br/>
Datový typ prvků v objektu `array_view`.

*_Rank*<br/>
Pořadí objektu `array_view`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[array_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `array_view`. Pro `array<T,N>`není k dispozici žádný výchozí konstruktor. Všechny konstruktory jsou omezené tak, aby se spouštěly jenom na procesoru, a nejde je spustit na cíli Direct3D.|
|[~ array_view destruktor](#ctor)|Odstraní objekt `array_view`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[copy_to](#copy_to)|Zkopíruje obsah objektu `array_view` do zadaného cíle voláním `copy(*this, dest)`.|
|[údajů](#data)|Vrátí ukazatel na nezpracovaná data `array_view`.|
|[discard_data](#discard_data)|Zahodí aktuální data, která jsou základem tohoto zobrazení.|
|[get_extent](#get_extent)|Vrátí objekt rozsahu objektu array_view.|
|[get_ref](#get_ref)|Vrátí odkaz na indexovaný element.|
|[get_source_accelerator_view](#get_source_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) , kde se nachází zdroj dat `array_view`.|
|[téhle](#refresh)|Upozorní objekt `array_view`, že jeho vázaná paměť byla upravena mimo rozhraní `array_view`. Volání této metody vykreslí všechny zastaralé informace v mezipaměti.|
|[reinterpret_as](#reinterpret_as)|Vrátí jednorozměrné pole, které obsahuje všechny prvky v objektu `array_view`.|
|[section](#section)|Vrátí dílčí část objektu `array_view`, která se nachází na zadaném umístění, a volitelně, která má zadaný rozsah.|
|[synchronize](#synchronize)|Synchronizuje všechny změny provedené v objektu `array_view` zpátky do zdrojových dat.|
|[synchronize_async](#synchronize_async)|Asynchronně synchronizuje všechny změny provedené v objektu `array_view` zpět do zdrojových dat.|
|[synchronize_to](#synchronize_to)|Synchronizuje všechny změny provedené v objektu `array_view` do zadaného [accelerator_view](accelerator-view-class.md).|
|[synchronize_to_async](#synchronize_to_async)|Asynchronně synchronizuje všechny změny provedené v objektu `array_view` do zadaného [accelerator_view](accelerator-view-class.md).|
|[view_as](#view_as)|Vytvoří objekt `array_view` jiného pořadí pomocí dat tohoto objektu `array_view`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator () – operátor](#operator_call)|Vrátí hodnotu prvku, který je určen parametrem nebo parametry.|
|[operátor\[\]](#operator_at)|Vrátí prvek, který je určen parametry.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `array_view` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta Rank](#rank)|Ukládá pořadí objektu `array_view`.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[stavební](#extent)|Získá objekt `extent`, který definuje tvar objektu `array_view`.|
|[source_accelerator_view](#source_accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) , kde se nachází zdroj dat `array_view`.|
|[value_type](#value_type)|Typ hodnoty `array_view` a vázaného pole.|

## <a name="remarks"></a>Poznámky

Třída `array_view` představuje zobrazení dat, která jsou obsažena v objektu [Array](array-class.md) nebo v dílčí části objektu `array`.

K objektu `array_view`, kde jsou umístěna zdrojová data (místně) nebo v jiném akcelerátoru nebo doméně s kosouvislostí (vzdáleně), můžete přistupovat. Při vzdáleném přístupu k objektu se zobrazení zkopírují a ukládají do mezipaměti podle potřeby. S výjimkou účinků automatického ukládání do mezipaměti má `array_view` objektů profil výkonu podobný tomuto: `array` objektů. Při přístupu k datům prostřednictvím zobrazení dojde k menšímu snížení výkonu.

Existují tři scénáře použití vzdáleného používání:

- Zobrazení ukazatele systémové paměti je předáno prostřednictvím [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) volání akcelerátoru a k němu přistupovalo v akcelerátoru.

- Zobrazení pole umístěného v akcelerátoru je předáno prostřednictvím `parallel_for_each` volání jiného akcelerátoru a je tam k němu přistupované.

- Zobrazení pole umístěného v akcelerátoru je dostupné na CPU.

V některém z těchto scénářů se odkazovaná zobrazení zkopírují do vzdáleného umístění a při změně voláním objektu `array_view` se zkopírují zpátky do místního umístění. Modul runtime může optimalizovat proces kopírování změn zpět, může kopírovat pouze změněné prvky nebo může zkopírovat také nezměněné části. U překrývajících se `array_view` objektů na jednom zdroji dat není zaručeno zachování referenční integrity ve vzdáleném umístění.

Je nutné synchronizovat jakýkoli vícevláknový přístup ke stejnému zdroji dat.

Modul runtime provádí následující záruky týkající se ukládání dat do mezipaměti v `array_view`ch objektech:

- Všechny dobře synchronizované přístupy k objektu `array` a objektu `array_view` v pořadí programu, které se řídí sériovým průběhem, se zobrazí před vztahem.

- Všechny dobře synchronizované přístupy k překrývání `array_view` objektů na jednom akcelerátoru u jednoho objektu `array` jsou aliasem prostřednictvím objektu `array`. Vyvolávat celkový součet výskytů, než je vztah, který dodržuje pořadí programu. Neexistuje žádné ukládání do mezipaměti. Pokud se `array_view` objekty spouštějí v různých akcelerátorech, pořadí přístupu není definováno a vytvoří se konflikt časování.

Když vytvoříte objekt `array_view` pomocí ukazatele v systémové paměti, je nutné změnit objekt zobrazení `array_view` pouze prostřednictvím ukazatele `array_view`. Alternativně je nutné volat `refresh()` na jednom z `array_view` objektů, které jsou připojeny k systémovému ukazateli, pokud je základní nativní paměť změněna přímo místo objektu `array_view`.

Buď akce upozorní objekt `array_view`, že se změnila základní nativní paměť a že všechny kopie, které jsou umístěny v akcelerátoru, jsou zastaralé. Pokud budete postupovat podle těchto pokynů, jsou zobrazení založená na ukazateli shodná s hodnotami uvedenými pro zobrazení polí paralelních dat.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="dtor"></a>~ array_view

Odstraní objekt `array_view`.

```cpp
~array_view()restrict(amp,cpu);
```

## <a name="ctor"></a>array_view

Inicializuje novou instanci třídy `array_view`.

```cpp
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
Typ prvku pole ve stylu jazyka C, ze kterého jsou dodána data.

*_Container*<br/>
Argument šablony, který musí určovat lineární kontejner, který podporuje členy `data()` a `size()`.

*_E0*<br/>
Nejvýznamnější součást rozsahu této části.

*_E1*<br/>
Další nejvýznamnější součást rozsahu této části...

*_E2*<br/>
Nejméně významná komponenta rozsahu tohoto oddílu.

*_Extent*<br/>
Rozsah v každé dimenzi tohoto `array_view`.

*_Other*<br/>
Objekt typu `array_view<T,N>`, ze kterého se má inicializovat nový `array_view`

*_Size*<br/>
Velikost pole ve stylu jazyka C, ze kterého jsou data dodána.

*_Src*<br/>
Ukazatel na zdrojová data, která budou zkopírována do nového pole.

## <a name="copy_to"></a>copy_to

Zkopíruje obsah objektu `array_view` do zadaného cílového objektu voláním `copy(*this, dest)`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Objekt, do kterého se má kopírovat.

## <a name="data"></a>údajů

Vrátí ukazatel na nezpracovaná data `array_view`.

```cpp
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná data `array_view`.

## <a name="discard_data"></a>discard_data

Zahodí aktuální data, která jsou základem tohoto zobrazení. Toto je pomocný parametr pro optimalizaci za běhu, který se používá k tomu, aby nedocházelo k kopírování aktuálního obsahu zobrazení do cílového `accelerator_view`, na kterém je k němu přistupované, a jeho použití se doporučuje, pokud není potřeba existující obsah. Tato metoda je při použití v kontextu restrict (amp) neop.

```cpp
void discard_data() const restrict(cpu);
```

## <a name="extent"></a>stavební

Získá objekt `extent`, který definuje tvar objektu `array_view`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_extent"></a>get_extent

Vrátí objekt [rozsahu](extent-class.md) objektu `array_view`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>Návratová hodnota

Objekt `extent` objektu `array_view`

## <a name="get_ref"></a>get_ref

Získat odkaz na element indexovaný pomocí _Index. Na rozdíl od ostatních operátorů indexování pro přístup k array_view na procesoru, tato metoda implicitně nesynchronizuje obsah této array_view s PROCESORem. Po přístupu k array_view na vzdáleném umístění nebo provedení operace kopírování zahrnující tento array_view se uživatelé před voláním této metody zodpovídají array_view na CPU. V důsledku tohoto selhání dojde k nedefinovanému chování.

```cpp
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element indexovaný _Index

## <a name="get_source_accelerator_view"></a>get_source_accelerator_view

Vrátí accelerator_view, kde se nachází zdroj dat array_view. Pokud array_view nemá zdroj dat, toto rozhraní API vyvolá runtime_exception

```cpp
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_call"></a>operator () – operátor

Vrátí hodnotu prvku, který je určen parametrem nebo parametry.

```cpp
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
Index v prvním rozměru.

*_I1*<br/>
Index ve druhém rozměru.

*_I2*<br/>
Index třetího rozměru.

*_I*<br/>
Umístění elementu.

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku, který je určen parametrem nebo parametry.

## <a name="operator_at"></a>operator [] – operátor

Vrátí prvek, který je určen parametry.

```cpp
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

Hodnota elementu v indexu nebo `array_view` prochází z nejvýznamnější dimenze.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu `array_view` do tohoto objektu.

```cpp
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `array_view`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `array_view`.

## <a name="rank"></a>pořadí

Ukládá pořadí objektu `array_view`.

```cpp
static const int rank = _Rank;
```

## <a name="refresh"></a>téhle

Upozorní objekt `array_view`, že jeho vázaná paměť byla upravena mimo rozhraní `array_view`. Volání této metody vykreslí všechny zastaralé informace v mezipaměti.

```cpp
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a>reinterpret_as

Opětovně interpretuje array_view pomocí jednorozměrné array_view, který jako možnost může mít jiný typ hodnoty než zdrojový array_view.

### <a name="syntax"></a>Syntaxe

```cpp
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
Datový typ nového objektu `array_view`.

### <a name="return-value"></a>Návratová hodnota

Objekt `array_view` nebo objekt const `array_view`, který je založen na tomto `array_view`, s typem elementu převedeným z `T` na `_Value_type2`a pořadím sníženým z *N* na 1.

### <a name="remarks"></a>Poznámky

Někdy je vhodné zobrazit multidimenzionální pole jako lineární jednorozměrné pole, které může mít jiný typ hodnoty než zdrojové pole. Tuto možnost můžete dosáhnout u `array_view` pomocí této metody.

**Upozornění** Opětovná interpretace objektu array_view pomocí jiného typu hodnoty je potenciálně nebezpečná operace. Tato funkce by se měla používat opatrně.

Tady je příklad:

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>section

Vrátí dílčí část objektu `array_view`, která se nachází na zadaném umístění, a volitelně, která má zadaný rozsah.

```cpp
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

### <a name="return-value"></a>Návratová hodnota

Dílčí část objektu `array_view`, která se nachází na zadaném umístění, a volitelně, která má zadaný rozsah. Je-li zadán pouze objekt `index`, obsahuje dílčí část všechny prvky v přidruženém rozsahu, které mají indexy větší než indexy prvků v objektu `index`.

## <a name="source_accelerator_view"></a>source_accelerator_view

Získá zdroj accelerator_view, ke kterému je přidružen tento array_view.

```cpp
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

## <a name="synchronize"></a>Synchronize

Synchronizuje všechny změny provedené v objektu `array_view` zpátky do zdrojových dat.

```cpp
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Access_type*<br/>
Zamýšlená [access_type](concurrency-namespace-enums-amp.md#access_type) na cílovém [accelerator_view](accelerator-view-class.md). Tento parametr má výchozí hodnotu `access_type_read`.

## <a name="synchronize_async"></a>synchronize_async

Asynchronně synchronizuje všechny změny provedené v objektu `array_view` zpět do zdrojových dat.

```cpp
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Access_type*<br/>
Zamýšlená [access_type](concurrency-namespace-enums-amp.md#access_type) na cílovém [accelerator_view](accelerator-view-class.md). Tento parametr má výchozí hodnotu `access_type_read`.

### <a name="return-value"></a>Návratová hodnota

Budoucí, na které se má čekat na dokončení operace.

## <a name="synchronize_to"></a>synchronize_to

Synchronizuje všechny změny provedené v tomto array_view v zadaném accelerator_view.

```cpp
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Cílová accelerator_view pro synchronizaci.

*_Access_type*<br/>
Požadovaná access_type na cílovém accelerator_view. Tento parametr má výchozí hodnotu access_type_read.

## <a name="synchronize_to_async"></a>synchronize_to_async

Asynchronně synchronizuje všechny změny provedené v tomto array_view zadaného accelerator_view.

```cpp
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Cílová accelerator_view pro synchronizaci.

*_Access_type*<br/>
Požadovaná access_type na cílovém accelerator_view. Tento parametr má výchozí hodnotu access_type_read.

### <a name="return-value"></a>Návratová hodnota

Budoucí, na které se má čekat na dokončení operace.

## <a name="value_type"></a>value_type

Typ hodnoty array_view a vázaného pole.

```cpp
typedef typenamevalue_type value_type;
```

## <a name="view_as"></a>view_as

Přeinterpretuje tento `array_view` jako `array_view` jiného pořadí.

```cpp
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
Pořadí nového objektu `array_view`.

*_View_extent*<br/>
`extent`přetvarování.

*value_type*<br/>
Datový typ prvků v původním objektu [Array](array-class.md) a vrácený objekt `array_view`.

### <a name="return-value"></a>Návratová hodnota

Objekt `array_view`, který je vytvořen.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
