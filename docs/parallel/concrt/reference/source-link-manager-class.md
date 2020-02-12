---
title: source_link_manager – třída
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142698"
---
# <a name="source_link_manager-class"></a>source_link_manager – třída

Objekt `source_link_manager` spravuje zprávy blokující síťové odkazy na bloky `ISource`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>Parametry

*_LinkRegistry*<br/>
Registr síťového propojení.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`const_pointer`|Typ, který poskytuje ukazatel na prvek `const` v objektu `source_link_manager`.|
|`const_reference`|Typ, který poskytuje odkaz na `const` prvek uložený v objektu `source_link_manager` pro čtení a provádění operací const.|
|`iterator`|Typ, který poskytuje iterátor, který může číst nebo upravovat libovolný prvek v objektu `source_link_manager`.|
|`type`|Typ registru propojení, který je spravován objektem `source_link_manager`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[source_link_manager](#ctor)|Vytvoří objekt `source_link_manager`.|
|[~ source_link_manager destruktor](#dtor)|Odstraní objekt `source_link_manager`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Přidá zdrojový odkaz na objekt `source_link_manager`.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor na první prvek objektu `source_link_manager`.|
|[zobrazí](#contains)|Vyhledá `network_link_registry` v rámci tohoto objektu `source_link_manager` pro zadaný blok.|
|[count](#count)|Spočítá počet propojených bloků v objektu `source_link_manager`.|
|[odkaz](#reference)|Získá odkaz na objekt `source_link_manager`.|
|[register_target_block](#register_target_block)|Zaregistruje cílový blok, který obsahuje tento objekt `source_link_manager`.|
|[předběžné](#release)|Uvolní odkaz na objekt `source_link_manager`.|
|[remove](#remove)|Odebere propojení z objektu `source_link_manager`.|
|[set_bound](#set_bound)|Nastaví maximální počet zdrojových odkazů, které lze přidat k tomuto objektu `source_link_manager`.|

## <a name="remarks"></a>Poznámky

V současné době jsou zdrojové bloky zjištěny odkazem. Toto je obálka objektu `network_link_registry`, který umožňuje souběžný přístup k odkazům a poskytuje možnost odkazovat na odkazy prostřednictvím zpětných volání. Bloky zpráv (`target_block`s nebo `propagator_block`) by měly tuto třídu používat pro své zdrojové odkazy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`source_link_manager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="add"></a>přidávání

Přidá zdrojový odkaz na objekt `source_link_manager`.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být přidán.

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor na první prvek objektu `source_link_manager`.

```cpp
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek v objektu `source_link_manager`.

### <a name="remarks"></a>Poznámky

Koncový stav iterátoru je označen odkazem `NULL`.

## <a name="contains"></a>zobrazí

Vyhledá `network_link_registry` v rámci tohoto objektu `source_link_manager` pro zadaný blok.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být prohledán v objektu `source_link_manager`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl nalezen zadaný blok, jinak **false** .

## <a name="count"></a>výpočtu

Spočítá počet propojených bloků v objektu `source_link_manager`.

```cpp
size_t count();
```

### <a name="return-value"></a>Návratová hodnota

Počet propojených bloků v objektu `source_link_manager`.

## <a name="reference"></a>odkaz

Získá odkaz na objekt `source_link_manager`.

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

Zaregistruje cílový blok, který obsahuje tento objekt `source_link_manager`.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Cílový blok, který drží tento objekt `source_link_manager`.

## <a name="release"></a>předběžné

Uvolní odkaz na objekt `source_link_manager`.

```cpp
void release();
```

## <a name="remove"></a>odebrány

Odebere propojení z objektu `source_link_manager`.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být odebrán, pokud je nalezen.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl odkaz nalezen a odebrán, jinak **false** .

## <a name="set_bound"></a>set_bound

Nastaví maximální počet zdrojových odkazů, které lze přidat k tomuto objektu `source_link_manager`.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maximální počet odkazů

## <a name="ctor"></a>source_link_manager

Vytvoří objekt `source_link_manager`.

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

Odstraní objekt `source_link_manager`.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[single_link_registry – třída](single-link-registry-class.md)<br/>
[multi_link_registry – třída](multi-link-registry-class.md)
