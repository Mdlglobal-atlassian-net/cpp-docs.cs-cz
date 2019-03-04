---
title: network_link_registry – třída
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 2537ed857651b5210b104a270b3d827246b8339a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273345"
---
# <a name="networklinkregistry-class"></a>network_link_registry – třída

`network_link_registry` Abstraktní základní třída spravuje propojení mezi zdrojovými a cílovými bloky.

## <a name="syntax"></a>Syntaxe

```
template<class _Block>
class network_link_registry;
```

#### <a name="parameters"></a>Parametry

*_Block*<br/>
Zadejte bloku dat ukládají do `network_link_registry`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`const_pointer`|Typ, který poskytuje ukazatel na `const` prvek `network_link_registry` objektu.|
|`const_reference`|Typ, který poskytuje odkaz na `const` element uložené v `network_link_registry` objekt pro čtení a provádění operací const.|
|`iterator`|Typ, který poskytuje iterátor, který může číst nebo upravovat libovolný prvek v `network_link_registry` objektu.|
|`type`|Typ, který představuje typ bloku, které jsou uložené v `network_link_registry` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Při přepisu v odvozené třídě, přidá odkaz `network_link_registry` objektu.|
|[začít](#begin)|Při přepisu v odvozené třídě vrátí iterátor na první prvek `network_link_registry` objektu.|
|[Obsahuje](#contains)|Při přepisu v odvozené třídě, hledá `network_link_registry` objekt pro zadaný blok.|
|[Počet](#count)|Při přepisu v odvozené třídě vrátí počet položek v `network_link_registry` objektu.|
|[remove](#remove)|Při přepisu v odvozené třídě Odstraní zadaný blok z `network_link_registry` objektu.|

## <a name="remarks"></a>Poznámky

`network link registry` Není bezpečné pro souběžný přístup.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`network_link_registry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="add"></a> Přidat

Při přepisu v odvozené třídě, přidá odkaz `network_link_registry` objektu.

```
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který chcete přidat.

##  <a name="begin"></a> začít

Při přepisu v odvozené třídě vrátí iterátor na první prvek `network_link_registry` objektu.

```
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek `network_link_registry` objektu.

### <a name="remarks"></a>Poznámky

Je indikován stav koncový iterátor `NULL` odkaz.

##  <a name="contains"></a> Obsahuje

Při přepisu v odvozené třídě, hledá `network_link_registry` objekt pro zadaný blok.

```
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který má být vyhledán v `network_link_registry` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud bloku byla nalezena, **false** jinak.

##  <a name="count"></a> Počet

Při přepisu v odvozené třídě vrátí počet položek v `network_link_registry` objektu.

```
virtual size_t count() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v `network_link_registry` objektu.

##  <a name="remove"></a> odebrat

Při přepisu v odvozené třídě Odstraní zadaný blok z `network_link_registry` objektu.

```
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který se odeberou, pokud se nenašel.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud odkazu byl nalezen a odebrání **false** jinak.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[single_link_registry – třída](single-link-registry-class.md)<br/>
[multi_link_registry – třída](multi-link-registry-class.md)
