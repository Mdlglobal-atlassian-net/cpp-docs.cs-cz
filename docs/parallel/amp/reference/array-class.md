---
title: Array – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0a7d063d5e57d77735a33eac8ec944d41032fea
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694703"
---
# <a name="array-class"></a>array – třída
Představuje kontejner dat používá k přesunu dat do akcelerátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename value_type, int _Rank>  
friend class array;  
```  
  
#### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementu data.  
  
 `_Rank`  
 Pořadí pole.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[pole – konstruktor](#ctor)|Inicializuje novou instanci třídy `array` třídy.|  
|[~ array – destruktor](#dtor)|Zničí `array` objektu.|  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[copy_to](#copy_to)|Zkopíruje obsah pole do jiného pole.|  
|[data](#data)|Vrací ukazatel na nezpracovaná data tohoto pole.|  
|[get_accelerator_view](#get_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) objekt, který reprezentuje umístění, kde je přidělen pole. Tato vlastnost je přístupná jenom na procesoru.|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který se předá jako parametr po pracovní konstruktor pro vytvoření instance `array` objektu.|  
|[get_cpu_access_type](#get_cpu_access_type)|Vrátí [access_type](concurrency-namespace-enums-amp.md#access_type) pole. Tato metoda je přístupná jenom na procesoru.|  
|[get_extent](#get_extent)|Vrátí [rozsah](extent-class.md) objekt pole.|  
|[reinterpret_as](#reinterpret_as)|Vrací jednorozměrné pole, která obsahuje všechny elementy ve `array` objektu.|  
|[section](#section)|Vrátí dílčí části `array` objekt, který je na zadaný zdrojový a volitelně, který má zadaný rozsah.|  
|[view_as](#view_as)|Vrátí [array_view](array-view-class.md) objekt, který je vytvořený z `array` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor std::vector&lt;value_type&gt;](#operator_vec)|Používá `copy(*this, vector)` implicitně převést pole std::[vektoru](../../../standard-library/vector-class.md) objektu.|  
|[Operator() –](#operator_call)|Vrátí element hodnotu, která je zadanou parametry.|  
|[[] – operátor](#operator_at)|Vrátí element, který je v zadaném indexu.|  
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `array` objekt s touto.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[pořadí konstanta](#rank)|Ukládá pořadí pole.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[accelerator_view](#accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) objekt, který reprezentuje umístění, kde je přidělen pole. Tato vlastnost je přístupná jenom na procesoru.|  
|[associated_accelerator_view](#associated_accelerator_view)|Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který se předá jako parametr po pracovní konstruktor pro vytvoření instance `array` objektu.|  
|[cpu_access_type](#cpu_access_type)|Získá [access_type](concurrency-namespace-enums-amp.md#access_type) představující jak procesoru mají přístup k úložišti pole.|  
|[rozsah](#extent)|Získá v rozsahu, který definuje tvar pole.|  
  
## <a name="remarks"></a>Poznámky  
 Typ `array<T,N>` představuje hustých a běžné (není vícenásobná) *N*-jednorozměrné pole, která se nachází v konkrétní umístění, jako je akcelerátor nebo procesoru. Datový typ elementů v poli je `T`, která musí být typu, který je kompatibilní s akcelerátoru cíl. I když pořadí, `N`, (z tohoto pole je určena staticky a je součástí typu, v rozsahu pole je dáno modulu runtime a je vyjádřit pomocí třídy `extent<N>`.  
  
 Pole může mít libovolný počet dimenzí, i když některé funkce se specializuje na `array` objekty s rank jeden, dva a tři. Pokud nezadáte argument dimenze, výchozí hodnota je 1.  
  
 Pole data rozložená souvisle v paměti. Elementy, které se liší podle jednoho v nejméně významný dimenzi sousedí v paměti.  
  
 Pole jsou logicky považuje za typy hodnot, protože po zkopírování pole ke druhému je prováděna hloubkové kopie. Dvěma poli nikdy bodu ke stejným datům.  
  
 `array<T,N>` Typ se používá v několika scénářích:  
  
-   Jako kontejner dat, který lze použít v výpočtů na akcelerátoru.  
  
-   Jako datový kontejner pro uložení paměť na hostiteli procesoru (které je možné zkopírovat do a z dalších polí).  
  
-   Jako pracovní objekt tak, aby fungoval jako rychlou prostředník v zařízení hostitele kopie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `array`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ pole 

 Zničí `array` objektu.  
  
```  
~array() restrict(cpu);
```  
  
##  <a name="accelerator_view"></a> accelerator_view 

 Získá [accelerator_view](accelerator-view-class.md) objekt, který reprezentuje umístění, kde je přidělen pole. Tato vlastnost je přístupná jenom na procesoru.  
  
```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;  
```  
  
##  <a name="ctor"></a> Pole 

 Inicializuje novou instanci třídy [array – třída](array-class.md). Neexistuje žádný výchozí konstruktor `array<T,N>`. Všechny konstruktory se spouštějí na pouze procesoru. Se nedá spustit na Direct3D – cíl.  
  
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
 `_Associated_Av`  
 Accelerator_view, který určuje upřednostňovaný cílové umístění pole.  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md) objekt, který určuje umístění pole.  
  
 `_Cpu_access_type`  
 Požadovanou [access_type](concurrency-namespace-enums-amp.md#access_type) pro toto pole na procesor. Tento parametr má výchozí hodnotu `access_type_auto` ponechat procesoru `access_type` rozhodnutí modulu runtime. Skutečné využití procesoru `access_type` pro pole lze dotazovat pomocí `get_cpu_access_type` metoda.  
  
 `_Extent`  
 Rozsah v Každá dimenze pole.  
  
 `_E0`  
 Nejdůležitější komponenta rozsahu, v této části.  
  
 `_E1`  
 Další na většinu významné součást v rozsahu tohoto oddílu.  
  
 `_E2`  
 Nejméně významný součást v rozsahu tohoto oddílu.  
  
 `_InputIterator`  
 Typ vstupu interator.  
  
 `_Src`  
 Chcete-li objekt pro kopírování.  
  
 `_Src_first`  
 Začátek iterator do kontejneru zdroje.  
  
 `_Src_last`  
 Koncová iterator do kontejneru zdroje.  
  
 `_Other`  
 Další zdroje dat.  
  
 `_Rank`  
 Pořadí v části.  
  
 `value_type`  
 Datový typ elementů, které jste zkopírovali.  
  
##  <a name="associated_accelerator_view"></a> associated_accelerator_view – 

 Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který se předá jako parametr po pracovní konstruktor pro vytvoření instance `array` objektu.  
  
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
 `_Dest`  
 [Array_view](array-view-class.md) objekt, který chcete zkopírovat do.  
  
##  <a name="cpu_access_type"></a> cpu_access_type 

 Získá access_type procesoru povoleny pro toto pole.  
  
```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;  
```  
  
##  <a name="data"></a> data 

 Vrací ukazatel na nezpracovaná data tohoto `array`.  
  
```  
value_type* data() restrict(amp, cpu);
  
const value_type* data() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nezpracovaná data tohoto pole.  
  
##  <a name="extent"></a> rozsah 

 Získá [rozsah](extent-class.md) objekt, který definuje tvar `array`.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_accelerator_view"></a> get_accelerator_view – 

 Vrátí [accelerator_view](accelerator-view-class.md) objekt, který reprezentuje umístění kde `array` objektu je přidělen. Tato vlastnost je přístupná jenom na procesoru.  
  
```  
Concurrency::accelerator_view get_accelerator_view() const;  
```    
  
### <a name="return-value"></a>Návratová hodnota  
 `accelerator_view` Objekt, který reprezentuje umístění kde `array` objektu je přidělen.  
  
##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view – 

 Získá druhý [accelerator_view](accelerator-view-class.md) objekt, který se předá jako parametr po pracovní konstruktor pro vytvoření instance `array` objektu.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Druhý [accelerator_view](accelerator-view-class.md) pracovní konstruktoru byl předán objekt.  
  
##  <a name="get_cpu_access_type"></a> get_cpu_access_type 

 Vrátí access_type procesoru, který je povolen pro toto pole.  
  
```  
access_type get_cpu_access_type() const restrict(cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="get_extent"></a> get_extent – 

 Vrátí [rozsah](extent-class.md) objekt `array`.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `extent` Objekt `array`.  
  
##  <a name="operator_vec"></a> operátor std::vector&lt;value_type&gt; 

 Používá `copy(*this, vector)` pole implicitně převést na objekt std::vector.  
  
```  
operator std::vector<value_type>() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `value_type`  
 Datový typ elementů Vektoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt typu `vector<T>` obsahující kopii dat, která se nachází v poli.  
  
##  <a name="operator_call"></a> Operator() – 

 Vrátí element hodnotu, která je zadanou parametry.  
  
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
 `_Index`  
 Umístění elementu.  
  
 `_I0`  
 Nejdůležitější komponenta původ v této části.  
  
 `_I1`  
 Další na většinu významné součást původ v této části.  
  
 `_I2`  
 Nejméně významný součást původ v této části.  
  
 `_I`  
 Umístění elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu zadanou parametry.  
  
##  <a name="operator_at"></a> [] – operátor 

 Vrátí element, který je v zadaném indexu.  
  
```  
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);  
  
const value_type& operator[]  
    (const index<_Rank>& _Index) const restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);
  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```  
    
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index.  
  
 `_I`  
 Index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element, který je v zadaném indexu.  
  
##  <a name="operator_eq"></a> operátor = 

 Zkopíruje obsah zadaného `array` objektu.  
  
```  
array& operator= (const array& _Other) restrict(cpu);  
   
array& operator= (array&& _Other) restrict(cpu);  
 
array& operator= (  
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `array` Objekt, který chcete zkopírovat z.  
  
 `_Src`  
 `array` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `array` objektu.  
  
##  <a name="rank"></a> Pořadí 

 Ukládá pořadí `array`.  
  
```  
static const int rank = _Rank;  
```  
## <a name="reinterpret_as"></a> reinterpret_as – 

Reinterprets pole prostřednictvím jednorozměrné array_view, který volitelně může mít typ jinou hodnotu než zdrojové pole.

### <a name="syntax"></a>Syntaxe
``` 
template <typename _Value_type2>  
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);  
  
template <typename _Value_type2>  
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);  
``` 
  
### <a name="parameters"></a>Parametry  
`_Value_type2` Datový typ vrácená data.

### <a name="return-value"></a>Návratová hodnota
Array_view nebo const array_view objektu, která je založena na poli s typem elementu reinterpreted z T ElementType a pořadí z N snížen na 1.

### <a name="remarks"></a>Poznámky
Někdy je vhodnější zobrazit vícerozměrné, pokud je lineární jednorozměrné pole, které by mohly mít s typem jinou hodnotu než zdrojové pole. Tuto metodu můžete použít k dosažení tohoto cíle.
**Upozornění:** nový výklad pole objekt pomocí jiné hodnoty typu je potenciálně nebezpečné operace. Doporučujeme pečlivě používat tuto funkci. 

Následující kód představuje příklad.

```cpp  
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...; 
array_view<float,1> v = a.reinterpret_as<float>(); 

assert(v.extent == 3*a.extent);
```  
  
##  <a name="section"></a> Část 

 Vrátí dílčí části `array` objekt, který je na zadaný zdrojový a volitelně, který má zadaný rozsah.  
  
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
 `_E0`  
 Nejdůležitější komponenta rozsahu, v této části.  
  
 `_E1`  
 Další na většinu významné součást v rozsahu tohoto oddílu.  
  
 `_E2`  
 Nejméně významný součást v rozsahu tohoto oddílu.  
  
 `_Ext`  
 [Rozsah](extent-class.md) objekt, který určuje rozsah oddílu. Počátek je 0.  
  
 `_Idx`  
 [Index](index-class.md) objekt, který určuje umístění počátku. Dílčí části je zbytek v rozsahu.  
  
 `_I0`  
 Nejdůležitější komponenta původ v této části.  
  
 `_I1`  
 Další na většinu významné součást původ v této části.  
  
 `_I2`  
 Nejméně významný součást původ v této části.  
  
 `_Rank`  
 Pořadí v části.  
  
 `_Section_extent`  
 [Rozsah](extent-class.md) objekt, který určuje rozsah oddílu.  
  
 `_Section_origin`  
 [Index](index-class.md) objekt, který určuje umístění počátku.  
  
 `value_type`  
 Datový typ elementů, které jste zkopírovali.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí dílčí části `array` objekt, který je na zadaný zdrojový a volitelně, který má zadaný rozsah. Když pouze `index` je zadaný objekt, část obsahuje všechny elementy ve přidružené mřížky, které mají indexy, které jsou větší než indexy elementů v `index` objektu.  
  
##  <a name="view_as"></a> view_as – 

 Toto pole jako reinterprets [array_view](array-view-class.md) z jiné pořadí.  
  
```  
template <int _New_rank>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

 
template <int _New_rank>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_New_rank`  
 Pořadí `extent` objekt předaný jako parametr.  
  
 `_View_extent`  
 V rozsahu, který se používá k vytvoření nové [array_view](array-view-class.md) objektu.  
  
 `value_type`  
 Datový typ elementů v obou původní `array` objekt a vrácený `array_view` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 [Array_view](array-view-class.md) objekt, který je vytvořený.  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
