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
ms.openlocfilehash: 13996a8ec4ab56fc56a78606d1a2ce8d76994c0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375859"
---
# <a name="thread-class"></a>thread – třída

Definuje objekt, který umožňuje sledovat a spravovat vlákno provádění v rámci aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
class thread;
```

## <a name="remarks"></a>Poznámky

Objekt **podprocesu** můžete použít ke sledování a správě podprocesu spuštění v rámci aplikace. Objekt vlákna, který je vytvořen pomocí výchozího konstruktoru, není přidružen k žádnému vláknu provádění. Objekt vlákna, který byl vytvořen pomocí volatelného objektu, vytváří nové vlákno provádění a volá v něm volatelný objekt. Objekty vláken mohou být přesunuty, ale nemohou být zkopírovány. Proto může být vlákno provádění přidruženo pouze k jednomu objektu vlákna.

Každé vlákno provádění má jedinečný identifikátor typu `thread::id`. Funkce `this_thread::get_id` vrací identifikátor volajícího vlákna. Členská funkce `thread::get_id` vrací identifikátor vlákna, které je objektem vlákna spravováno. Pro objekt vlákna vytvořený s výchozím nastavením vrací metoda `thread::get_id` objekt, který má hodnotu shodnou pro všechny objekty vlákna vytvořené s výchozím nastavením a rozdílnou od hodnoty, která je metodou `this_thread::get_id` vrácena pro jakékoli vlákno provádění, které by mohlo být připojeno v době volání.

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Name (Název)|Popis|
|----------|-----------------|
|[vlákno::třída id](#id_class)|Jednoznačně identifikuje přidružené vlákno.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[vlákno](#thread)|Vytvoří objekt **vlákna.**|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Odpojit](#detach)|Odpojí přidružené vlákno od objektu **vlákna.**|
|[get_id](#get_id)|Vrací jedinečný identifikátor přidruženého vlákna.|
|[hardware_concurrency](#hardware_concurrency)|Statická. Vrací odhadovaný počet kontextů hardwarových vláken.|
|[Připojit](#join)|Blokuje, dokud se přidružené vlákno nedokončí.|
|[připojitelné](#joinable)|Určuje, zda je přidružené vlákno spojitelné.|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač vlákna.|
|[Swap](#swap)|Zamění stav objektu zadaným objektem **vlákna.**|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[vlákno::operátor=](#op_eq)|Přidruží vlákno k aktuálnímu objektu **vlákna.**|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> vláken

**Obor názvů:** std

## <a name="threaddetach"></a><a name="detach"></a>vlákno::detach

Odpojí přidružený podproces. Operační systém se stane zodpovědný za uvolnění prostředků vlákna na ukončení.

```cpp
void detach();
```

### <a name="remarks"></a>Poznámky

Po volání `detach`na , následné volání [get_id](#get_id) [id](#id_class)vrácení .

Pokud vlákno, které je přidruženo k volajícímu objektu, není spojitelné, funkce `invalid_argument`vyvolá [system_error,](../standard-library/system-error-class.md) který má kód chyby aplikace .

Pokud podproces, který je přidružen k volající objekt je `system_error` neplatný, funkce `no_such_process`vyvolá, který má kód chyby .

## <a name="threadget_id"></a><a name="get_id"></a>vlákno::get_id

Vrátí jedinečný identifikátor pro přidružené vlákno.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

A [thread::id](#id_class) objekt, který jednoznačně identifikuje `thread::id()` přidružené vlákno, nebo pokud žádné vlákno je přidružen k objektu.

## <a name="threadhardware_concurrency"></a><a name="hardware_concurrency"></a>vlákno::hardware_concurrency

Statická metoda, která vrací odhad počtu kontextů hardwarového vlákna.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odhad počtu kontextů hardwarového vlákna. Pokud hodnotu nelze vypočítat nebo není dobře definována, vrátí tato metoda hodnotu 0.

## <a name="threadid-class"></a><a name="id_class"></a>vlákno::třída id

Poskytuje jedinečný identifikátor pro každé vlákno provádění v procesu.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který neporovnává `thread::id` rovný objektu pro existující vlákno.

Všechny výchozí konstruované objekty `thread::id` porovnat stejné.

## <a name="threadjoin"></a><a name="join"></a>vlákno::spojení

Bloky, dokud vlákno spuštění, který je spojen s volající objekt dokončí.

```cpp
void join();
```

### <a name="remarks"></a>Poznámky

Pokud je volání úspěšné, následné volání [get_id](#get_id) volajícího objektu vrátí výchozí [vlákno::id,](#id_class) které se nevyrovná existujícímu `thread::id` vláknu; Pokud volání neproběhne úspěšně, hodnota, `get_id` která je vrácena, se nezmění.

## <a name="threadjoinable"></a><a name="joinable"></a>vlákno::spojitelné

Určuje, zda je přidružené vlákno *spojitelné*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je přidružené vlákno *spojitelné*; jinak **false**.

### <a name="remarks"></a>Poznámky

Objekt vlákna je `get_id() != id()` *spojitelný,* pokud .

## <a name="threadnative_handle"></a><a name="native_handle"></a>vlákno::native_handle

Vrátí typ specifický pro implementaci představující popisovač vlákna. Popisovač podprocesu lze použít v konkrétních způsobech implementace.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type`je definována jako `HANDLE` Win32, `void *`který je obsazení jako .

## <a name="threadoperator"></a><a name="op_eq"></a>vlákno::operátor=

Přidruží vlákno zadaného objektu k aktuálnímu objektu.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt **vlákna.**

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Metoda volá odpojení, pokud je volající objekt připojitelný.

Po přidružení `Other` je nastavena na výchozí stav konstrukce.

## <a name="threadswap"></a><a name="swap"></a>vlákno::swap

Zamění stav objektu zadaný objekt **vlákna.**

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt **vlákna.**

## <a name="threadthread-constructor"></a><a name="thread"></a>vlákno:konstruktor vláken

Vytvoří objekt **vlákna.**

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*F*\
Funkce definovaná aplikací, která má být spuštěna podprocesem.

*A*\
Seznam argumentů, které mají být předány *F*.

*Další*\
Existující objekt **podprocesu.**

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, který není spojen s podprocesem provádění. Hodnota, která je vrácena `get_id` volání pro vytvořený `thread::id()`objekt je .

Druhý konstruktor vytvoří objekt, který je přidružen k nové vlákno provádění a `INVOKE` provede pseudo-funkce, která je definována ve [ \<funkční>](../standard-library/functional.md). Pokud není k dispozici dostatek prostředků pro spuštění nového vlákna, funkce `resource_unavailable_try_again`vyvolá [system_error](../standard-library/system-error-class.md) objekt, který má kód chyby . Pokud volání *F* ukončí s uncaught výjimku, [terminate](../standard-library/exception-functions.md#terminate) je volána.

Třetí konstruktor vytvoří objekt, který je přidružen k podprocesu, který je přidružen . `Other` `Other`je pak nastavena na výchozí stav konstrukce.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>vláken](../standard-library/thread.md)
