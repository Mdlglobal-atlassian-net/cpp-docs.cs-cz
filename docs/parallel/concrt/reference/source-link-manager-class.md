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
ms.openlocfilehash: d4979eaf9065183be646be72cfdd5a94500edf55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337580"
---
# <a name="sourcelinkmanager-class"></a>source_link_manager – třída

`source_link_manager` Objekt spravuje zasílání zpráv bloku síťová propojení k `ISource` bloky.

## <a name="syntax"></a>Syntaxe

```
template<class _LinkRegistry>
class source_link_manager;
```

#### <a name="parameters"></a>Parametry

*_LinkRegistry*<br/>
Síťového propojení registru.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`const_pointer`|Typ, který poskytuje ukazatel na `const` prvek `source_link_manager` objektu.|
|`const_reference`|Typ, který poskytuje odkaz na `const` element uložené v `source_link_manager` objekt pro čtení a provádění operací const.|
|`iterator`|Typ, který poskytuje iterátor, který může číst nebo upravovat libovolný prvek v `source_link_manager` objektu.|
|`type`|Typ odkazu registru spravovaných `source_link_manager` objektu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[source_link_manager](#ctor)|Vytvoří `source_link_manager` objektu.|
|[~source_link_manager Destructor](#dtor)|Odstraní `source_link_manager` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add](#add)|Přidá odkaz na zdroj `source_link_manager` objektu.|
|[začít](#begin)|Vrátí iterátor na první prvek `source_link_manager` objektu.|
|[Obsahuje](#contains)|Hledání `network_link_registry` v rámci této `source_link_manager` objekt pro zadaný blok.|
|[Počet](#count)|Spočítá počet propojených bloky v `source_link_manager` objektu.|
|[Referenční dokumentace](#reference)|Získá odkaz na `source_link_manager` objektu.|
|[register_target_block](#register_target_block)|Zaregistruje cílový blok, který obsahuje tato `source_link_manager` objektu.|
|[Vydání verze](#release)|Verze odkazu na `source_link_manager` objektu.|
|[remove](#remove)|Odebere odkaz `source_link_manager` objektu.|
|[set_bound](#set_bound)|Nastaví maximální počet odkazů zdroje, které mohou být přidány do tohoto `source_link_manager` objektu.|

## <a name="remarks"></a>Poznámky

V současné době zdrojových bloků je počítáno referenčně. Toto je obálka na `network_link_registry` objekt, který umožňuje souběžný přístup k odkazy a umožňuje odkazovat na odkazy pomocí zpětných volání. Zpráva bloky ( `target_block`s nebo `propagator_block`s) by měla tuto třídu použít odkazy na jejich zdroj.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`source_link_manager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="add"></a> Přidat

Přidá odkaz na zdroj `source_link_manager` objektu.

```
void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který chcete přidat.

##  <a name="begin"></a> začít

Vrátí iterátor na první prvek `source_link_manager` objektu.

```
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první prvek `source_link_manager` objektu.

### <a name="remarks"></a>Poznámky

Je indikován stav koncový iterátor `NULL` odkaz.

##  <a name="contains"></a> Obsahuje

Hledání `network_link_registry` v rámci této `source_link_manager` objekt pro zadaný blok.

```
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který má být vyhledán v `source_link_manager` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud byl nalezen zadaný blok, **false** jinak.

##  <a name="count"></a> Počet

Spočítá počet propojených bloky v `source_link_manager` objektu.

```
size_t count();
```

### <a name="return-value"></a>Návratová hodnota

Počet propojených bloků v `source_link_manager` objektu.

##  <a name="reference"></a> Referenční dokumentace

Získá odkaz na `source_link_manager` objektu.

```
void reference();
```

##  <a name="register_target_block"></a> register_target_block

Zaregistruje cílový blok, který obsahuje tato `source_link_manager` objektu.

```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Cílový blok uchovávající to `source_link_manager` objektu.

##  <a name="release"></a> Vydání verze

Verze odkazu na `source_link_manager` objektu.

```
void release();
```

##  <a name="remove"></a> odebrat

Odebere odkaz `source_link_manager` objektu.

```
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Propojit*<br/>
Ukazatele na blok, který se odeberou, pokud se nenašel.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud odkazu byl nalezen a odebrání **false** jinak.

##  <a name="set_bound"></a> set_bound –

Nastaví maximální počet odkazů zdroje, které mohou být přidány do tohoto `source_link_manager` objektu.

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maximální počet odkazů.

##  <a name="ctor"></a> source_link_manager –

Vytvoří `source_link_manager` objektu.

```
source_link_manager();
```

##  <a name="dtor"></a> ~source_link_manager

Odstraní `source_link_manager` objektu.

```
~source_link_manager();
```

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[single_link_registry – třída](single-link-registry-class.md)<br/>
[multi_link_registry – třída](multi-link-registry-class.md)
