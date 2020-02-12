---
title: single_link_registry – třída
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142725"
---
# <a name="single_link_registry-class"></a>single_link_registry – třída

Objekt `single_link_registry` je `network_link_registry`, který spravuje pouze jeden zdrojový nebo cílový blok.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Datový typ Block uložený v objektu `single_link_registry`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[single_link_registry](#ctor)|Vytvoří objekt `single_link_registry`.|
|[~ single_link_registry destruktor](#dtor)|Odstraní objekt `single_link_registry`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Přidá odkaz na objekt `single_link_registry`. (Potlačení [network_link_registry:: Add](network-link-registry-class.md#add).)|
|[ifunctiondiscovery](#begin)|Vrátí iterátor na první prvek objektu `single_link_registry`. (Overrides [network_link_registry:: begin](network-link-registry-class.md#begin).)|
|[zobrazí](#contains)|Vyhledá zadaný blok v objektu `single_link_registry`. (Potlačení [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Spočítá počet položek v objektu `single_link_registry`. (Potlačení [network_link_registry:: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Odebere propojení z objektu `single_link_registry`. (Potlačení [network_link_registry:: Remove](network-link-registry-class.md#remove).)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="add"></a>přidávání

Přidá odkaz na objekt `single_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být přidán.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_link_target](invalid-link-target-class.md) , pokud v registru již existuje odkaz.

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor na první prvek objektu `single_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek v objektu `single_link_registry`.

### <a name="remarks"></a>Poznámky

Koncový stav je označen odkazem `NULL`.

## <a name="contains"></a>zobrazí

Vyhledá zadaný blok v objektu `single_link_registry`.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být prohledán v objektu `single_link_registry`.

### <a name="return-value"></a>Návratová hodnota

**hodnota true** , pokud byl odkaz nalezen, jinak **false** .

## <a name="count"></a>výpočtu

Spočítá počet položek v objektu `single_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v objektu `single_link_registry`.

## <a name="remove"></a>odebrány

Odebere propojení z objektu `single_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být odebrán, pokud je nalezen.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl odkaz nalezen a odebrán, jinak **false** .

## <a name="ctor"></a>single_link_registry

Vytvoří objekt `single_link_registry`.

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

Odstraní objekt `single_link_registry`.

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_operation](invalid-operation-class.md) , pokud je volána před odebráním odkazu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[multi_link_registry – třída](multi-link-registry-class.md)
