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
ms.openlocfilehash: f663034cdc7985dd440a1cdfdd659358c4e250f4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458576"
---
# <a name="thread-class"></a>thread – třída

Definuje objekt, který umožňuje sledovat a spravovat vlákno provádění v rámci aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
class thread;
```

## <a name="remarks"></a>Poznámky

Můžete použít objekt **vlákna** ke sledování a správě vlákna provádění v rámci aplikace. Objekt vlákna, který je vytvořen pomocí výchozího konstruktoru, není přidružen k žádnému vláknu provádění. Objekt vlákna, který byl vytvořen pomocí volatelného objektu, vytváří nové vlákno provádění a volá v něm volatelný objekt. Objekty vláken mohou být přesunuty, ale nemohou být zkopírovány. Proto může být vlákno provádění přidruženo pouze k jednomu objektu vlákna.

Každé vlákno provádění má jedinečný identifikátor typu `thread::id`. Funkce `this_thread::get_id` vrací identifikátor volajícího vlákna. Členská funkce `thread::get_id` vrací identifikátor vlákna, které je objektem vlákna spravováno. Pro objekt vlákna vytvořený s výchozím nastavením vrací metoda `thread::get_id` objekt, který má hodnotu shodnou pro všechny objekty vlákna vytvořené s výchozím nastavením a rozdílnou od hodnoty, která je metodou `this_thread::get_id` vrácena pro jakékoli vlákno provádění, které by mohlo být připojeno v době volání.

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Name|Popis|
|----------|-----------------|
|[Thread:: ID – třída](#id_class)|Jednoznačně identifikuje přidružené vlákno.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[thread](#thread)|Vytvoří objekt **vlákna** .|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[dělitel](#detach)|Odpojí přidružené vlákno od objektu **vlákna** .|
|[get_id](#get_id)|Vrací jedinečný identifikátor přidruženého vlákna.|
|[hardware_concurrency](#hardware_concurrency)|Tras. Vrací odhadovaný počet kontextů hardwarových vláken.|
|[join](#join)|Blokuje, dokud se přidružené vlákno nedokončí.|
|[joinable](#joinable)|Určuje, zda je přidružené vlákno spojitelné.|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač vlákna.|
|[swap](#swap)|Zamění stav objektu pomocí zadaného objektu **vlákna** .|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[Thread:: operator =](#op_eq)|Přidruží vlákno k aktuálnímu objektu **vlákna** .|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> vlákna

**Obor názvů:** std

## <a name="detach"></a>vlákno::d etach

Odpojí přidružené vlákno. Operační systém se bude zodpovědná za uvolnění prostředků vlákna při ukončení.

```cpp
void detach();
```

### <a name="remarks"></a>Poznámky

Po volání `detach`, následné volání [get_id](#get_id) návratového [ID](#id_class).

Pokud vlákno, které je přidruženo k volajícímu objektu, není spojeno, funkce vyvolá [system_error](../standard-library/system-error-class.md) s kódem `invalid_argument`chyby.

Pokud je vlákno přidružené k volajícímu objektu neplatné, funkce vyvolá výjimku `system_error` , která má `no_such_process`kód chyby.

## <a name="get_id"></a>vlákno:: get_id

Vrátí jedinečný identifikátor pro přidružené vlákno.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

[Vlákno:: ID](#id_class) objekt, který jednoznačně identifikuje přidružené vlákno, nebo `thread::id()` Pokud není k objektu přidruženo žádné vlákno.

## <a name="hardware_concurrency"></a>vlákno:: hardware_concurrency

Statická metoda, která vrací odhad počtu kontextů hardwarových vláken.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odhad počtu kontextů hardwarových vláken. Pokud hodnotu nelze vypočítat nebo není správně definována, vrátí tato metoda hodnotu 0.

## <a name="id_class"></a>Thread:: ID – třída

Poskytuje jedinečný identifikátor pro každé vlákno provádění v procesu.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který se nerovná se rovná `thread::id` objektu pro jakékoli existující vlákno.

Všechny `thread::id` objekty ve výchozím nastavení se rovnají hodnotě EQUAL.

## <a name="join"></a>vlákno:: JOIN

Blokuje až do dokončení vlákna, které je spojeno s volajícím objektem.

```cpp
void join();
```

### <a name="remarks"></a>Poznámky

Pokud je volání úspěšné, následné volání [get_id](#get_id) pro volající objekt vrátí výchozí [vlákno:: ID](#id_class) , které se neporovnání `thread::id` rovná s žádným existujícím vláknem; Pokud volání není úspěšné, hodnota vrácená `get_id`je beze změny.

## <a name="joinable"></a>vlákno:: JOINED

Určuje, zda je přidružené vlákno k.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je přidružené vlákno k. v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Objekt vlákna je *spojen* , pokud `get_id() != id()`.

## <a name="native_handle"></a>vlákno:: native_handle

Vrátí typ specifický pro implementaci představující popisovač vlákna. Popisovač vlákna lze použít v způsobech specifických pro implementaci.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type`je definován jako Win32 `HANDLE` , který se přetypování jako. `void *`

## <a name="op_eq"></a>Thread:: operator =

Přidruží vlákno zadaného objektu k aktuálnímu objektu.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
Objekt **vlákna** .

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Metoda volá metodu detach, pokud je volající objekt spojený.

Po navázání `Other` přidružení je nastaveno na výchozí stav vytvořený.

## <a name="swap"></a>Thread:: swap

Zamění stav objektu pomocí zadaného objektu **vlákna** .

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
Objekt **vlákna** .

## <a name="thread"></a>Thread:: Thread – konstruktor

Vytvoří objekt **vlákna** .

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*FJ*\
Funkce definovaná aplikací, která má být provedena vláknem.

*URČITÉHO*\
Seznam argumentů, které mají být předány *F*.

*Jiná*\
Existující objekt **vlákna** .

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, který není přidružen ke vláknu provádění. Hodnota, která je vrácena voláním `get_id` pro konstruovaný objekt je. `thread::id()`

Druhý konstruktor vytvoří objekt, který je přidružen k novému vláknu provádění a spustí pseudo funkci `INVOKE` , která je definována ve [ \<funkční >](../standard-library/functional.md). Pokud není k dispozici dostatek prostředků pro spuštění nového vlákna, funkce vyvolá objekt [system_error](../standard-library/system-error-class.md) , který má kód `resource_unavailable_try_again`chyby. Pokud se volání *jazyka F* ukončí s nezachycenou výjimkou, je volána metoda [Terminate](../standard-library/exception-functions.md#terminate) .

Třetí konstruktor vytvoří objekt, který je přidružen k vláknu, které je přidruženo `Other`k. `Other`je pak nastaveno na výchozí stav vytvořen.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<> vlákna](../standard-library/thread.md)
