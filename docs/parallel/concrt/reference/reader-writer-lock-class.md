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
ms.openlocfilehash: 1a7386e527b5327d928bfdcb3281c88666f1b106
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140854"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock – třída

Zámek zapisovače založený na frontě pro zapisovače, který se zakládá jenom s místním odstřeďováním Zámek uděluje při průběžném načítání zapisovačů přístup FIFO k modulům pro zápis a starves.

## <a name="syntax"></a>Syntaxe

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[reader_writer_lock:: scoped_lock – třída](#scoped_lock_class)|Bezpečnostní obálka RAII, která se dá použít k získání `reader_writer_lock` objektů zámku jako zapisovače.|
|[reader_writer_lock:: scoped_lock_read – třída](#scoped_lock_read_class)|Bezpečnostní obálka RAII, která se dá použít k získání `reader_writer_lock` objektů zámku jako čtecího zařízení.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Vytvoří nový objekt `reader_writer_lock`.|
|[~ reader_writer_lock destruktor](#dtor)|Odstraní objekt `reader_writer_lock`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Získá zámek zapisovače čtenářů jako zapisovače.|
|[lock_read](#lock_read)|Získá zámek zapisovače pro čtení a čtení. Pokud existují moduly pro zápis, musí aktivní čtenáři počkat, než se dokončí. Čtecí modul jednoduše zaregistruje zájem v zámku a počká, až ho zapisovač vypustí.|
|[try_lock](#try_lock)|Pokusí se získat zámek zapisovače pro čtení ve formě zapisovače bez blokování.|
|[try_lock_read](#try_lock_read)|Pokusí se získat zámek zapisovače pro čtení ve formě čtecího modulu bez blokování.|
|[Uzamknout](#unlock)|Odemkne zámek zapisovače pro čtení na základě toho, kdo ho uzamkl, čtenář nebo zapisovač.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Synchronizace datových struktur](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`reader_writer_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="lock"></a>získáte

Získá zámek zapisovače čtenářů jako zapisovače.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Je často bezpečnější využít [scoped_lock](#scoped_lock_class) konstrukce k získání a uvolnění `reader_writer_lock` objektu jako zapisovače bezpečným způsobem.

Jakmile se zapisovač pokusí získat zámek, všechna budoucí čtenáři budou blokovat až do úspěšného získání a uvolnění zámku. Tento zámek se posune k modulům pro zápis a může omezují čtenáři za průběžné načítání zapisovačů.

Moduly pro zápis jsou zřetězené tak, že zapisovač ukončí zámek uvolnění dalšího zapisovače na řádku.

Pokud je zámek již držen volajícím kontextem, bude vyvolána výjimka [improper_lock](improper-lock-class.md) .

## <a name="lock_read"></a>lock_read

Získá zámek zapisovače pro čtení a čtení. Pokud existují moduly pro zápis, musí aktivní čtenáři počkat, než se dokončí. Čtecí modul jednoduše zaregistruje zájem v zámku a počká, až ho zapisovač vypustí.

```cpp
void lock_read();
```

### <a name="remarks"></a>Poznámky

Je často bezpečnější využít [scoped_lock_read](#scoped_lock_read_class) konstrukce pro získání a uvolnění `reader_writer_lock`ho objektu jako čtecího zařízení bezpečným způsobem.

Pokud na zámek čekají moduly pro zápis, čtečka počká, dokud všichni autoři na řádku nezískají a neuvolní zámek. Tento zámek se posune k modulům pro zápis a může omezují čtenáři za průběžné načítání zapisovačů.

## <a name="ctor"></a>reader_writer_lock

Vytvoří nový objekt `reader_writer_lock`.

```cpp
reader_writer_lock();
```

## <a name="dtor"></a>~ reader_writer_lock

Odstraní objekt `reader_writer_lock`.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Poznámky

Očekává se, že zámek již není držen při spuštění destruktoru. Díky tomu, aby zámek zapisovače čtenářů destrukci s zámkem, se pořád drží výsledky v nedefinovaném chování.

## <a name="scoped_lock_class"></a>reader_writer_lock:: scoped_lock – třída

Bezpečnostní obálka RAII, která se dá použít k získání `reader_writer_lock` objektů zámku jako zapisovače.

```cpp
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Vytvoří objekt `scoped_lock` a získá `reader_writer_lock` objekt předaný v parametru `_Reader_writer_lock` jako zapisovač. Pokud je zámek držen jiným vláknem, toto volání bude zablokováno.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
Objekt `reader_writer_lock`, který se má načíst jako zapisovač.

## <a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Odstraní objekt `reader_writer_lock` a uvolní zámek dodaný v jeho konstruktoru.

```cpp
~scoped_lock();
```

## <a name="scoped_lock_read_class"></a>reader_writer_lock:: scoped_lock_read – třída

Bezpečnostní obálka RAII, která se dá použít k získání `reader_writer_lock` objektů zámku jako čtecího zařízení.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read:: scoped_lock_read

Vytvoří objekt `scoped_lock_read` a získá `reader_writer_lock` objekt předaný v parametru `_Reader_writer_lock` jako čtecí modul. Pokud je zámek držen jiným vláknem jako modul pro zápis nebo čekají na zapisovače, toto volání bude zablokováno.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
Objekt `reader_writer_lock`, který se má načíst jako čtecí modul.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor"> reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read destruktor

Odstraní objekt `scoped_lock_read` a uvolní zámek dodaný v jeho konstruktoru.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a>try_lock

Pokusí se získat zámek zapisovače pro čtení ve formě zapisovače bez blokování.

### <a name="syntax"></a>Syntaxe

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; v opačném případě hodnota **false**.

## <a name="try_lock_read"></a>try_lock_read

Pokusí se získat zámek zapisovače pro čtení ve formě čtecího modulu bez blokování.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl zámek získán, hodnota **true**; v opačném případě hodnota **false**.

## <a name="unlock"></a>Uzamknout

Odemkne zámek zapisovače pro čtení na základě toho, kdo ho uzamkl, čtenář nebo zapisovač.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud na zámek čekají moduly pro zápis, bude verze zámku vždycky přejít k dalšímu zapisovači v pořadí FIFO. Tento zámek se posune k modulům pro zápis a může omezují čtenáři za průběžné načítání zapisovačů.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[critical_section – třída](critical-section-class.md)
