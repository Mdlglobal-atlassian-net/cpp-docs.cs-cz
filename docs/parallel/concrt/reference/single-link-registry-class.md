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
ms.openlocfilehash: 4f706b4551d71c77e136e4d65d2d6a3183293d8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454493"
---
# <a name="singlelinkregistry-class"></a>single_link_registry – třída

`single_link_registry` Je objekt `network_link_registry` , který spravuje pouze jeden blok zdroje nebo cíle.

## <a name="syntax"></a>Syntaxe

```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

#### <a name="parameters"></a>Parametry

*_Blok při znaku*<br/>
Zadejte bloku dat ukládají do `single_link_registry` objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[single_link_registry](#ctor)|Vytvoří `single_link_registry` objektu.|
|[~ single_link_registry – destruktor](#dtor)|Odstraní `single_link_registry` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Přidá odkaz `single_link_registry` objektu. (Přepíše [network_link_registry::Add –](network-link-registry-class.md#add).)|
|[začít](#begin)|Vrátí iterátor na první prvek `single_link_registry` objektu. (Přepíše [network_link_registry::BEGIN –](network-link-registry-class.md#begin).)|
|[Obsahuje](#contains)|Hledání `single_link_registry` objekt pro zadaný blok. (Přepíše [network_link_registry::contains –](network-link-registry-class.md#contains).)|
|[Počet](#count)|Vrátí počet položek v `single_link_registry` objektu. (Přepíše [network_link_registry::Count –](network-link-registry-class.md#count).)|
|[remove](#remove)|Odebere odkaz `single_link_registry` objektu. (Přepíše [network_link_registry::Remove –](network-link-registry-class.md#remove).)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="add"></a> Přidat

Přidá odkaz `single_link_registry` objektu.

```
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který chcete přidat.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_link_target –](invalid-link-target-class.md) výjimku, pokud už existuje odkaz v registru.

##  <a name="begin"></a> začít

Vrátí iterátor na první prvek `single_link_registry` objektu.

```
virtual iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek `single_link_registry` objektu.

### <a name="remarks"></a>Poznámky

Koncový stav je indikován `NULL` odkaz.

##  <a name="contains"></a> Obsahuje

Hledání `single_link_registry` objekt pro zadaný blok.

```
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který má být vyhledán v `single_link_registry` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud byl nalezen odkaz, **false** jinak.

##  <a name="count"></a> Počet

Vrátí počet položek v `single_link_registry` objektu.

```
virtual size_t count();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v `single_link_registry` objektu.

##  <a name="remove"></a> odebrat

Odebere odkaz `single_link_registry` objektu.

```
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který se odeberou, pokud se nenašel.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud odkazu byl nalezen a odebrání **false** jinak.

##  <a name="ctor"></a> single_link_registry –

Vytvoří `single_link_registry` objektu.

```
single_link_registry();
```

##  <a name="dtor"></a> ~ single_link_registry –

Odstraní `single_link_registry` objektu.

```
virtual ~single_link_registry();
```

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_operation](invalid-operation-class.md) výjimku, pokud je volána před odebráním odkazu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[multi_link_registry – třída](multi-link-registry-class.md)
