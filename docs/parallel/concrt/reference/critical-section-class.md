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
ms.openlocfilehash: f334b159ae39f48006a135c6e36d413b737a7344
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296153"
---
# <a name="criticalsection-class"></a>critical_section – třída

Bez reentrant objektu mutex, na které je explicitně vědoma souběžnosti modulu runtime.

## <a name="syntax"></a>Syntaxe

```
class critical_section;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`native_handle_type`|Odkaz na `critical_section` objektu.|

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[critical_section::scoped_lock Class](#critical_section__scoped_lock_class)|Výjimka Obálka bezpečné RAII pro `critical_section` objektu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[critical_section](#ctor)|Vytvoří nový kritický oddíl.|
|[~ critical_section – destruktor](#dtor)|Zničí kritický oddíl.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Získá tento kritický oddíl.|
|[native_handle](#native_handle)|Pokud takové existuje, vrátí platformu konkrétní nativní popisovač.|
|[try_lock](#try_lock)|Pokusí se získat zámek bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat zámek bez blokování pro určitý počet milisekund.|
|[unlock](#unlock)|Odemkne důležité části.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [synchronizačních datových struktur](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`critical_section`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> critical_section –

Vytvoří nový kritický oddíl.

```
critical_section();
```

##  <a name="dtor"></a> ~ critical_section –

Zničí kritický oddíl.

```
~critical_section();
```

### <a name="remarks"></a>Poznámky

Očekává se, že zámek už mezipaměť není při spuštění destruktoru. Povolení kritický oddíl k destrukci s uzamčením stále uchovávat výsledky nedefinované chování.

##  <a name="lock"></a> Zámek

Získá tento kritický oddíl.

```
void lock();
```

### <a name="remarks"></a>Poznámky

Často je bezpečnější používat [scoped_lock](#critical_section__scoped_lock_class) konstrukce pro získání a uvolnění `critical_section` objektu v výjimku bezpečným způsobem.

Pokud volání kontextu již drží zámek [improper_lock –](improper-lock-class.md) , bude vyvolána výjimka.

##  <a name="native_handle"></a> native_handle –

Pokud takové existuje, vrátí platformu konkrétní nativní popisovač.

```
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na kritický oddíl.

### <a name="remarks"></a>Poznámky

A `critical_section` objektu není přidružen k platformě konkrétní nativní popisovač pro operační systém Windows. Metoda jednoduše vrací odkaz na objekt samotný.

##  <a name="critical_section__scoped_lock_class"></a>  critical_section::scoped_lock – třída

Výjimka Obálka bezpečné RAII pro `critical_section` objektu.

```
class scoped_lock;
```

##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock

Vytvoří `scoped_lock` objektu a získá `critical_section` objekt předaný `_Critical_section` parametr. Pokud je kritický oddíl načtený v jiném vlákně, zablokuje se toto volání.

```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Kritická sekce uzamknout.

##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock::~scoped_lock

Odstraní `scoped_lock` objektu a uvolní kritický oddíl zadaný v konstruktoru.

```
~scoped_lock();
```

##  <a name="try_lock"></a> try_lock –

Pokusí se získat zámek bez blokování.

```
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

Pokud byl získán zámek, hodnota **true**; v opačném případě hodnota **false**.

##  <a name="try_lock_for"></a> try_lock_for –

Pokusí se získat zámek bez blokování pro určitý počet milisekund.

```
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Vypršení časového limitu*<br/>
Počet milisekund čekání před vypršením časového limitu.

### <a name="return-value"></a>Návratová hodnota

Pokud byl získán zámek, hodnota **true**; v opačném případě hodnota **false**.

##  <a name="unlock"></a> Odemknutí

Odemkne důležité části.

```
void unlock();
```

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[reader_writer_lock – třída](reader-writer-lock-class.md)
