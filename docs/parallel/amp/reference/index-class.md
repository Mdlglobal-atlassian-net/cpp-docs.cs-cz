---
title: index – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 154f9b4835f7dc18fcf45de53b078d3d5b649e37
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446918"
---
# <a name="index-class"></a>index – třída

Definuje *N*-multidimenzionálním index pographics-cpp-amp.md.

## <a name="syntax"></a>Syntaxe

```
template <int _Rank>
class index;
```

#### <a name="parameters"></a>Parametry

*_Rank*<br/>
Řád, neboli počet rozměrů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[index konstruktor](#ctor)|Inicializuje novou instanci třídy `index` třídy.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator--](#operator--)|Sníží každý prvek `index` objektu.|
|[Operator(MOD) =](#operator_mod_eq)|Vypočítá modulo (zbytek) každého prvku `index` objektu při dělení podle čísla.|
|[Operator * =](#operator_star_eq)|Vynásobí každý prvek `index` číslem.|
|[/ = – operátor](#operator_div_eq)|Vydělí každý prvek `index` číslem.|
|[index::Operator\[\]](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[Operator ++](#operator_add_add)|Zvýší všechny prvky objektu `index` objektu.|
|[operator+=](#operator_add_eq)|Přičte zadané číslo ke každému prvku objektu `index` objektu.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `index` do tohoto objektu.|
|[operátor-=](#operator_-_eq)|Odečte zadané číslo od každého prvku objektu `index` objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RANK – konstanta](#rank)|Udržuje řád objektu `index` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`index`

## <a name="remarks"></a>Poznámky

`index` Struktura představuje vektor souřadnic *N* celých čísel, které určují jedinečné umístění v *N*-rozměrného prostoru. Hodnoty ve vektoru jsou seřazeny od nejvýznamnější po nejméně významnou. Můžete načíst hodnoty komponent pomocí [operátoru =](#operator_eq).

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Namespace:** souběžnosti

## <a name="index_ctor"></a> index konstruktor

Inicializuje novou instanci třídy indexu.

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

*_Pole*<br/>
Jednorozměrné pole s hodnotami řádů.

*_I*<br/>
Umístění indexu v jednorozměrném indexu.

*_I0*<br/>
Délka nejvýznamnějšího rozměru.

*_I1*<br/>
Délka další na nejvýznamnější dimenze.

*_I2*<br/>
Velikost nejméně významného rozměru.

*Ji_né*<br/>
Index objektu, na kterých je založena na nový objekt indexu.

## <a name="operator--"></a>  Operator--

Sníží každý prvek objektu indexu.
```
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```
### <a name="return-values"></a>Vrácené hodnoty

Pro prefixový operátor objekt indexu (* to). Pro sufixový operátor nový objekt v indexu.

## <a name="operator_mod_eq"></a>  Operator(MOD) =

Vypočítá modulo (zbytek) jednotlivých prvků v objektu indexu při dělení zadaným číslem.

```
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```
### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které má rozdělit podle najít zbytek.

## <a name="return-value"></a>Návratová hodnota
Index objektu.

## <a name="operator_star_eq"></a>  Operator * =

Vynásobí každý prvek v objektu indexu zadaným číslem.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Násobené číslo.

## <a name="operator_div_eq"></a>  / = – operátor

Vydělí každý prvek v objektu indexu zadaným číslem.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```
### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které má dělit.

## <a name="operator_at"></a>  – Operátor\[\]

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

*_Index*<br/>
Celé číslo od 0 do řádu mínus 1.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je v zadaném indexu.

### <a name="remarks"></a>Poznámky

Následující příklad zobrazí hodnoty komponent indexu.
```
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  Operator ++

Zvýší hodnotu všech prvků objektu indexu.
```
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```
### <a name="return-value"></a>Návratová hodnota

Pro prefixový operátor objekt indexu (* to). Pro sufixový operátor nový objekt v indexu.

## <a name="operator_add_eq"></a>  += – operátor

Přičte zadané číslo ke každému prvku objektu indexu.
```
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```
### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Přičítané číslo.

### <a name="return-value"></a>Návratová hodnota

Index objektu.

## <a name="operator_eq"></a>  operátor =

Zkopíruje obsah zadaného indexu objektu do tohoto objektu.
```
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```
### <a name="parameters"></a>Parametry

*Ji_né*<br/>
Index objektu bude kopírováno.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt indexu.

## <a name="operator_-_eq"></a>  operátor-=

Odečte zadané číslo od každého prvku objektu indexu.
```
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```
### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Odečítané číslo.

### <a name="return-value"></a>Návratová hodnota

Index objektu.

## <a name="rank"></a>  pořadí
  Zjistí řád objektu indexu.
```
static const int rank = _Rank;
```
## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
