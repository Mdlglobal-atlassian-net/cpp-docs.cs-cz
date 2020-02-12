---
title: task_continuation_context – třída
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142579"
---
# <a name="task_continuation_context-class"></a>task_continuation_context – třída

Třída `task_continuation_context` umožňuje určit, kde má být pokračování spuštěno. Tuto třídu je užitečné použít jenom z aplikace prostředí Windows Runtime. Pro aplikace, které nejsou prostředí Windows Runtime, je kontext provádění pokračování úlohy určený modulem runtime a nelze jej konfigurovat.

## <a name="syntax"></a>Syntaxe

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Vrátí objekt kontextu pokračování úlohy, který představuje aktuální kontext vlákna WinRT.|
|[use_arbitrary](#use_arbitrary)|Vytvoří kontext pokračování úlohy, který umožňuje modulu runtime zvolit kontext spuštění pro pokračování.|
|[use_current](#use_current)|Vrátí objekt kontextu pokračování úlohy, který představuje aktuální kontext spuštění.|
|[use_default](#use_default)|Vytvoří výchozí kontext pokračování úlohy.|
|[use_synchronous_execution](#use_synchronous_execution)|Vrátí objekt kontextu pokračování úlohy, který představuje synchronní kontext spuštění.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks. h

**Obor názvů:** souběžnost

## <a name="get_current_winrt_context"></a>get_current_winrt_context

Vrátí objekt kontextu pokračování úlohy, který představuje aktuální kontext vlákna WinRT.

### <a name="syntax"></a>Syntaxe

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální kontext vlákna prostředí Windows Runtime. Vrací prázdné task_continuation_context, je-li voláno z kontextu, který není prostředí Windows Runtime.

### <a name="remarks"></a>Poznámky

Metoda `get_current_winrt_context` zachytí kontext vlákna prostředí Windows Runtime volajícího. Vrátí prázdný kontext volajícím jiným než prostředí Windows Runtime.

Hodnota vrácená `get_current_winrt_context` může být použita k označení modulu runtime, že pokračování má být spuštěno v modelu Apartment zachyceného kontextu (STA vs MTA) bez ohledu na to, zda je předchozí úloha v rámci prostředí typu apartment. Úkol využívající prostředí typu Apartment je úkol, který rozbalí rozhraní prostředí Windows Runtime `IAsyncInfo` nebo úkol, který je následníkem tohoto úkolu.

Tato metoda je podobná metodě `use_current`, ale je také k dispozici pro nativní C++ kód bez C++podpory rozšíření/CX. Je určena pro použití pokročilými uživateli, kteří C++zapisují/CX-agnostic kód knihovny pro nativní i prostředí Windows Runtime volající. Pokud tuto funkci nepotřebujete, doporučujeme `use_current` metodu, která je k dispozici pouze C++pro klienty/CX.

## <a name="use_arbitrary"></a>use_arbitrary

Vytvoří kontext pokračování úlohy, který umožňuje modulu runtime zvolit kontext spuštění pro pokračování.

### <a name="syntax"></a>Syntaxe

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Návratová hodnota

Kontext pokračování úlohy, který představuje libovolné umístění.

### <a name="remarks"></a>Poznámky

Pokud je tento kontext pokračování používán, pokračování bude spuštěno v kontextu, který modul runtime zvolí i v případě, že je předchozí úloha vědoma prostředí typu apartment.

`use_arbitrary` lze použít k vypnutí výchozího chování pro pokračování na úkolu, který je zaměřen na použití v rámci STA.

Tato metoda je k dispozici pouze pro prostředí Windows Runtime aplikace.

## <a name="use_current"></a>use_current

Vrátí objekt kontextu pokračování úlohy, který představuje aktuální kontext spuštění.

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální kontext spuštění.

### <a name="remarks"></a>Poznámky

Tato metoda zachycuje kontext prostředí Windows Runtime volajícího, aby bylo možné spustit pokračování v pravém podoblasti.

Hodnota vrácená `use_current` může být použita k označení modulu runtime, že pokračování má být spuštěno v zachyceném kontextu (STA vs MTA) bez ohledu na to, zda je předchozí úloha v rámci prostředí typu apartment. Úkol využívající prostředí typu Apartment je úkol, který rozbalí rozhraní prostředí Windows Runtime `IAsyncInfo` nebo úkol, který je následníkem tohoto úkolu.

Tato metoda je k dispozici pouze pro prostředí Windows Runtime aplikace.

## <a name="use_default"></a>use_default

Vytvoří výchozí kontext pokračování úlohy.

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí kontext pokračování.

### <a name="remarks"></a>Poznámky

Výchozí kontext je použit, pokud nezadáte kontext pokračování při volání metody `then`. V aplikacích systému Windows pro systém Windows 7 a níže i v aplikacích klasické pracovní plochy v systému Windows 8 a vyšší modul runtime určuje, kde budou spouštěny pokračování úlohy. V aplikaci prostředí Windows Runtime však výchozí kontext pokračování pro pokračování v rámci úlohy s podporou na práci s Apartment je objekt Apartment, ve kterém je vyvoláno `then`.

Úkol využívající prostředí typu Apartment je úkol, který rozbalí rozhraní prostředí Windows Runtime `IAsyncInfo` nebo úkol, který je následníkem tohoto úkolu. Proto Pokud naplánujete pokračování v rámci úlohy, která je na základě typu Apartment v prostředí Windows Runtime STA, pokračování bude provedeno v tomto modelu STA.

Pokračování úlohy, která nepracuje na typu apartment, se spustí v kontextu, který modul runtime zvolí.

## <a name="use_synchronous_execution"></a>task_continuation_context:: use_synchronous_execution

Vrátí objekt kontextu pokračování úlohy, který představuje synchronní kontext spuštění.

### <a name="syntax"></a>Syntaxe

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>Návratová hodnota

Kontext synchronního spuštění.

### <a name="remarks"></a>Poznámky

Metoda `use_synchronous_execution` vynutí, aby úloha pokračování běžela synchronně v kontextu, což způsobilo dokončení jeho předchozí úlohy.

Pokud již předchozí úloha byla dokončena, když je pokračování připojeno, pokračování bude spuštěno synchronně v kontextu, který připojení dokončí.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
