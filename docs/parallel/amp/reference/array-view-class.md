---
title: "array_view – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54202618f578b9a5e6fd602924a37d7ea0825353
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="arrayview-class"></a>array_view – třída
Reprezentuje N-trojrozměrné zobrazení přes data ukládaná v jiném kontejneru.  
  
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
 `value_type`  
 Datový typ elementů v `array_view` objektu.  
  
 `_Rank`  
 Pořadí `array_view` objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[array_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `array_view` třídy. Neexistuje žádný výchozí konstruktor `array<T,N>`. Všechny konstruktory jsou omezeny na procesoru pouze spouštět a se nedá spustit na Direct3D – cíl.|  
|[~array_view Destructor](#ctor)|Zničí `array_view` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[copy_to](#copy_to)|Zkopíruje obsah `array_view` objektu do určeného cíle voláním `copy(*this, dest)`.|  
|[data](#data)|Vrací ukazatel na nezpracovaná data tohoto `array_view`.|  
|[discard_data](#discard_data)|Zruší aktuální data základní toto zobrazení.|  
|[get_extent](#get_extent)|Vrací objekt rozsah array_view objektu.|  
|[get_ref](#get_ref)|Vrátí odkaz na element indexovaný.|  
|[get_source_accelerator_view](#get_source_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) kde zdroj dat `array_view` nachází.|  
|[refresh](#refresh)|Upozorní `array_view` objekt, který jeho vázané paměť byla změněna mimo `array_view` rozhraní. Volání tato metoda vykreslí všechny informace uložené v mezipaměti zastaralé.|  
|[reinterpret_as](#reinterpret_as)|Vrací jednorozměrné pole, která obsahuje všechny elementy ve `array_view` objektu.|  
|[section](#section)|Vrátí dílčí části `array_view` objekt, který je na zadaný zdrojový a volitelně, který má zadaný rozsah.|  
|[synchronize](#synchronize)|Synchronizuje všechny změny provedené `array_view` objektu zpět na jeho zdrojová data.|  
|[synchronize_async](#synchronize_async)|Asynchronně synchronizuje všechny změny provedené `array_view` objektu zpět na jeho zdrojová data.|  
|[synchronize_to](#synchronize_to)|Synchronizuje všechny změny provedené `array_view` objekt, který má zadaný [accelerator_view](accelerator-view-class.md).|  
|[synchronize_to_async](#synchronize_to_async)|Asynchronně synchronizuje všechny změny provedené `array_view` objekt, který má zadaný [accelerator_view](accelerator-view-class.md).|  
|[view_as](#view_as)|Vytvoří `array_view` objekt jiné pořadí pomocí této `array_view` dat objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator()](#operator_call)|Vrátí hodnotu elementu, který je zadán parametr nebo parametry.|  
|[operator[]](#operator_at)|Vrátí element, který je zadanou parametry.|  
|[operator=](#operator_eq)|Zkopíruje obsah zadaného `array_view` objekt s touto.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[pořadí konstanta](#rank)|Ukládá pořadí `array_view` objektu.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[extent](#extent)|Získá `extent` objekt, který definuje tvar `array_view` objektu.|  
|[source_accelerator_view](#source_accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) kde zdroj dat `array_view` nachází|  
|[value_type](#value_type)|Typ hodnoty `array_view` a vázané pole.|  
  
## <a name="remarks"></a>Poznámky  
 `array_view` Třída představuje pohled na data, která je součástí [pole](array-class.md) objekt nebo dílčí části `array` objektu.  
  
 Dostanete `array_view` objektu, kde zdrojová data nachází (místní) nebo na jinou akcelerátoru nebo doméně soudržnost (vzdáleně). Při přístupu k objektu vzdáleně, zobrazení jsou zkopírovány a uložili do mezipaměti podle potřeby. S výjimkou důsledky automatické ukládání do mezipaměti `array_view` objekty mají profil výkonu podobná `array` objekty. Při přístupu k datům prostřednictvím zobrazení je snížení výkonu malé.  
  
 Existují tři scénáře použití vzdáleného přístupu:  
  
-   Zobrazení ukazatele paměti systému byla předána prostřednictvím [parallel_for_each –](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) volání do akcelerátor a získat přístup na akcelerátor.  
  
-   Zobrazení do pole umístěné na akcelerátor předávána prostřednictvím `parallel_for_each` volání do jiného akcelerátoru a přístupu k dispozici.  
  
-   Zobrazení do pole umístěné na akcelerátor přistupuje na procesoru.  
  
 V některém z těchto scénářů odkazovaného zobrazení se zkopírují modulem runtime do vzdáleného umístění a pokud upraveném volání `array_view` objektu, se zkopírují zpět do místního umístění. Modul runtime může optimalizovat proces kopírování zpět změny, může kopírovat pouze změněné prvky nebo může také zkopírujte beze změny části. Překrývající se `array_view` objektů na jeden zdroj dat se nezaručuje, že zachovat referenční integritu ze vzdáleného umístění.  
  
 Je nutné synchronizovat všechny vícevláknové přístup ke stejnému zdroji dat.  
  
 Modul runtime umožňuje tyto záruky ohledně ukládání dat v `array_view` objekty:  
  
-   Všechny dobře synchronizované přístupů k `array` objektu a `array_view` objektu na něm v programu pořadí orientují serial se stane-před vztah.  
  
-   Všechny dobře synchronizované přístupů k překrývání `array_view` objekty na stejné akcelerátoru na jednom `array` objekt jsou alias prostřednictvím `array` objektu. Vyvolávat celkem dojde k – před relace, který dodržuje program pořadí. Není žádný ukládání do mezipaměti. Pokud `array_view` objekty jsou prováděny v různých akcelerátorů, není definován, vytváření časování pořadí přístup.  
  
 Při vytváření `array_view` pomocí ukazatele v paměti systému, musíte změnit zobrazení `array_view` pouze prostřednictvím objektu `array_view` ukazatel. Alternativně musí volat `refresh()` na jednom z `array_view` objekty, které jsou připojené k systému ukazatele, pokud základní nativní paměti mění přímo, namísto prostřednictvím `array_view` objektu.  
  
 Obě tyto akce upozorní `array_view` objektu, že se změní základní nativní paměť a zda jsou všechny kopie, které se nacházejí na akcelerátor zastaralé. Pokud budete postupovat podle těchto pokynů, jsou stejné jako ty poskytované zobrazení dat paralelní pole zobrazení založené na ukazatel.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ array_view 

 Zničí `array_view` objektu.  
  
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
 `_Arr_type`  
 Typ elementu stylu jazyka C pole, ze kterého je zadaná data.  
  
 `_Container`  
 Argument šablony, který musíte zadat lineární kontejner, který podporuje `data()` a `size()` členy.  
  
 `_E0`  
 Nejdůležitější komponenta rozsahu, v této části.  
  
 `_E1`  
 Další na většinu významné součást v rozsahu tohoto oddílu.  
  
 `_E2`  
 Nejméně významný součást v rozsahu tohoto oddílu.  
  
 `_Extent`  
 Rozsah v Každá dimenze tohoto `array_view`.  
  
 `_Other`  
 Objekt typu `array_view<T,N>` ze kterého se inicializovat nové `array_view`.  
  
 `_Size`  
 Velikost stylu jazyka C pole, ze kterého je zadaná data.  
  
 `_Src`  
 Ukazatel na zdroj dat, která se zkopírují do nové pole.  
  
##  <a name="copy_to"></a> copy_to – 

 Zkopíruje obsah `array_view` objekt, který má zadaný cílový objekt voláním `copy(*this, dest)`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Objekt, který se má zkopírovat do.  
  
##  <a name="data"></a> data 

 Vrací ukazatel na nezpracovaná data tohoto `array_view`.  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nezpracovaná data tohoto `array_view`.  
  
##  <a name="discard_data"></a> discard_data 

 Zruší aktuální data základní toto zobrazení. Toto je optimalizačního pomocného parametru pro modul runtime umožňuje vyhnout kopírování aktuální obsah zobrazení na cíl `accelerator_view` který je přístupný v, a jeho použití se doporučuje, pokud není nutné existujícího obsahu. Tato metoda je no-op, pokud se používá v kontextu restrict(amp)  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="extent"></a> rozsah 

 Získá `extent` objekt, který definuje tvar `array_view` objektu.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_extent"></a> get_extent – 

 Vrátí [rozsah](extent-class.md) objekt `array_view` objektu.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `extent` Objekt `array_view` objektu  
  
##  <a name="get_ref"></a> get_ref 

 Získáte odkaz na element indexovat pomocí _Index. Na rozdíl od jiných indexování operátory pro přístup k array_view na procesoru tato metoda nebude synchronizovat implicitně obsah této array_view k procesoru. Po přístup k array_view ve vzdáleném umístění nebo provádění operace kopírování zahrnující tuto array_view uživatelé zodpovídají explicitně synchronizace array_view k procesoru před voláním této metody. Tak neučiníte výsledkem nedefinované chování.  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na element indexovat pomocí _Index  
  
##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view 

 Vrátí accelerator_view, kde se nachází zdroj dat array_view. Pokud array_view nemá zdroj dat, vyvolá toto rozhraní API runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_call"></a> Operator() – 

 Vrátí hodnotu elementu, který je zadán parametr nebo parametry.  
  
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
 `_Index`  
 Umístění elementu.  
  
 `_I0`  
 Index v první dimenzi.  
  
 `_I1`  
 Index v druhé dimenzi.  
  
 `_I2`  
 Index v jiných dimenzi.  
  
 `_I`  
 Umístění elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu, který je zadán parametr nebo parametry.  
  
##  <a name="operator_at"></a> [] – operátor 

 Vrátí element, který je zadanou parametry.  
  
```  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

 
value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index.  
  
 `_I`  
 Index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota element v indexu, nebo `array_view` projekci většinu významné dimenze.  
  
##  <a name="operator_eq"></a> operátor = 

 Zkopíruje obsah zadaného `array_view` k tomuto objektu.  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `array_view` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `array_view` objektu.  
  
##  <a name="rank"></a> Pořadí 

 Ukládá pořadí `array_view` objektu.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="refresh"></a> Aktualizace 

 Upozorní `array_view` objekt, který jeho vázané paměť byla změněna mimo `array_view` rozhraní. Volání tato metoda vykreslí všechny informace uložené v mezipaměti zastaralé.  
  
```  
void refresh() const restrict(cpu);
```  
## <a name="reinterpret_as"></a> reinterpret_as 

Reinterprets array_view prostřednictvím jednorozměrné array_view, který jako možnost může mít typ jinou hodnotu než array_view zdroje.  
  
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
 `_Value_type2`  
 Datový typ nové `array_view` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `array_view` Objekt nebo const `array_view` objekt, který je na základě `array_view`, s typem elementu převést z `T` k `_Value_type2`, a pořadí z *N* na 1.  
  
### <a name="remarks"></a>Poznámky  
 Někdy je vhodnější zobrazit vícerozměrné jako lineární, jednorozměrné pole, která může mít typ jinou hodnotu než zdrojové pole. Toho lze dosáhnout na `array_view` pomocí této metody.  
  
**Upozornění** Reinterpeting array_view objekt pomocí jiné hodnoty typu je potenciálně nebezpečné operace. Tato funkce je třeba použít dát pozor.  
  
 Tady je příklad:  
  
```cpp  
struct RGB { float r; float g; float b; };  
  
array<RGB,3>  a = ...;   
array_view<float,1> v = a.reinterpret_as<float>();   
  
assert(v.extent == 3*a.extent);  
```  
    
##  <a name="section"></a> Část 

 Vrátí dílčí části `array_view` objekt, který je na zadaný zdrojový a volitelně, který má zadaný rozsah.  
  
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
  
### <a name="return-value"></a>Návratová hodnota  
 Dílčí části `array_view` objekt, který je na zadaný zdrojový a volitelně, který má zadaný rozsah. Když pouze `index` je zadaný objekt, část obsahuje všechny elementy ve přidružené rozsah, které mají indexy, které jsou větší než indexy elementů v `index` objektu.  
  
##  <a name="source_accelerator_view"></a> source_accelerator_view 

 Získá accelerator_view – zdroj, který je přidružený tento array_view.  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="synchronize"></a> Synchronizovat 

 Synchronizuje všechny změny provedené `array_view` objektu zpět na jeho zdrojová data.  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Access_type`  
 Požadovanou [access_type](concurrency-namespace-enums-amp.md#access_type) na cílovém [accelerator_view](accelerator-view-class.md). Tento parametr má výchozí hodnotu `access_type_read`.  
  
##  <a name="synchronize_async"></a> synchronize_async 

 Asynchronně synchronizuje všechny změny provedené `array_view` objektu zpět na jeho zdrojová data.  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Access_type`  
 Požadovanou [access_type](concurrency-namespace-enums-amp.md#access_type) na cílovém [accelerator_view](accelerator-view-class.md). Tento parametr má výchozí hodnotu `access_type_read`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Budoucí němž čekat na dokončení operace.  
  
##  <a name="synchronize_to"></a> synchronize_to 

 Synchronizuje všechny změny provedené v této array_view k zadané accelerator_view.  
  
```  
void synchronize_to(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accl_view`  
 Accelerator_view cíl synchronizovat.  
  
 `_Access_type`  
 Požadované access_type na accelerator_view cíl. Tento parametr má výchozí hodnotu access_type_read.  
  
##  <a name="synchronize_to_async"></a> synchronize_to_async 

 Asynchronně synchronizuje všechny změny provedené v této array_view k zadané accelerator_view.  
  
```  
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accl_view`  
 Accelerator_view cíl synchronizovat.  
  
 `_Access_type`  
 Požadované access_type na accelerator_view cíl. Tento parametr má výchozí hodnotu access_type_read.  
  
### <a name="return-value"></a>Návratová hodnota  
 Budoucí němž čekat na dokončení operace.  
  
##  <a name="value_type"></a> value_type 

 Typ hodnoty array_view a vázané pole.  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="view_as"></a> view_as 

 To reinterprets `array_view` jako `array_view` z jiné pořadí.  
  
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
 `_New_rank`  
 Pořadí nové `array_view` objektu.  
  
 `_View_extent`  
 Změna tvaru `extent`.  
  
 `value_type`  
 Datový typ elementů v obou původní [pole](array-class.md) objekt a vrácený `array_view` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `array_view` Objekt, který je vytvořený.  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
