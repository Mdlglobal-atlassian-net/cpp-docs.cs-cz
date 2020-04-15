---
title: index – třída
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365155"
---
# <a name="index-class"></a>index – třída

Definuje vektor *N*n-dimenzionálního indexu.

## <a name="syntax"></a>Syntaxe

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí nebo počet dimenzí.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[konstruktor indexu](#index_ctor)|Inicializuje novou instanci třídy. `index`|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátora--](#operator--)|Sníží každý prvek objektu. `index`|
|[operátor%=](#operator_mod_eq)|Vypočítá modul (zbytek) každého prvku `index` v objektu, když je tento prvek vydělen číslem.|
|[operátor*=](#operator_star_eq)|Vynásobí `index` každý prvek objektu číslem.|
|[operátor/=](#operator_div_eq)|Vydělí každý `index` prvek objektu číslem.|
|[index::operátor\[\]](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[operátor++](#operator_add_add)|Increments každý prvek `index` objektu.|
|[operátor+=](#operator_add_eq)|Přidá zadané číslo ke každému `index` prvku objektu.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `index` objektu do tohoto objektu.|
|[operátor-=](#operator_-_eq)|Odečte zadané číslo od každého `index` prvku objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[pořadí konstanta](#rank)|Ukládá pořadí objektu. `index`|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`index`

## <a name="remarks"></a>Poznámky

Struktura `index` představuje souřadnicový vektor *N* celočísel, který určuje jedinečnou pozici v n-dimenzionálním prostoru. *N* Hodnoty ve vektoru jsou seřazeny od nejvýznamnějších po nejméně významné. Hodnoty komponent můžete načíst pomocí [operator=](#operator_eq).

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Obor názvů:** Souběžnost

## <a name="index-constructor"></a><a name="index_ctor"></a>konstruktor indexu

Inicializuje novou instanci třídy indexu.

```cpp
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

*_Array*<br/>
Jednorozměrné pole s hodnotami pořadí.

*_I*<br/>
Umístění indexu v jednorozměrném indexu.

*_I0*<br/>
Délka nejvýznamnější dimenze.

*_I1*<br/>
Délka následující ho dimenzí.

*_I2*<br/>
Délka nejméně významné dimenze.

*_Other*<br/>
Objekt indexu, na kterém je založen nový objekt indexu.

## <a name="operator--"></a><a name="operator--"></a>operátora--

Sníží každý prvek objektu indexu.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Vrácené hodnoty

Pro operátor předpony, objekt indexu (*this). Pro operátor přípony nový objekt indexu.

## <a name="operator"></a><a name="operator_mod_eq"></a>operátor%=

Vypočítá modul (zbytek) každého prvku v objektu indexu, pokud je tento prvek vydělen zadaným číslem.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, podle kterého chcete najít modul.

## <a name="return-value"></a>Návratová hodnota

Index objektu.

## <a name="operator"></a><a name="operator_star_eq"></a>operátor*=

Vynásobí každý prvek v objektu indexu zadaným číslem.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo násobit.

## <a name="operator"></a><a name="operator_div_eq"></a>operátor/=

Vydělí každý prvek v objektu indexu zadaným číslem.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, podle kterého chcete vydělit.

## <a name="operator"></a><a name="operator_at"></a>Operátor\[\]

Vrátí součást indexu v zadaném umístění.

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Celé číslo od 0 do pořadí mínus 1.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je v zadaném indexu.

### <a name="remarks"></a>Poznámky

Následující příklad zobrazuje hodnoty komponent indexu.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>operátor++

Zintáží každý prvek objektu indexu.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Pro operátor předpony, objekt indexu (*this). Pro operátor přípony nový objekt indexu.

## <a name="operator"></a><a name="operator_add_eq"></a>operátor+=

Přidá zadané číslo ke každému prvku objektu indexu.

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Index objektu.

## <a name="operator"></a><a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu indexu do tohoto objektu.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Index objektu kopírovat z.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt indexu.

## <a name="operator-"></a><a name="operator_-_eq"></a>operátor-=

Odečte zadané číslo od každého prvku objektu indexu.

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo odečíst.

### <a name="return-value"></a>Návratová hodnota

Index objektu.

## <a name="rank"></a><a name="rank"></a>Hodnost

Získá pořadí objektu indexu.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
