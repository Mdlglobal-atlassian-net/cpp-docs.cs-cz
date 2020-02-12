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
ms.openlocfilehash: e22df5ee65d0219a46065044385dca46aac297a3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142375"
---
# <a name="multi_link_registry-class"></a>multi_link_registry – třída

Objekt `multi_link_registry` je `network_link_registry`, který spravuje více zdrojových bloků nebo více cílových bloků.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Datový typ Block uložený v objektu `multi_link_registry`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[multi_link_registry](#ctor)|Vytvoří objekt `multi_link_registry`.|
|[~ multi_link_registry destruktor](#dtor)|Odstraní objekt `multi_link_registry`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Přidá odkaz na objekt `multi_link_registry`. (Potlačení [network_link_registry:: Add](network-link-registry-class.md#add).)|
|[ifunctiondiscovery](#begin)|Vrátí iterátor na první prvek objektu `multi_link_registry`. (Overrides [network_link_registry:: begin](network-link-registry-class.md#begin).)|
|[zobrazí](#contains)|Vyhledá zadaný blok v objektu `multi_link_registry`. (Potlačení [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Spočítá počet položek v objektu `multi_link_registry`. (Potlačení [network_link_registry:: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Odebere propojení z objektu `multi_link_registry`. (Potlačení [network_link_registry:: Remove](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Nastaví horní mez počtu odkazů, které může objekt `multi_link_registry` uchovávat.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="add"></a>přidávání

Přidá odkaz na objekt `multi_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být přidán.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_link_target](invalid-link-target-class.md) , je-li odkaz již přítomen v registru, nebo pokud již byla nastavena vazba s funkcí `set_bound` a odkaz byl od odebrání odstraněn.

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor na první prvek objektu `multi_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek v objektu `multi_link_registry`.

### <a name="remarks"></a>Poznámky

Koncový stav je označen odkazem `NULL`.

## <a name="contains"></a>zobrazí

Vyhledá zadaný blok v objektu `multi_link_registry`.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být prohledán v objektu `multi_link_registry`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl nalezen zadaný blok, jinak **false** .

## <a name="count"></a>výpočtu

Spočítá počet položek v objektu `multi_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v objektu `multi_link_registry`.

## <a name="ctor"></a>multi_link_registry

Vytvoří objekt `multi_link_registry`.

```cpp
multi_link_registry();
```

## <a name="dtor"></a>~ multi_link_registry

Odstraní objekt `multi_link_registry`.

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_operation](invalid-operation-class.md) , pokud je volána před odebráním všech propojení.

## <a name="remove"></a>odebrány

Odebere propojení z objektu `multi_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Ukazatel na blok, který má být odebrán, pokud je nalezen.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl odkaz nalezen a odebrán, jinak **false** .

## <a name="set_bound"></a>set_bound

Nastaví horní mez počtu odkazů, které může objekt `multi_link_registry` uchovávat.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maximální počet odkazů, které může objekt `multi_link_registry` uchovávat.

### <a name="remarks"></a>Poznámky

Po nastavení vazby, zrušení propojení položky způsobí, že objekt `multi_link_registry` zadá neměnný stav, kde další volání `add` vyvolá výjimku `invalid_link_target`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[single_link_registry – třída](single-link-registry-class.md)
