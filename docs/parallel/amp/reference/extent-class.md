---
title: "Extent – třída (C++ AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a8606b01ac5d3676b06c93c373677f2eb85d954
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="extent-class-c-amp"></a>extent – třída (C++ AMP)
Představuje vektor *N* celočíselné hodnoty, které určují hranice *N*-dimenzí prostor, který má počátek 0. Hodnoty v vektor seřazeni z nejvýznamnějších k nejméně významný.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <int _Rank>  
class extent;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí `extent` objektu.  

 ## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Extent – konstruktor](#ctor)|Inicializuje novou instanci třídy `extent` třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Obsahuje](#contains)|Ověřuje, že zadaný `extent` objekt má zadané pořadí.|  
|[Velikost](#size)|Vrátí celkový počet lineární velikost v rozsahu (v jednotkách elementů).|  
|[Dlaždice](#tile)|Vytváří `tiled_extent` zadaný objekt s rozsahy dlaždice poskytují rozměry.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator-](#operator_min)|Vrátí novou `extent` objektu, který je vytvořen odečtením `index` elementy z odpovídající `extent` elementy.|  
|[operator--](#operator_min_min)|Snižuje každý element `extent` objektu.|  
|[operator%=](#operator_mod_eq)|Vypočítá numerického zbytku (zbývající) každý prvek v `extent` objektu při dělení čísla daný element.|  
|[operator*=](#operator_star_eq)|Vynásobí jednotlivé prvky `extent` objekt číslem.|  
|[/ = – operátor](#operator_min_eq)|Vydělí jednotlivé prvky `extent` objekt číslem.|  
|[Extent::Operator\[\]](#operator_at)|Vrátí element, který je v zadaném indexu.|  
|[operator+](#operator_add)|Vrátí novou `extent` objektu, který je vytvořen přidáním odpovídající `index` a `extent` elementy.|  
|[operator++](#operator_add_add)|Zvýší jednotlivé prvky `extent` objektu.|  
|[operator+=](#operator_add_eq)|Přidá zadané číslo na jednotlivé prvky `extent` objektu.|  
|[operator=](#operator_eq)|Zkopíruje obsah jiného `extent` objekt s touto.|  
|[operator-=](#operator_min_eq)|Odečítá od zadané číslo z každý element `extent` objektu.|  

  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[pořadí konstanta](#rank)|Získá pořadí `extent` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `extent`  


## <a name="contains">Obsahuje</a> 

Určuje, zda zadaný [index](index-class.md) hodnota je obsažený v objektu "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 `index` Hodnotu k testování.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zadaný `index` hodnota je obsažena v `extent` objektu; jinak `false`.  
  
##  <a name="ctor"></a> rozsah 

Inicializuje novou instanci třídy "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent() restrict(amp,cpu);    
extent(const extent<_Rank>& _Other) restrict(amp,cpu);    
explicit extent(int _I) restrict(amp,cpu);    
extent(int _I0,  int _I1) restrict(amp,cpu);    
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);    
explicit extent(const int _Array[_Rank])restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Array`  
 Pole `_Rank` celých čísel, která se používá k vytvoření nové `extent` objektu.  
  
 `_I`  
 Délka rozsahu.  
  
 `_I0`  
 Délka nejvýznamnějších dimenze.  
  
 `_I1`  
 Délka další na většinu významné dimenze.  
  
 `_I2`  
 Délka nejméně významný dimenze.  
  
 `_Other`  
 `extent` Objekt, u kterého nové `extent` objektu je založena.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje konstruktor bez parametrů `extent` objekt, který má tři pořadí.  
  
 Pokud pole se používá pro konstrukci `extent` objektu, délka pole musí odpovídat pořadí `extent` objektu.  
  
##  <a name="operator_mod_eq"></a> Operator % = 

Vypočítá numerického zbytku (zbývající) jednotlivých prvků na rozsah při dělení čísla daný element.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Číslo, které má-li zjistit zbytek z.  
  
### <a name="return-value"></a>Návratová hodnota  
 `extent` Objektu.  
  
##  <a name="operator_star_eq"></a> Operator * = 

Vynásobí každý prvek v objektu "rozsah" pomocí zadané číslo.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Číslo, které má násobení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `extent` Objektu.  
  
## <a name="operator_add"></a> operátor + 

Vrátí novou `extent` objektu vytvořeny tak, že přidáte k odpovídající položce `index` a `extent` elementy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 `index` Objekt, který obsahuje prvky, které chcete přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové `extent` objektu.  
  
##  <a name="operator_add_add"></a> Operator ++ 

Zvýší každý prvek objektu "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator++() restrict(amp,cpu);    
extent<_Rank> operator++(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro operátor předpona `extent` objektu (`*this`). Pro operátor příponu novou `extent` objektu.  
  
##  <a name="operator_add_eq"></a> += – operátor 

Přidá zadané číslo na každý element objektu "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Číslo, index nebo rozsah přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledná `extent` objektu.  
  
##  <a name="operator_min"></a> Operator – 

Vytvoří novou `extent` objekt odečtením každý prvek v zadané `index` objekt z odpovídající element v tomto `extent` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 `index` Objekt, který obsahuje prvky, které je odečtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové `extent` objektu.  
  
##  <a name="operator_min_min"></a> --– operátor 

Snižuje každý prvek v objektu "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro operátor předpona `extent` objektu (`*this`). Pro operátor příponu novou `extent` objektu.  
  
##  <a name="operator_div_eq">/ = – operátor</a> 

Každý prvek v objektu "rozsah" vydělí pomocí zadané číslo.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Číslo, které má dělit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `extent` Objektu.  
  
##  <a name="operator_min_eq"></a> -= – operátor 

Odečítá od zadané číslo z každého prvku objektu "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Číslo, které má odečíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledná `extent` objektu.  
  
##  <a name="operator_eq"></a> operátor = 

S touto zkopíruje obsah jiného objektu "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `extent` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `extent` objektu.  
  
##  <a name="operator_at">Extent::Operator</a>\[\] 
Vrátí element, který je v zadaném indexu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int operator[](unsigned int _Index) const restrict(amp,cpu);    
int& operator[](unsigned int _Index) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Celé číslo od 0 do pořadí minus 1.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element, který je v zadaném indexu.  
  
##  <a name="rank_constant"></a> Pořadí 

Ukládá pořadí objekt "rozsah".  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="size">Velikost</a> 

Vrátí celkový počet lineární velikost `extent` objektu (v jednotkách elementů).  
  
### <a name="syntax"></a>Syntaxe  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="tile">Dlaždice</a> 

Vytvoří objekt tiled_extent s dimenzí zadaný dlaždice.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>Parametry
`_Dim0` Nejdůležitější komponenta vedle sebe rozsah.
`_Dim1` Další na většinu významné součást vedle sebe rozsah.
`_Dim2` Nejméně významný součást vedle sebe rozsah.


  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
