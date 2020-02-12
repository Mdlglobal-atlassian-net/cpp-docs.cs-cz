---
title: location – třída
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 7f45ff6d3092bd7c27e81adddca72c9411f752d1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139827"
---
# <a name="location-class"></a>location – třída

Abstrakce fyzického umístění na hardwaru.

## <a name="syntax"></a>Syntaxe

```cpp
class location;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[location](#ctor)|Přetíženo. Vytvoří objekt `location`.|
|[~ Location – destruktor](#dtor)|Odstraní objekt `location`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[aktivní](#current)|Vrátí objekt `location` reprezentující nejvíce specifické místo, které je volající vlákno prováděno.|
|[from_numa_node](#from_numa_node)|Vrátí objekt `location`, který představuje daný uzel NUMA.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Určuje, zda dva objekty `location` reprezentují jiné umístění.|
|[operátor =](#operator_eq)|Přiřadí k tomuto jednomu obsahu jiný objekt `location`.|
|[operator = = – operátor](#operator_eq_eq)|Určuje, zda dva objekty `location` reprezentují stejné umístění.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`location`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ umístění

Odstraní objekt `location`.

```cpp
~location();
```

## <a name="current"></a>aktivní

Vrátí objekt `location` reprezentující nejvíce specifické místo, které je volající vlákno prováděno.

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>Návratová hodnota

Umístění, které představuje nejvíce specifické místo, které je volající vlákno prováděno.

## <a name="from_numa_node"></a>from_numa_node

Vrátí objekt `location`, který představuje daný uzel NUMA.

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parametry

*_NumaNodeNumber*<br/>
Číslo uzlu NUMA, pro které se má vytvořit umístění

### <a name="return-value"></a>Návratová hodnota

Umístění, které představuje uzel NUMA určený parametrem `_NumaNodeNumber`.

## <a name="ctor"></a>oblasti

Vytvoří objekt `location`.

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
Volitelné Ukazatel vazby

### <a name="remarks"></a>Poznámky

Výchozí vytvořená poloha představuje systém jako celek.

## <a name="operator_neq"></a>! = – operátor

Určuje, zda dva objekty `location` reprezentují jiné umístění.

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Operand `location`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou dvě umístění odlišná, jinak **false** .

## <a name="operator_eq"></a>operátor =

Přiřadí k tomuto jednomu obsahu jiný objekt `location`.

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zdrojový objekt `location`.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq_eq"></a>operator = = – operátor

Určuje, zda dva objekty `location` reprezentují stejné umístění.

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Operand `location`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou dvě umístění shodná, a jinak **false** .

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
