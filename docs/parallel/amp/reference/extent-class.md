---
title: extent – třída (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: 3e8dae7b76ea2efc852486a19f5d298cda477012
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126718"
---
# <a name="extent-class-c-amp"></a>extent – třída (C++ AMP)

Představuje vektor *n* celočíselných hodnot, které určují meze *n*-dimenzionálního prostoru, který má počátek 0. Hodnoty ve vektoru jsou seřazené od nejvýznamnějších po nejméně významné.

## <a name="syntax"></a>Syntaxe

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí objektu `extent`.

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Rozsah – konstruktor](#ctor)|Inicializuje novou instanci třídy `extent`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[zobrazí](#contains)|Ověřuje, že zadaný objekt `extent` má zadané pořadí.|
|[hodnota](#size)|Vrátí celkovou lineární velikost rozsahu (v jednotkách prvků).|
|[podobě](#tile)|Vytvoří objekt `tiled_extent` s rozsahy dlaždic, které jsou zadané v zadaných dimenzích.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[podnikatel](#operator_min)|Vrátí nový objekt `extent`, který je vytvořen odečtením `index` prvků z odpovídajících prvků `extent`.|
|[--– operátor](#operator_min_min)|Sníží všechny prvky objektu `extent`.|
|[% = – operátor](#operator_mod_eq)|Vypočítá zbytek (zbytek) každého prvku v objektu `extent`, pokud je tento prvek dělen číslem.|
|[operator * = – operátor](#operator_star_eq)|Vynásobí každý prvek `extent` objektu číslem.|
|[operator/= – operátor](#operator_min_eq)|Vydělí každý prvek `extent` objektu číslem.|
|[Rozsah:: operator\[\]](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[operator + – operátor](#operator_add)|Vrátí nový objekt `extent`, který je vytvořen přidáním odpovídajícího prvku `index` a `extent`.|
|[operator + + – operátor](#operator_add_add)|Zvýší všechny prvky objektu `extent`.|
|[operator + = – operátor](#operator_add_eq)|Přidá zadané číslo do každého prvku `extent` objektu.|
|[operátor =](#operator_eq)|Zkopíruje obsah jiného objektu `extent` do tohoto typu.|
|[-= – operátor](#operator_min_eq)|Odečte zadané číslo od každého prvku `extent` objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta Rank](#rank_constant)|Získá pořadí objektu `extent`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`extent`

## <a name="contains"></a>zobrazí

Určuje, zda je zadaná hodnota [indexu](index-class.md) obsažena v objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Hodnota `index` k otestování.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je zadaná hodnota *indexu* obsažena v objektu `extent`; v opačném případě **false**.

## <a name="ctor"></a>stavební

Inicializuje novou instanci třídy "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Array*<br/>
Pole `_Rank` celé číslo, které se používá k vytvoření nového objektu `extent`.

*_I*<br/>
Délka rozsahu.

*_I0*<br/>
Délka nejvýznamnějšího rozměru.

*_I1*<br/>
Délka dalšího významného rozměru.

*_I2*<br/>
Délka nejméně významného rozměru.

*_Other*<br/>
Objekt `extent`, na kterém je založen nový objekt `extent`.

## <a name="remarks"></a>Poznámky

Výchozí konstruktor inicializuje objekt `extent`, který má pořadí tří.

Pokud je pole použito k vytvoření objektu `extent`, délka pole musí odpovídat rozměru objektu `extent`.

## <a name="operator_mod_eq"></a>% = – operátor

Vypočítá zbytek (zbytek) každého prvku v ' rozsahu ', pokud je tento prvek dělen číslem.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, ve kterém se mají najít zbytky.

### <a name="return-value"></a>Návratová hodnota

Objekt `extent`

## <a name="operator_star_eq"></a>operator * = – operátor

Vynásobí každý prvek v objektu "rozsah" zadaným číslem.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které se má vynásobit.

### <a name="return-value"></a>Návratová hodnota

Objekt `extent`

## <a name="operator_add"></a>operator + – operátor

Vrátí nový objekt `extent` vytvořený přidáním odpovídajícího prvku `index` a `extent`.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Objekt `index`, který obsahuje prvky, které mají být přidány.

### <a name="return-value"></a>Návratová hodnota

Nový objekt `extent`

## <a name="operator_add_add"></a>operator + + – operátor

Zvýší všechny prvky objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Pro operátor prefix, objekt `extent` (`*this`). Pro operátor přípona nový objekt `extent`.

## <a name="operator_add_eq"></a>operator + = – operátor

Přičte zadané číslo ke každému prvku objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, index nebo rozsah, který chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Výsledný objekt `extent`.

## <a name="operator_min"></a>podnikatel

Vytvoří nový objekt `extent` odečtením každého elementu v zadaném `index` objektu z odpovídajícího prvku v tomto objektu `extent`.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Objekt `index`, který obsahuje prvky, které mají být odečteny.

### <a name="return-value"></a>Návratová hodnota

Nový objekt `extent`

## <a name="operator_min_min"></a>--– operátor

Sníží všechny prvky v objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Pro operátor prefix, objekt `extent` (`*this`). Pro operátor přípona nový objekt `extent`.

## <a name="operator_div_eq"></a>operator/= – operátor

Vydělí každý prvek v objektu "rozsah" zadaným číslem.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, kterým se má dělit.

### <a name="return-value"></a>Návratová hodnota

Objekt `extent`

## <a name="operator_min_eq"></a>-= – operátor

Odečte zadané číslo od každého prvku objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které má být odečteno.

### <a name="return-value"></a>Návratová hodnota

Výsledný objekt `extent`.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah jiného objektu "rozsah" do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `extent`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `extent`.

## <a name="operator_at"></a>Rozsah:: operator \[\]

Vrátí prvek, který je v zadaném indexu.

### <a name="syntax"></a>Syntaxe

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Celé číslo od 0 do pořadí minus 1.

### <a name="return-value"></a>Návratová hodnota

Prvek na zadaném indexu.

## <a name="rank_constant"></a>pořadí

Ukládá pořadí objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```cpp
static const int rank = _Rank;
```

## <a name="size"></a>hodnota

Vrátí celkovou lineární velikost objektu `extent` (v jednotkách prvků).

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a>podobě

Vytvoří objekt tiled_extent se zadanými Rozměry dlaždice.

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Nejvýznamnější komponenta v rozsahu vedle sebe.
*_Dim1*<br/>
Další nejvýznamnější součást v rozsahu.
*_Dim2*<br/>
Nejméně významná komponenta rozsahu, který je v dlaždicích.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
