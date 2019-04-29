---
title: thread – třída
ms.date: 11/04/2016
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.openlocfilehash: d1405062ef553dbfea3b60b5f39e0546707343b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412069"
---
# <a name="thread-class"></a>thread – třída

Definuje objekt, který umožňuje sledovat a spravovat vlákno provádění v rámci aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
class thread;
```

## <a name="remarks"></a>Poznámky

Můžete použít **vlákno** pro sledování a správu vlákna provádění v rámci aplikace. Objekt vlákna, který je vytvořen pomocí výchozího konstruktoru, není přidružen k žádnému vláknu provádění. Objekt vlákna, který byl vytvořen pomocí volatelného objektu, vytváří nové vlákno provádění a volá v něm volatelný objekt. Objekty vláken mohou být přesunuty, ale nemohou být zkopírovány. Proto může být vlákno provádění přidruženo pouze k jednomu objektu vlákna.

Každé vlákno provádění má jedinečný identifikátor typu `thread::id`. Funkce `this_thread::get_id` vrací identifikátor volajícího vlákna. Členská funkce `thread::get_id` vrací identifikátor vlákna, které je objektem vlákna spravováno. Pro objekt vlákna vytvořený s výchozím nastavením vrací metoda `thread::get_id` objekt, který má hodnotu shodnou pro všechny objekty vlákna vytvořené s výchozím nastavením a rozdílnou od hodnoty, která je metodou `this_thread::get_id` vrácena pro jakékoli vlákno provádění, které by mohlo být připojeno v době volání.

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[Thread::ID – třída](#id_class)|Jednoznačně identifikuje přidružené vlákno.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[thread](#thread)|Vytvoří **vlákno** objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Odpojení](#detach)|Odpojí přidružené vlákno od **vlákno** objektu.|
|[get_id](#get_id)|Vrací jedinečný identifikátor přidruženého vlákna.|
|[hardware_concurrency](#hardware_concurrency)|Statické. Vrací odhadovaný počet kontextů hardwarových vláken.|
|[join](#join)|Blokuje, dokud se přidružené vlákno nedokončí.|
|[joinable](#joinable)|Určuje, zda je přidružené vlákno spojitelné.|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač vlákna.|
|[swap](#swap)|Zamění stav objektu se zadaným **vlákno** objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Thread::Operator =](#op_eq)|Přidruží vlákno s aktuálním **vlákno** objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vlákna >

**Namespace:** std

## <a name="detach"></a>  Thread::detach –

Odpojí přidružené vlákno. Operační systém zodpovědná za uvolnění prostředků vlákno na ukončení.

```cpp
void detach();
```

### <a name="remarks"></a>Poznámky

Po volání `detach`, následné volání [get_id –](#get_id) vrátit [id](#id_class).

Pokud není, který je spojen s objektem neúčastnícím se volání vlákno spojitelné, funkce vyvolá [system_error](../standard-library/system-error-class.md) , který má kód chyby `invalid_argument`.

Pokud podproces, který je spojen s objektem neúčastnícím se volání je neplatný, funkce vyvolá `system_error` , který má kód chyby `no_such_process`.

## <a name="get_id"></a>  Thread::get_id –

Vrací jedinečný identifikátor pro přidružené vlákno.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

A [Thread::ID –](#id_class) objekt, který jednoznačně identifikuje přidružené vlákno nebo `thread::id()` Pokud žádné vlákno je přidružený k objektu.

## <a name="hardware_concurrency"></a>  Thread::hardware_concurrency –

Statická metoda, která vrací odhadovaný počet kontextů hardwarových vláken.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odhadovaný počet kontextů hardwarových vláken. Pokud hodnotu nelze vypočítat, nebo není dobře definované, tato metoda vrátí hodnotu 0.

## <a name="id_class"></a>  Thread::ID – třída

Poskytuje jedinečný identifikátor pro každé vlákno provádění v procesu.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který není výsledkem porovnání rovna `thread::id` objektu pro jakékoli existující vlákno.

Všechny vytvořené s výchozím nastavením `thread::id` objekty rovnají.

## <a name="join"></a>  Thread::JOIN –

Blokuje, dokud vlákno provádění, který je spojen s objektem neúčastnícím se volání nedokončí.

```cpp
void join();
```

### <a name="remarks"></a>Poznámky

Pokud bude volání úspěšné, následných volání [get_id –](#get_id) objektem neúčastnícím se volání vrátí výchozí [Thread::ID –](#id_class) , který není výsledkem porovnání `thread::id` existující vlákna; Pokud volání selže , hodnotu, která je vrácena `get_id` se nezmění.

## <a name="joinable"></a>  Thread::joinable –

Určuje, zda je přidružené vlákno *spojitelné*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud přidružené vlákno *spojitelné*; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Objekt vlákna je *spojitelné* Pokud `get_id() != id()`.

## <a name="native_handle"></a>  Thread::native_handle –

Vrátí typ specifický pro implementaci představující popisovač vlákna. Popisovač vlákna je možné způsoby specifický pro implementaci.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type` je definován jako Win32 `HANDLE` , který je typovaná jako `void *`.

## <a name="op_eq"></a>  Thread::Operator =

Přidruží vlákno zadaného objektu aktuálního objektu.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
A **vlákno** objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Volání metody odpojit, pokud je objektem neúčastnícím se volání spojitelné.

Po přidružení `Other` nastavena do stavu vytvořené s výchozím nastavením.

## <a name="swap"></a>  Thread::swap –

Zamění stav objektu s u určeného **vlákno** objektu.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
A **vlákno** objektu.

## <a name="thread"></a>  Thread::Thread – konstruktor

Vytvoří **vlákno** objektu.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*F*<br/>
Aplikacemi definovaná funkce ke spuštění podle vlákna.

*A*<br/>
Seznam argumentů, které mají být předány *F*.

*Jiné*<br/>
Existující **vlákno** objektu.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, který není přidružený k vláknu spuštění. Hodnota vrácená voláním `get_id` vytvořeného objektu je `thread::id()`.

Druhý konstruktor vytvoří objekt, který je spojen s nové vlákno provádění a spustí pseudofunkce `INVOKE` , která je definována v [ \<funkční >](../standard-library/functional.md). Pokud není k dispozici dostatek prostředků je možné vytvořit nové vlákno, funkce vyvolá [system_error](../standard-library/system-error-class.md) objekt, který má kód chyby `resource_unavailable_try_again`. Pokud volání *F* se ukončí se vydá nezachycenou výjimku [ukončit](../standard-library/exception-functions.md#terminate) je volána.

Třetí konstruktor vytvoří objekt, který je spojen s vláknem, který je přidružen `Other`. `Other` je nastaven na stav vytvořené s výchozím nastavením.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<vlákna >](../standard-library/thread.md)<br/>
