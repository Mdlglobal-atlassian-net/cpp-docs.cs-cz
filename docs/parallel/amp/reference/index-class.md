---
title: index – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs:
- C++
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594ee94bbbfc19bc6fcceb9ae7f0760d9ec877dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="index-class"></a>index – třída
Definuje *N*-dimenzí index pographics-cpp-amp.md.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <int _Rank>  
class index;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí, nebo počet dimenzí.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[index – konstruktor](#ctor)|Inicializuje novou instanci třídy `index` třídy.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[--– operátor](#operator--)|Snižuje každý element `index` objektu.|  
|[Operator(MOD) =](#operator_mod_eq)|Vypočítá numerického zbytku (zbývající) každý prvek v `index` objektu při dělení čísla daný element.|  
|[Operator * =](#operator_star_eq)|Vynásobí jednotlivé prvky `index` objekt číslem.|  
|[/ = – operátor](#operator_div_eq)|Vydělí jednotlivé prvky `index` objekt číslem.|  
|[index::Operator\[\]](#operator_at)|Vrátí element, který je v zadaném indexu.|  
|[Operator ++](#operator_add_add)|Zvýší jednotlivé prvky `index` objektu.|  
|[operator+=](#operator_add_eq)|Přidá zadané číslo na jednotlivé prvky `index` objektu.|  
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `index` objekt s touto.|  
|[-= – operátor](#operator_-_eq)|Odečítá od zadané číslo z každý element `index` objektu.|  

  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[pořadí konstanta](#rank)|Ukládá pořadí `index` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `index`  
  
## <a name="remarks"></a>Poznámky  
 `index` Struktura představuje souřadnic vektor *N* celých čísel, která určuje jedinečný pozici v *N*-dimenzí místa. Hodnoty v vektor seřazeni z nejvýznamnějších k nejméně významný. Můžete načíst hodnoty složek pomocí [operátor =](#operator_eq).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  


## <a name="index_ctor"></a> index – konstruktor
Inicializuje novou instanci třídy index.

```  
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
``` 

### <a name="parameters"></a>Parametry

_Array  
Jednorozměrné pole s rank hodnotami.  
_I  
Umístění indexu v jednorozměrné indexu.  
_I0  
Délka nejvýznamnějších dimenze.  
_I1  
Délka další na většinu významné dimenze.  
_I2  
Délka nejméně významný dimenze.  
_Other  
Objekt index, na kterých je založena na nový objekt index.  

## <a name="operator--"></a>  --– operátor
Snižuje každý prvek objektu indexu.  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>Vrácené hodnoty
Pro operátor předpona objektu indexu (* to). Pro operátor příponu nový objekt v indexu.

## <a name="operator_mod_eq"></a>  Operator(MOD) =   
Vypočítá numerického zbytku (zbývající) každý element v indexu objektu při dělení tohoto prvku zadané číslo.

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>Parametry
_Rhs číslo rozdělit pomocí zjistit zbytek.
Vrátí hodnotu objektu indexu.

## <a name="operator_star_eq"></a>  Operator * =   
Vynásobí každý element v indexu objektu podle zadaného čísla.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry
_Rhs číslo, které má násobení.

## <a name="operator_div_eq"></a>  / = – operátor 
Vydělí každý element v indexu objektu podle zadaného čísla.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parametry
_Rhs číslo, které má dělit.

## <a name="operator_at"></a>  Operátor\[\]  
Vrátí komponentu indexu v zadaném umístění.

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry
_Index celé číslo od 0 do pořadí minus 1.

### <a name="return-value"></a>Návratová hodnota
Element, který je v zadaném indexu.

### <a name="remarks"></a>Poznámky
Tato následující příklad zobrazuje hodnoty součást indexu.
```  
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  Operator ++   
Zvýší každý prvek objektu indexu.
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>Návratová hodnota
Pro operátor předpona objektu indexu (* to). Pro operátor příponu nový objekt v indexu.

## <a name="operator_add_eq"></a>  += – operátor   
Přidá zadané číslo na každý element objektu indexu.
```  
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parametry
_Rhs číslo, které chcete přidat.

### <a name="return-value"></a>Návratová hodnota
Index objektu.

## <a name="operator_eq"></a>  operátor =   
S touto zkopíruje obsah objektu zadaného indexu.
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parametry
_Other index objekt, který chcete zkopírovat z.

### <a name="return-value"></a>Návratová hodnota
Odkaz na tento objekt v indexu.

## <a name="operator_-_eq"></a>  -= – operátor
Odečítá od zadané číslo z každého prvku objektu indexu.
```  
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```  
### <a name="parameters"></a>Parametry
_Rhs číslo, které má být odečtena.

### <a name="return-value"></a>Návratová hodnota
Index objektu.   

## <a name="rank"></a>  Pořadí  
  Získá pořadí objektu indexu.
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
