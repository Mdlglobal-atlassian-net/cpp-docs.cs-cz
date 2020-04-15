---
title: reader_writer_lock – třída
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376245"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock – třída

Zámek pro zápisdo fronty a zapisovače předvoleb pro zápis do fronty s místním pouze předení. Zámek uděluje první in - první ven (FIFO) přístup k zapisovače a hladovění čtenáři pod nepřetržité zatížení zapisovače.

## <a name="syntax"></a>Syntaxe

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Name (Název)|Popis|
|----------|-----------------|
|[reader_writer_lock::scoped_lock třída](#scoped_lock_class)|Výjimka bezpečné RAII obálka, která `reader_writer_lock` může být použita k získání objektů zámku jako zapisovač.|
|[reader_writer_lock::scoped_lock_read třída](#scoped_lock_read_class)|Výjimka bezpečné RAII obálka, která `reader_writer_lock` může být použita k získání objektů zámku jako čtečka.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Vytvoří nový `reader_writer_lock` objekt.|
|[~reader_writer_lock Destruktor](#dtor)|Zničí `reader_writer_lock` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zámek](#lock)|Získá zámek reader-writer jako zapisovač.|
|[lock_read](#lock_read)|Získá zámek čtečky a zapisovače jako čtenář. Pokud existují spisovatelé, aktivní čtenáři musí počkat, až budou hotovi. Čtenář jednoduše zaregistruje zájem o zámek a čeká na autory, aby jej vydali.|
|[try_lock](#try_lock)|Pokusí se získat zámek pro zápis čtenáře jako zapisovač bez blokování.|
|[try_lock_read](#try_lock_read)|Pokusí se získat zámek pro zápis čtenáře jako čtečku bez blokování.|
|[Odemknout](#unlock)|Odemkne zámek čtečky a zapisovače podle toho, kdo jej uzamkl, čtečku nebo zapisovač.|

## <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Synchronizační datové struktury](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`reader_writer_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Obor názvů:** souběžnost

## <a name="lock"></a><a name="lock"></a>Zámek

Získá zámek reader-writer jako zapisovač.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Je často bezpečnější využít [scoped_lock](#scoped_lock_class) konstrukce získat `reader_writer_lock` a uvolnit objekt jako zapisovač e-mailem v bezpečném způsobem výjimky.

Poté, co se zapisovatel pokusí získat zámek, všechny budoucí čtenáři budou blokovat, dokud autoři úspěšně získali a neuvolnili zámek. Tento zámek je zaujatý vůči spisovatelům a může hladovět čtenáře pod nepřetržitým zatížením spisovatelů.

Zapisovače jsou zřetězené tak, aby zapisovač ukončení zámku uvolní další zapisovač v řádku.

Pokud zámek je již v držení kontextu volání, improper_lock [výjimka](improper-lock-class.md) bude vyvolána.

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Získá zámek čtečky a zapisovače jako čtenář. Pokud existují spisovatelé, aktivní čtenáři musí počkat, až budou hotovi. Čtenář jednoduše zaregistruje zájem o zámek a čeká na autory, aby jej vydali.

```cpp
void lock_read();
```

### <a name="remarks"></a>Poznámky

Je často bezpečnější využít [scoped_lock_read](#scoped_lock_read_class) konstrukce získat `reader_writer_lock` a uvolnit objekt jako čtenář v výjimky bezpečným způsobem.

Pokud existují autoři čekají na zámek, bude čtenář čekat, dokud všechny autory v řádku získali a uvolní zámek. Tento zámek je zaujatý vůči spisovatelům a může hladovět čtenáře pod nepřetržitým zatížením spisovatelů.

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

Vytvoří nový `reader_writer_lock` objekt.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>~reader_writer_lock

Zničí `reader_writer_lock` objekt.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Poznámky

Očekává se, že zámek již není držen při spuštění destruktoru. Povolení zámek zapisovače čtečky zničit se zámkem stále držené výsledky v nedefinované chování.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock::scoped_lock třída

Výjimka bezpečné RAII obálka, která `reader_writer_lock` může být použita k získání objektů zámku jako zapisovač.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock

Vytvoří `scoped_lock` objekt a získá `reader_writer_lock` objekt předaný v parametru `_Reader_writer_lock` jako zapisovatel. Pokud je zámek držen jiným vláknem, toto volání bude blokovat.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
Objekt `reader_writer_lock` získat jako zapisovatel.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock::~scoped_lock

Zničí `reader_writer_lock` objekt a uvolní zámek dodaný v jeho konstruktoru.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock::scoped_lock_read třída

Výjimka bezpečné RAII obálka, která `reader_writer_lock` může být použita k získání objektů zámku jako čtečka.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read

Vytvoří `scoped_lock_read` objekt a získá `reader_writer_lock` objekt předaný v parametru `_Reader_writer_lock` jako čtenář. Pokud zámek je držen jiným vláknem jako zapisovač nebo jsou čekající autoři, toto volání bude blokovat.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
Objekt `reader_writer_lock` získat jako čtenář.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock::scoped_lock_read:~scoped_lock_read Destruktor

Zničí `scoped_lock_read` objekt a uvolní zámek dodaný v jeho konstruktoru.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Pokusí se získat zámek pro zápis čtenáře jako zapisovač bez blokování.

### <a name="syntax"></a>Syntaxe

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; jinak hodnota **false**.

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Pokusí se získat zámek pro zápis čtenáře jako čtečku bez blokování.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; jinak hodnota **false**.

## <a name="unlock"></a><a name="unlock"></a>Odemknout

Odemkne zámek čtečky a zapisovače podle toho, kdo jej uzamkl, čtečku nebo zapisovač.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud jsou autoři čekají na zámek, uvolnění zámku bude vždy přejít na další zapisovač v pořadí FIFO. Tento zámek je zaujatý vůči spisovatelům a může hladovět čtenáře pod nepřetržitým zatížením spisovatelů.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[critical_section – třída](critical-section-class.md)
