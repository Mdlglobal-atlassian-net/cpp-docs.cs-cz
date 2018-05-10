---
title: Texture – třída | Microsoft Docs
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
ms.openlocfilehash: b16e449f3def7b4b86932e9806fa78d422466978
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="texture-class"></a>texture – třída
Texturou je typu dat na agregační `accelerator_view` v doméně rozsah. Jedná se o kolekci proměnných, jednu pro každý prvek v doméně rozsah. Každá proměnná obsahuje hodnotu odpovídající primitivní typ C++ ( `unsigned int`, `int`, `float`, `double`), skalárního typu ( `norm`, nebo `unorm`), nebo zadejte krátký vektoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename value_type,  int _Rank>  
class texture;  
```  
  
#### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementů v textury.  
  
 `_Rank`  
 Pořadí textury.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`scalar_type`|Skalární typy.|  
|`value_type`|Typy hodnot.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Texture – konstruktor](#ctor)|Inicializuje novou instanci třídy `texture` třídy.|  
|[~ texture – destruktor](#ctor)|Zničí `texture` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[copy_to](#copy_to)|Kopie `texture` objektu do cílového umístění, pomocí tohoto postupu hloubkové kopie.|  
|[data](#data)|Nezpracovaná data tohoto texture vrátí ukazatel procesoru.|  
|[get](#get)|Vrátí hodnotu elementu v zadaném indexu.|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Vrátí [accelerator_view](accelerator-view-class.md) tedy upřednostňovaný cíl pro tuto texture zkopírovány do.|  
|[get_depth_pitch](#get_depth_pitch)|Vrátí počet bajtů mezi každý řez hloubka v 3D pracovní texture na procesoru.|  
|[get_row_pitch](#get_row_pitch)|Vrátí počet bajtů mezi každý řádek v 2D nebo 3D pracovní texture na procesoru.|  
|[set](#set)|Nastaví hodnotu elementu v zadaném indexu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Operator() –](#operator_call)|Vrátí element hodnotu, která je zadanou parametry.|  
|[[] – operátor](#operator_at)|Vrátí element, který je v zadaném indexu.|  
|[operátor =](#operator_eq)|Zkopíruje zadaný [texture](texture-class.md) k tomuto objektu.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[pořadí konstanta](#rank)|Získá pořadí `texture` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[associated_accelerator_view](#associated_accelerator_view)|Získá [accelerator_view](accelerator-view-class.md) tedy upřednostňovaný cíl pro tuto texture zkopírovány do.|  
|[depth_pitch](#depth_pitch)|Získá počet bajtů mezi každý řez hloubka v 3D pracovní texture na procesoru.|  
|[row_pitch](#row_pitch)|Získá počet bajtů mezi každý řádek v 2D nebo 3D pracovní texture na procesoru.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_graphics.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="dtor"></a> ~ texture 

 Zničí `texture` objektu.  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="associated_accelerator_view"></a> associated_accelerator_view – 

 Získá [accelerator_view](accelerator-view-class.md) tedy upřednostňovaný cíl pro tuto texture zkopírovány do.  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a> copy_to – 

 Kopie `texture` objektu do cílového umístění, pomocí tohoto postupu hloubkové kopie.  
  
```  
void copy_to(texture& _Dest) const; 
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Objekt, který se má zkopírovat do.  
  
 `_Rank`  
 Pořadí textury.  
  
 `value_type`  
 Typ elementů v textury.  
  
##  <a name="data"></a> data 

 Nezpracovaná data tohoto texture vrátí ukazatel procesoru.  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nezpracovaná data textury.  
  
##  <a name="depth_pitch"></a> depth_pitch 

 Získá počet bajtů mezi každý řez hloubka v 3D pracovní texture na procesoru.  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="get"></a> GET 

 Vrátí hodnotu elementu v zadaném indexu.  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu v zadaném indexu.  
  
##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view – 

 Vrátí accelerator_view, který je upřednostňovaný cíl pro tuto texture zkopírovány do.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [Accelerator_view](accelerator-view-class.md) tedy upřednostňovaný cíl pro tuto texture zkopírovány do.  
  
##  <a name="get_depth_pitch"></a> get_depth_pitch 

 Vrátí počet bajtů mezi každý řez hloubka v 3D pracovní texture na procesoru.  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů mezi každý řez hloubka v 3D pracovní texture na procesoru.  
  
##  <a name="get_row_pitch"></a> get_row_pitch 

 Vrátí počet bajtů mezi každý řádek v prostorovém 2 pracovní texture nebo mezi každý řádek hloubka řez ve 3 dimenzí pracovní texture.  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů mezi každý řádek v prostorovém 2 pracovní texture nebo mezi každý řádek hloubka řez ve 3 dimenzí pracovní texture.  
  
##  <a name="operator_call"></a> Operator() – 

 Vrátí element hodnotu, která je zadanou parametry.  
  
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
 `_Index`  
 Index.  
  
 `_I0`  
 Většina významné součást index.  
  
 `_I1`  
 Další na většinu významné součást index.  
  
 `_I2`  
 Nejméně významným součást index.  
  
 `_Rank`  
 Pořadí index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu, která je zadána parametry.  
  
##  <a name="operator_at"></a> [] – operátor 

 Vrátí element, který je v zadaném indexu.  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index.  
  
 `_I0`  
 Index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element, který je v zadaném indexu.  
  
##  <a name="operator_eq"></a> operátor = 

 Zkopíruje zadaný [texture](texture-class.md) k tomuto objektu.  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `texture` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `texture` objektu.  
  
##  <a name="rank"></a> Pořadí 

 Získá pořadí `texture` objektu.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="row_pitch"></a> row_pitch 

 Získá počet bajtů mezi každý řádek v 2D nebo 3D pracovní texture na procesoru.  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="set"></a> nastavení 

 Nastaví hodnotu elementu v zadaném indexu.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu.  
  
 `_Rank`  
 Pořadí index.  
  
 `value`  
 Nová hodnota elementu.  
  
##  <a name="ctor"></a> Texture 

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
 `_Acc_view`  
 [Accelerator_view](accelerator-view-class.md) , určuje umístění textury.  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md) , určuje umístění textury.  
  
 `_Associated_av`  
 Accelerator_view, která určuje upřednostňovaný cíl pro kopie do nebo z této texture.  
  
 `_Bits_per_scalar_element`  
 Počet bitů na každý skalární prvek v základní typ skalární textury. Podporované hodnoty jsou obecně, 8, 16, 32 až 64. Pokud zadáte hodnotu 0, je stejná jako základní scalar_type počet bitů. 64 je platná pouze pro textury založené na dvojitou hodnotu.  
  
 `_Ext`  
 Rozsah v Každá dimenze textury.  
  
 `_E0`  
 Nejdůležitější komponenta textury.  
  
 `_E1`  
 Další na většinu významné součást textury.  
  
 `_E2`  
 Nejméně významný součást rozsah textury.  
  
 `_Input_iterator`  
 Typ vstupu interator.  
  
 `_Mipmap_levels`  
 Počet úrovní mipmap v základní texture. Pokud zadáte hodnotu 0, textury bude mít plný rozsah mipmap úrovně dolů na nejmenší možná velikost pro zadaný rozsah.  
  
 `_Rank`  
 Pořadí v rozsahu.  
  
 `_Source`  
 Ukazatel na vyrovnávací paměť hostitele.  
  
 `_Src`  
 Chcete-li texture ke kopírování.  
  
 `_Src_byte_size`  
 Počet bajtů ve vyrovnávací paměti zdroje.  
  
 `_Src_first`  
 Začátek iterator do kontejneru zdroje.  
  
 `_Src_last`  
 Koncová iterator do kontejneru zdroje.  
  
 `_Other`  
 Další zdroje dat.  
  
 `_Rank`  
 Pořadí v části.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
