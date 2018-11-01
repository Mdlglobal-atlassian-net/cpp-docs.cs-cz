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
ms.openlocfilehash: 5f358dbc61fc39928e877dbc3673a8b9f51917eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582507"
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context – třída

`task_continuation_context` Třída umožňuje určit, kde byste chtěli pokračování má být proveden. Je vhodné použít tuto třídu z aplikace pro Windows Runtime. Pro aplikace Windows Runtime je kontext pokračování úlohy určován v modulu runtime a nelze jej konfigurovat.

## <a name="syntax"></a>Syntaxe

```
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Vrátí objekt kontextu pokračování úlohy, představující aktuální kontext vlákna winrt.|
|[use_arbitrary](#use_arbitrary)|Vytvoří kontext pokračování úlohy, která umožňuje zvolit kontext pokračování spuštění modulu Runtime.|
|[use_current](#use_current)|Vrátí objekt kontextu pokračování úlohy, představující aktuální kontext spuštění.|
|[use_default](#use_default)|Vytvoří výchozí kontext pokračování úlohy.|
|[use_synchronous_execution](#use_synchronous_execution)|Vrátí objekt kontextu pokračování úlohy, představující kontext synchronní provádění.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks.h

**Namespace:** souběžnosti

## <a name="get_current_winrt_context"></a> get_current_winrt_context

Vrátí objekt kontextu pokračování úlohy, představující aktuální kontext vlákna WinRT.

## <a name="syntax"></a>Syntaxe

```
static task_continuation_context get_current_winrt_context();
```

## <a name="return-value"></a>Návratová hodnota

Aktuální kontext vlákna modulu Windows Runtime. Vrátí prázdný task_continuation_context – Pokud se volá z kontextu Windows Runtime.

## <a name="remarks"></a>Poznámky

`get_current_winrt_context` Metoda zachycuje kontext vlákna volajícího prostředí Windows Runtime. Vrátí prázdnému kontextu volajícím Windows Runtime.

Hodnota vrácená `get_current_winrt_context` slouží k oznámení modulu Runtime, že pokračování má být spuštěno v modelu objektu apartment zachyceném kontextu (STA vs MTA) bez ohledu na to, zda je předchozí úloha vědoma objektu apartment. Úkol je úkol, který rozbalí Windows Runtime komplexu `IAsyncInfo` rozhraní nebo úloha, která je potomkem takového úkolu.

Tato metoda je podobný `use_current` metody, ale dostupná je i nativní kód C++ bez C + +/ CX rozšíření podpory. Je určena pro použití zkušení uživatelé psaní C + +/ CX bez ohledu na kód knihovny pro nativní a volající modulu Windows Runtime. Pokud potřebujete tuto funkci, doporučujeme `use_current` metodu, která je dostupná jenom pro C + +/ CX klientů.

##  <a name="use_arbitrary"></a> use_arbitrary –

Vytvoří kontext pokračování úlohy, která umožňuje zvolit kontext pokračování spuštění modulu Runtime.

```
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Návratová hodnota

Kontext pokračování úlohy, který představuje libovolné umístění.

### <a name="remarks"></a>Poznámky

Když je použit tento kontext pokračování, pokračování bude spuštěno v kontextu, který modul runtime zvolí i v případě, že je předchozí úloha vědoma objektu apartment.

`use_arbitrary` slouží k vypnutí výchozího chování pro pokračování na vědom objektu Apartment vytvořené v STA.

Tato metoda je pouze k dispozici pro aplikace Windows Runtime.

##  <a name="use_current"></a> use_current –

Vrátí objekt kontextu pokračování úlohy, představující aktuální kontext spuštění.

```
static task_continuation_context use_current();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální kontext spuštění.

### <a name="remarks"></a>Poznámky

Tato metoda zachycuje kontext modulu Runtime Windows volajícího tak, aby pokračování mohla být provedena ve správném objektu apartment.

Hodnota vrácená `use_current` slouží k oznámení modulu Runtime, že pokračování má být spuštěno v zachyceném kontextu (STA vs MTA) bez ohledu na to, zda je předchozí úloha vědoma objektu apartment. Úkol je úkol, který rozbalí Windows Runtime komplexu `IAsyncInfo` rozhraní nebo úloha, která je potomkem takového úkolu.

Tato metoda je pouze k dispozici pro aplikace Windows Runtime.

##  <a name="use_default"></a> use_default –

Vytvoří výchozí kontext pokračování úlohy.

```
static task_continuation_context use_default();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí kontext pokračování.

### <a name="remarks"></a>Poznámky

Výchozí kontext se používá, pokud nezadáte pokračování kontextu při volání `then` metody. Ve Windows aplikací pro Windows 7 a níže, jakož i aplikace klasické pracovní plochy v systému Windows 8 a vyšší modul runtime určuje, kde budou prováděna pokračování úlohy. Ale v aplikaci Windows Runtime, je výchozí kontext pokračování pro pokračování na vědom objektu Apartment apartment kde `then` je vyvolána.

Úkol je úkol, který rozbalí Windows Runtime komplexu `IAsyncInfo` rozhraní nebo úloha, která je potomkem takového úkolu. Proto pokud plánujete pokračování na vědom objektu Apartment v Windows Runtime STA, pokračování bude spuštěno v tomto STA

Pokračování na úkolu vědět-objektu apartment bude spuštěno v kontextu, který modul Runtime zvolí.

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution

Vrátí objekt kontextu pokračování úlohy, představující kontext synchronní provádění.

## <a name="syntax"></a>Syntaxe

```
static task_continuation_context use_synchronous_execution();
```

## <a name="return-value"></a>Návratová hodnota

Synchronní provádění kontextu.

## <a name="remarks"></a>Poznámky

`use_synchronous_execution` Metoda donutí úkol pokračování, aby běžel synchronně v kontextu, což způsobí jeho předchozí úloha dokončení.

Pokud je předchozí úloha již dokončena případě, že pokračování, pokračování pracuje synchronně, na kontextu, který se připojí pokračování.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
