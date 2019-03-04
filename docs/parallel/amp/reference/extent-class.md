---
title: extent – třída (C++ AMP)
ms.date: 11/04/2016
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
ms.openlocfilehash: 2236b1a1b72f307dae1efa0cfe197e222820c460
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270186"
---
# <a name="extent-class-c-amp"></a>extent – třída (C++ AMP)

Představuje vektor *N* celočíselných hodnot určujících hranice *N*-rozměrného prostoru s počátkem 0. Hodnoty ve vektoru jsou seřazeny od nejvýznamnější po nejméně významnou.

### <a name="syntax"></a>Syntaxe

```
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Řád objektu `extent` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Namespace:** Souběžnost

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[v rozsahu konstruktoru](#ctor)|Inicializuje novou instanci třídy `extent` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Obsahuje](#contains)|Ověřuje, že zadaný `extent` objektu má určený řád.|
|[Velikost](#size)|Vrátí celkovou lineární velikost rozsahu (v jednotkách prvků).|
|[dlaždice](#tile)|Vytvoří `tiled_extent` objekt s rozsahy bloku dle zadaných rozměrů.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator-](#operator_min)|Vrátí nový `extent` objekt, který je vytvořen tak, že se `index` prvků z odpovídajících `extent` elementy.|
|[operator--](#operator_min_min)|Sníží každý prvek `extent` objektu.|
|[operator%=](#operator_mod_eq)|Vypočítá modulo (zbytek) každého prvku `extent` objektu při dělení podle čísla.|
|[Operator * =](#operator_star_eq)|Vynásobí každý prvek `extent` číslem.|
|[/ = – operátor](#operator_min_eq)|Vydělí každý prvek `extent` číslem.|
|[Extent::Operator\[\]](#operator_at)|Vrátí prvek, který je v zadaném indexu.|
|[Operator +](#operator_add)|Vrátí nový `extent` objekt, který je vytvořený přidáním odpovídajících `index` a `extent` elementy.|
|[Operator ++](#operator_add_add)|Zvýší všechny prvky objektu `extent` objektu.|
|[operator+=](#operator_add_eq)|Přičte zadané číslo ke každému prvku objektu `extent` objektu.|
|[operátor =](#operator_eq)|Zkopíruje obsah jiného `extent` do tohoto objektu.|
|[operator-=](#operator_min_eq)|Odečte zadané číslo od každého prvku objektu `extent` objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RANK – konstanta](#rank)|Zjistí řád objektu `extent` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`extent`

## <a name="contains"></a> Obsahuje

Určuje, zda zadaný [index](index-class.md) hodnota je obsažen v objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
`index` Hodnotu k testování.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud zadaný *index* hodnota je obsažen v `extent` objektu; v opačném případě **false**.

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

*_Pole*<br/>
Pole `_Rank` celých čísel, která se používá k vytvoření nového `extent` objektu.

*_I*<br/>
Délka rozsahu.

*_I0*<br/>
Délka nejvýznamnějšího rozměru.

*_I1*<br/>
Délka další na nejvýznamnější dimenze.

*_I2*<br/>
Velikost nejméně významného rozměru.

*Ji_né*<br/>
`extent` Objekt, kterému nové `extent` objektu je založen.

## <a name="remarks"></a>Poznámky

Konstruktor bez parametru inicializuje `extent` objekt, který stupně tři.

Pokud pole se používá ke konstrukci `extent` objekt, musí délka pole odpovídat stupni objektu `extent` objektu.

##  <a name="operator_mod_eq"></a> Operator % =

Vypočítá modulo (zbytek) každého prvku v rozsahu při dělení podle čísla.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které chcete najít zbytek z.

### <a name="return-value"></a>Návratová hodnota

`extent` Objektu.

##  <a name="operator_star_eq"></a> Operator * =

Vynásobí každý prvek v objektu "rozsah" zadaným číslem.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Násobené číslo.

### <a name="return-value"></a>Návratová hodnota

`extent` Objektu.

## <a name="operator_add"></a> Operator +

Vrátí nový `extent` objekt vytvořený přidáním odpovídajících `index` a `extent` elementy.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`index` Objekt, který obsahuje prvky pro přidání.

### <a name="return-value"></a>Návratová hodnota

Nové `extent` objektu.

##  <a name="operator_add_add"></a> Operator ++

Zvýší hodnotu všech prvků objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Pro prefixový operátor `extent` objektu (`*this`). Pro sufixový operátor nový `extent` objektu.

##  <a name="operator_add_eq"></a> += – operátor

Přičte zadané číslo ke každému prvku objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, index nebo rozsah má přidat.

### <a name="return-value"></a>Návratová hodnota

Výsledná `extent` objektu.

##  <a name="operator_min"></a> Operator-

Vytvoří novou `extent` objekt odečtením každého prvku v zadaném `index` objekt z odpovídajícího prvku v tomto `extent` objektu.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`index` Objekt, který obsahuje prvky pro odečtení.

### <a name="return-value"></a>Návratová hodnota

Nové `extent` objektu.

##  <a name="operator_min_min"></a> Operator--

Sníží každý prvek v objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Pro prefixový operátor `extent` objektu (`*this`). Pro sufixový operátor nový `extent` objektu.

##  <a name="operator_div_eq"></a> / = – operátor

Vydělí každý prvek v objektu "rozsah" zadaným číslem.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Číslo, které má dělit.

### <a name="return-value"></a>Návratová hodnota

`extent` Objektu.

##  <a name="operator_min_eq"></a> operátor-=

Odečte zadané číslo od každého prvku objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Odečítané číslo.

### <a name="return-value"></a>Návratová hodnota

Výsledná `extent` objektu.

##  <a name="operator_eq"></a> operátor =

Zkopíruje obsah jiného objektu "rozsah" do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`extent` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `extent` objektu.

##  <a name="operator_at"></a> Extent::Operator \[\]

Vrátí prvek, který je v zadaném indexu.

### <a name="syntax"></a>Syntaxe

```
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Celé číslo od 0 do řádu mínus 1.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je v zadaném indexu.

##  <a name="rank_constant"></a> pořadí

Udržuje řád objektu "rozsah".

### <a name="syntax"></a>Syntaxe

```
static const int rank = _Rank;
```

##  <a name="size"></a> Velikost

Vrátí celkovou lineární velikost `extent` objekt (v jednotkách prvků).

### <a name="syntax"></a>Syntaxe

```
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a> dlaždice

Vytvoří objekt tiled_extent se specifikovanou dimenzí dlaždice.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Nejvýznamnější komponenta dlaždic.
*_Dim1*<br/>
Další na nejvýznamnější komponenta dlaždic.
*_Dim2*<br/>
Nejméně významná komponenta dlaždic.

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
