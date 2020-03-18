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
ms.openlocfilehash: aef3ae6100133374cb89098f118c447effafd840
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417150"
---
# <a name="critical_section-class"></a>critical_section – třída

Neurčený mutex, který je výslovně informován o Concurrency Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class critical_section;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`native_handle_type`|Odkaz na objekt `critical_section`.|

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[critical_section:: scoped_lock – třída](#critical_section__scoped_lock_class)|Výjimka bezpečná obálka RAII pro objekt `critical_section`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[critical_section](#ctor)|Vytvoří novou kritickou část.|
|[~ critical_section destruktor](#dtor)|Zničí kritickou část.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Získá tuto kritickou část.|
|[native_handle](#native_handle)|Vrátí nativní popisovač specifický pro platformu, pokud existuje.|
|[try_lock](#try_lock)|Pokusí se získat zámek bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat zámek bez blokování určitého počtu milisekund.|
|[Uzamknout](#unlock)|Odemkne oddíl Critical.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Synchronizace datových struktur](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`critical_section`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>critical_section

Vytvoří novou kritickou část.

```cpp
critical_section();
```

## <a name="dtor"></a>~ critical_section

Zničí kritickou část.

```cpp
~critical_section();
```

### <a name="remarks"></a>Poznámky

Očekává se, že zámek již není držen při spuštění destruktoru. Povolení destrukci oddílu s zámkem, který se pořád drží, má za následek nedefinované chování.

## <a name="lock"></a>získáte

Získá tuto kritickou část.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Je často bezpečnější využít [scoped_lock](#critical_section__scoped_lock_class) konstrukce k získání a uvolnění `critical_section` objektu, a to bezpečným způsobem.

Pokud je zámek již držen volajícím kontextem, bude vyvolána výjimka [improper_lock](improper-lock-class.md) .

## <a name="native_handle"></a>native_handle

Vrátí nativní popisovač specifický pro platformu, pokud existuje.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na oddíl Critical.

### <a name="remarks"></a>Poznámky

Objekt `critical_section` není přidružen k nativnímu popisovači specifickému pro platformu pro operační systém Windows. Metoda jednoduše vrátí odkaz na samotný objekt.

## <a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock – třída

Výjimka bezpečná obálka RAII pro objekt `critical_section`.

```cpp
class scoped_lock;
```

## <a name="critical_section__scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Vytvoří objekt `scoped_lock` a získá `critical_section` objekt předaný do parametru `_Critical_section`. Pokud je kritická část držena jiným vláknem, toto volání bude zablokováno.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Oddíl kritické, který se má uzamknout.

## <a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Odstraní objekt `scoped_lock` a uvolní kritickou část poskytnutou v jeho konstruktoru.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a>try_lock

Pokusí se získat zámek bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; v opačném případě hodnota **false**.

## <a name="try_lock_for"></a>try_lock_for

Pokusí se získat zámek bez blokování určitého počtu milisekund.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Počet milisekund, po které se má čekat před vypršením časového limitu

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; v opačném případě hodnota **false**.

## <a name="unlock"></a>Uzamknout

Odemkne oddíl Critical.

```cpp
void unlock();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[reader_writer_lock – třída](reader-writer-lock-class.md)
