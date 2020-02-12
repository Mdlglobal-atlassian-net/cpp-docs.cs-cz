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
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138890"
---
# <a name="network_link_registry-class"></a>network_link_registry – třída

Abstraktní základní třída `network_link_registry` spravuje propojení mezi zdrojovými a cílovými bloky.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Datový typ Block, který je uložen v `network_link_registry`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`const_pointer`|Typ, který poskytuje ukazatel na prvek `const` v objektu `network_link_registry`.|
|`const_reference`|Typ, který poskytuje odkaz na `const` prvek uložený v objektu `network_link_registry` pro čtení a provádění operací const.|
|`iterator`|Typ, který poskytuje iterátor, který může číst nebo upravovat libovolný prvek v objektu `network_link_registry`.|
|`type`|Typ, který představuje typ bloku uložený v objektu `network_link_registry`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Při přepsání v odvozené třídě přidá odkaz na objekt `network_link_registry`.|
|[ifunctiondiscovery](#begin)|Při přepsání v odvozené třídě vrátí iterátor na první prvek v objektu `network_link_registry`.|
|[zobrazí](#contains)|Při přepsání v odvozené třídě vyhledá objekt `network_link_registry` pro zadaný blok.|
|[count](#count)|Při přepsání v odvozené třídě vrátí počet položek v objektu `network_link_registry`.|
|[remove](#remove)|Při přepsání v odvozené třídě Odebere zadaný blok z objektu `network_link_registry`.|

## <a name="remarks"></a>Poznámky

`network link registry` není bezpečný pro souběžný přístup.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`network_link_registry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="add"></a>přidávání

Při přepsání v odvozené třídě přidá odkaz na objekt `network_link_registry`.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být přidán.

## <a name="begin"></a>ifunctiondiscovery

Při přepsání v odvozené třídě vrátí iterátor na první prvek v objektu `network_link_registry`.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek v objektu `network_link_registry`.

### <a name="remarks"></a>Poznámky

Koncový stav iterátoru je označen odkazem `NULL`.

## <a name="contains"></a>zobrazí

Při přepsání v odvozené třídě vyhledá objekt `network_link_registry` pro zadaný blok.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který je prohledáván v objektu `network_link_registry`.

### <a name="return-value"></a>Návratová hodnota

**hodnota true** , pokud byl blok nalezen, jinak **false** .

## <a name="count"></a>výpočtu

Při přepsání v odvozené třídě vrátí počet položek v objektu `network_link_registry`.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v objektu `network_link_registry`.

## <a name="remove"></a>odebrány

Při přepsání v odvozené třídě Odebere zadaný blok z objektu `network_link_registry`.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být odebrán, pokud je nalezen.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl odkaz nalezen a odebrán, jinak **false** .

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[single_link_registry – třída](single-link-registry-class.md)<br/>
[multi_link_registry – třída](multi-link-registry-class.md)
