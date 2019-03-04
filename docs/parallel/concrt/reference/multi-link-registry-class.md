---
title: multi_link_registry – třída
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: 388cc0082f69041368d1a444179855451d552ce6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264756"
---
# <a name="multilinkregistry-class"></a>multi_link_registry – třída

`multi_link_registry` Je objekt `network_link_registry` , který spravuje více zdrojových bloků nebo více cílových bloků.

## <a name="syntax"></a>Syntaxe

```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

#### <a name="parameters"></a>Parametry

*_Block*<br/>
Zadejte bloku dat ukládají do `multi_link_registry` objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[multi_link_registry](#ctor)|Vytvoří `multi_link_registry` objektu.|
|[~multi_link_registry Destructor](#dtor)|Odstraní `multi_link_registry` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Přidá odkaz `multi_link_registry` objektu. (Přepíše [network_link_registry::Add –](network-link-registry-class.md#add).)|
|[začít](#begin)|Vrátí iterátor na první prvek `multi_link_registry` objektu. (Overrides [network_link_registry::begin](network-link-registry-class.md#begin).)|
|[Obsahuje](#contains)|Hledání `multi_link_registry` objekt pro zadaný blok. (Přepíše [network_link_registry::contains –](network-link-registry-class.md#contains).)|
|[Počet](#count)|Vrátí počet položek v `multi_link_registry` objektu. (Přepíše [network_link_registry::Count –](network-link-registry-class.md#count).)|
|[remove](#remove)|Odebere odkaz `multi_link_registry` objektu. (Přepíše [network_link_registry::Remove –](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Nastaví horní mez počtu odkazů `multi_link_registry` objekt může obsahovat.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="add"></a> Přidat

Přidá odkaz `multi_link_registry` objektu.

```
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který chcete přidat.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_link_target –](invalid-link-target-class.md) výjimka Pokud odkaz je již v registru, nebo pokud vazby již byl nastaven s `set_bound` funkce a odkaz byl v mezičase odebrán.

##  <a name="begin"></a> začít

Vrátí iterátor na první prvek `multi_link_registry` objektu.

```
virtual iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek `multi_link_registry` objektu.

### <a name="remarks"></a>Poznámky

Koncový stav je indikován `NULL` odkaz.

##  <a name="contains"></a> Obsahuje

Hledání `multi_link_registry` objekt pro zadaný blok.

```
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který má být vyhledán v `multi_link_registry` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud byl nalezen zadaný blok, **false** jinak.

##  <a name="count"></a> Počet

Vrátí počet položek v `multi_link_registry` objektu.

```
virtual size_t count();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v `multi_link_registry` objektu.

##  <a name="ctor"></a> multi_link_registry –

Vytvoří `multi_link_registry` objektu.

```
multi_link_registry();
```

##  <a name="dtor"></a> ~multi_link_registry

Odstraní `multi_link_registry` objektu.

```
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_operation](invalid-operation-class.md) výjimku, pokud je volána před odstraněním všechny odkazy.

##  <a name="remove"></a> odebrat

Odebere odkaz `multi_link_registry` objektu.

```
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který se odeberou, pokud se nenašel.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud odkazu byl nalezen a odebrání **false** jinak.

##  <a name="set_bound"></a> set_bound –

Nastaví horní mez počtu odkazů `multi_link_registry` objekt může obsahovat.

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maximální počet, který odkazuje `multi_link_registry` objekt může obsahovat.

### <a name="remarks"></a>Poznámky

Po nastavení vazbu způsobí odpojení položku `multi_link_registry` objektu zadejte neměnného stavu kde další volání `add` vyvolá výjimku `invalid_link_target` výjimky.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[single_link_registry – třída](single-link-registry-class.md)
