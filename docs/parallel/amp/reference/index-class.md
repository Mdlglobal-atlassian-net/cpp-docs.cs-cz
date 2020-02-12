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
ms.openlocfilehash: 06a5fa9a2d7e645c46b90ace957d31251baed81c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127800"
---
# <a name="index-class"></a>index – třída

Definuje *N*-dimenzionální vektor indexu.

## <a name="syntax"></a>Syntaxe

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Rozměr nebo počet rozměrů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[index – konstruktor](#index_ctor)|Inicializuje novou instanci třídy `index`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[--– operátor](#operator--)|Sníží všechny prvky objektu `index`.|
|[% = – operátor](#operator_mod_eq)|Vypočítá zbytek (zbytek) každého prvku v objektu `index`, pokud je tento prvek dělen číslem.|
|[operator * = – operátor](#operator_star_eq)|Vynásobí každý prvek `index` objektu číslem.|
|[operator/= – operátor](#operator_div_eq)|Vydělí každý prvek `index` objektu číslem.|
|[index:: operator\[\]](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[operator + + – operátor](#operator_add_add)|Zvýší všechny prvky objektu `index`.|
|[operator + = – operátor](#operator_add_eq)|Přidá zadané číslo do každého prvku `index` objektu.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `index` do tohoto objektu.|
|[-= – operátor](#operator_-_eq)|Odečte zadané číslo od každého prvku `index` objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta Rank](#rank)|Ukládá pořadí objektu `index`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`index`

## <a name="remarks"></a>Poznámky

Struktura `index` představuje vektor souřadnic *n* celých čísel, která určují jedinečnou pozici v *n*-dimenzionálním prostoru. Hodnoty ve vektoru jsou seřazené od nejvýznamnějších po nejméně významné. Hodnoty komponent můžete načíst pomocí [operátoru =](#operator_eq).

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="index_ctor"></a>index – konstruktor

Inicializuje novou instanci třídy index.

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
Délka nejvýznamnějšího rozměru.

*_I1*<br/>
Délka dalšího významného rozměru.

*_I2*<br/>
Délka nejméně významného rozměru.

*_Other*<br/>
Indexový objekt, na kterém je založen nový index objektu.

## <a name="operator--"></a>--– operátor

Sníží všechny prvky objektu index.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Vrácené hodnoty

Pro operátor prefix, objekt index (* this). Pro operátor přípona nový objekt index.

## <a name="operator_mod_eq"></a>% = – operátor

Vypočítá zbytek (zbytek) každého prvku v objektu indexu, pokud je tento prvek rozdělen podle zadaného čísla.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které má být rozděleno, aby bylo možné najít zbytky.

## <a name="return-value"></a>Návratová hodnota

Objekt index.

## <a name="operator_star_eq"></a>operator * = – operátor

Vynásobí každý prvek v objektu index zadaným číslem.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které se má vynásobit.

## <a name="operator_div_eq"></a>operator/= – operátor

Vydělí každý prvek v objektu index zadaným číslem.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, kterým se má dělit.

## <a name="operator_at"></a>operátor\[\]

Vrátí komponentu indexu v zadaném umístění.

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
Celé číslo od 0 do pořadí minus 1.

### <a name="return-value"></a>Návratová hodnota

Prvek na zadaném indexu.

### <a name="remarks"></a>Poznámky

Následující příklad zobrazí hodnoty součásti indexu.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>operator + + – operátor

Zvýší všechny prvky objektu index.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Pro operátor prefix, objekt index (* this). Pro operátor přípona nový objekt index.

## <a name="operator_add_eq"></a>operator + = – operátor

Přidá zadané číslo do každého prvku objektu index.

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
Číslo, které se má přidat

### <a name="return-value"></a>Návratová hodnota

Objekt index.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu indexu do tohoto typu.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt indexu, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt indexu.

## <a name="operator_-_eq"></a>-= – operátor

Odečte zadané číslo od každého prvku objektu index.

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
Číslo, které má být odečteno.

### <a name="return-value"></a>Návratová hodnota

Objekt index.

## <a name="rank"></a>Pořadí

Získá pořadí objektu indexu.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
