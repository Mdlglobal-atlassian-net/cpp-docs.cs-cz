---
title: critical_section – třída
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: 24f96282a7728c6db6e0b05d36406f15383913f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372682"
---
# <a name="critical_section-class"></a>critical_section – třída

Mutex bez reentrant, který je explicitně vědom runtime souběžnosti.

## <a name="syntax"></a>Syntaxe

```cpp
class critical_section;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`native_handle_type`|Odkaz na `critical_section` objekt.|

### <a name="public-classes"></a>Veřejné třídy

|Name (Název)|Popis|
|----------|-----------------|
|[critical_section::scoped_lock třída](#critical_section__scoped_lock_class)|Výjimka bezpečné RAII obálka `critical_section` pro objekt.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[critical_section](#ctor)|Vytvoří nový kritický oddíl.|
|[~critical_section Destruktor](#dtor)|Zničí kritickou část.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zámek](#lock)|Získá tento kritický oddíl.|
|[native_handle](#native_handle)|Vrátí nativní popisovač specifický pro platformu, pokud existuje.|
|[try_lock](#try_lock)|Pokusí se získat zámek bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat zámek bez blokování pro určitý počet milisekund.|
|[Odemknout](#unlock)|Odemkne kritickou část.|

## <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Synchronizační datové struktury](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`critical_section`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Obor názvů:** souběžnost

## <a name="critical_section"></a><a name="ctor"></a>critical_section

Vytvoří nový kritický oddíl.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>~critical_section

Zničí kritickou část.

```cpp
~critical_section();
```

### <a name="remarks"></a>Poznámky

Očekává se, že zámek již není držen při spuštění destruktoru. Povolení kritické části zničit s zámek stále držené výsledky v nedefinované chování.

## <a name="lock"></a><a name="lock"></a>Zámek

Získá tento kritický oddíl.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Často je bezpečnější využít [scoped_lock](#critical_section__scoped_lock_class) konstrukce k `critical_section` získání a uvolnění objektu bezpečným způsobem.

Pokud zámek je již v držení kontextu volání, improper_lock [výjimka](improper-lock-class.md) bude vyvolána.

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Vrátí nativní popisovač specifický pro platformu, pokud existuje.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na kritický oddíl.

### <a name="remarks"></a>Poznámky

Objekt `critical_section` není přidružen k nativnímu popisovaču specifické pro platformu pro operační systém Windows. Metoda jednoduše vrátí odkaz na samotný objekt.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section::scoped_lock třída

Výjimka bezpečné RAII obálka `critical_section` pro objekt.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock

Vytvoří `scoped_lock` objekt a získá `critical_section` objekt předaný v parametru. `_Critical_section` Pokud je kritický oddíl držen jiným vláknem, toto volání bude blokovat.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Kritický oddíl, který chcete zamknout.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock::~scoped_lock

Zničí `scoped_lock` objekt a uvolní kritický oddíl dodaný v jeho konstruktoru.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Pokusí se získat zámek bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; jinak hodnota **false**.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Pokusí se získat zámek bez blokování pro určitý počet milisekund.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Počet milisekund čekání před vypršením časového limitu.

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; jinak hodnota **false**.

## <a name="unlock"></a><a name="unlock"></a>Odemknout

Odemkne kritickou část.

```cpp
void unlock();
```

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[reader_writer_lock třída](reader-writer-lock-class.md)
