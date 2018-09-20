---
title: reader_writer_lock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c319ba90a92ac534f4444960ff1e6e6d27acb180
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390181"
---
# <a name="readerwriterlock-class"></a>reader_writer_lock – třída

Zapisovač předvoleb zámek na základě fronty čtení a zápis s místní pouze na otáčejících se. Zámek pro autory uděluje nejprve – první out (FIFO) přístup a nepřetržitě, ubírá čtenáři průběžné zatížení zapisovačů.

## <a name="syntax"></a>Syntaxe

```
class reader_writer_lock;
```

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[reader_writer_lock::scoped_lock – třída](#scoped_lock_class)|Výjimka bezpečné Obálka RAII, který slouží k získání `reader_writer_lock` zamknutí objektů jako zapisovač.|
|[reader_writer_lock::scoped_lock_read – třída](#scoped_lock_read_class)|Výjimka bezpečné Obálka RAII, který slouží k získání `reader_writer_lock` zamknutí objektů jako čtečku.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Sestaví nový `reader_writer_lock` objektu.|
|[~reader_writer_lock Destructor](#dtor)|Odstraní `reader_writer_lock` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Získá zámek pro čtení a zápis jako zapisovač.|
|[lock_read](#lock_read)|Získá zámek pro čtení a zápis pro čtenáře. Pokud jsou uživatelé vytvářející obsah, aktivní čtenáři mají čekat, dokud to je všechno. Čtečka jednoduše zaregistruje zájmu o zámek a čeká zapisovače pro uvolnění.|
|[try_lock](#try_lock)|Pokusí se získat zámek pro čtení a zápis jako zapisovač bez blokování.|
|[try_lock_read](#try_lock_read)|Pokusí se získat zámek pro čtení a zápis pro čtenáře bez blokování.|
|[Odemknutí](#unlock)|Odemkne uzamčení čtení a zápis, podle který uzamčen, čtečky nebo zapisovače.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [synchronizačních datových struktur](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`reader_writer_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="lock"></a> Zámek

Získá zámek pro čtení a zápis jako zapisovač.

```
void lock();
```

### <a name="remarks"></a>Poznámky

Často je bezpečnější používat [scoped_lock](#scoped_lock_class) konstrukce pro získání a uvolnění `reader_writer_lock` objektu jako zapisovač výjimku bezpečným způsobem.

Po zapisovač se pokouší získat zámek, všechny budoucí čtenáři bude blokovat, dokud zapisovače mít úspěšné se načetl a vydání zámek. Tohoto uzamknout tendenční směrem k uživatelé vytvářející obsah a může zhoršit výkon čtenáři průběžné zatížení zapisovačů.

Uživatelé vytvářející obsah jsou zřetězeny tak, aby zapisovač ukončení uzamčení uvolní zapisovač dalším řádku.

Pokud volání kontextu již drží zámek [improper_lock –](improper-lock-class.md) , bude vyvolána výjimka.

##  <a name="lock_read"></a> lock_read –

Získá zámek pro čtení a zápis pro čtenáře. Pokud jsou uživatelé vytvářející obsah, aktivní čtenáři mají čekat, dokud to je všechno. Čtečka jednoduše zaregistruje zájmu o zámek a čeká zapisovače pro uvolnění.

```
void lock_read();
```

### <a name="remarks"></a>Poznámky

Často je bezpečnější používat [scoped_lock_read –](#scoped_lock_read_class) konstrukce pro získání a uvolnění `reader_writer_lock` objektu jako čtečku výjimku bezpečným způsobem.

Pokud jsou uživatelé vytvářející obsah čekání na zámek, čtečky počká, až všechny zapisovače řádku mají získat a vydání zámek. Tohoto uzamknout tendenční směrem k uživatelé vytvářející obsah a může zhoršit výkon čtenáři průběžné zatížení zapisovačů.

##  <a name="ctor"></a> reader_writer_lock –

Sestaví nový `reader_writer_lock` objektu.

```
reader_writer_lock();
```

##  <a name="dtor"></a> ~ reader_writer_lock –

Odstraní `reader_writer_lock` objektu.

```
~reader_writer_lock();
```

### <a name="remarks"></a>Poznámky

Očekává se, že zámek už mezipaměť není při spuštění destruktoru. Povolení zapisovací zámek čtecího zařízení k destrukci s uzamčením stále uchovávat výsledky nedefinované chování.

##  <a name="scoped_lock_class"></a>  reader_writer_lock::scoped_lock – třída

Výjimka bezpečné Obálka RAII, který slouží k získání `reader_writer_lock` zamknutí objektů jako zapisovač.

```
class scoped_lock;
```
## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock

Vytvoří `scoped_lock` objektu a získá `reader_writer_lock` předaný objekt `_Reader_writer_lock` parametr jako zapisovač. Pokud jiné vlákno drží zámek, zablokuje se toto volání.

```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

#### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
`reader_writer_lock` Objektu získat jako zapisovač.

## <a name="scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

Odstraní `reader_writer_lock` objektu a uvolní zámek zadaný v konstruktoru.

```
~scoped_lock();
```

##  <a name="scoped_lock_read_class"></a>  reader_writer_lock::scoped_lock_read – třída

Výjimka bezpečné Obálka RAII, který slouží k získání `reader_writer_lock` zamknutí objektů jako čtečku.

```
class scoped_lock_read;
```

##  <a name="try_lock"></a> try_lock –

Pokusí se získat zámek pro čtení a zápis jako zapisovač bez blokování.

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read

Vytvoří `scoped_lock_read` objektu a získá `reader_writer_lock` předaný objekt `_Reader_writer_lock` parametr jako čtečku. Pokud zámek je načtený v jiném vlákně jako zapisovač nebo existují čekající zapisovačů, zablokuje se toto volání.

```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

#### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
`reader_writer_lock` Objektu získat jako čtečku.

## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock::scoped_lock_read:: ~ scoped_lock_read – destruktor

Odstraní `scoped_lock_read` objektu a uvolní zámek zadaný v konstruktoru.

```
~scoped_lock_read();
```

## <a name="try_lock"></a> try_lock –

```
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl získán zámek, hodnota `true`; v opačném případě hodnota `false`.

##  <a name="try_lock_read"></a> try_lock_read –

Pokusí se získat zámek pro čtení a zápis pro čtenáře bez blokování.

```
bool try_lock_read();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl získán zámek, hodnota `true`; v opačném případě hodnota `false`.

##  <a name="unlock"></a> Odemknutí

Odemkne uzamčení čtení a zápis, podle který uzamčen, čtečky nebo zapisovače.

```
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud existují uživatelé vytvářející obsah čekání na zámek, uvolnění zámku vždy použít další zápis v pořadí FIFO. Tohoto uzamknout tendenční směrem k uživatelé vytvářející obsah a může zhoršit výkon čtenáři průběžné zatížení zapisovačů.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[critical_section – třída](critical-section-class.md)
