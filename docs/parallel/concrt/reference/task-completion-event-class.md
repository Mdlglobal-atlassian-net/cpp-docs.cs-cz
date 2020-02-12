---
title: task_completion_event – třída
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: b3e3093cb76df507f8c707e497c9aec75a065057
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142593"
---
# <a name="task_completion_event-class"></a>task_completion_event – třída

Třída `task_completion_event` umožňuje zpozdit provádění úlohy, dokud není splněna podmínka, nebo spustit úlohu jako odpověď na externí událost.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ výsledku této `task_completion_event` třídy

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_completion_event](#ctor)|Vytvoří objekt `task_completion_event`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[set](#set)|Přetíženo. Nastaví událost dokončení úkolu.|
|[set_exception](#set_exception)|Přetíženo. Šíří výjimku pro všechny úlohy přidružené k této události.|

## <a name="remarks"></a>Poznámky

Použijte úlohu vytvořenou z události dokončení úkolu, když váš scénář vyžaduje, abyste vytvořili úkol, který se dokončí, a tím i jejich pokračování naplánovat na spuštění, a to v nějakém okamžiku v budoucnu. `task_completion_event` musí mít stejný typ jako úloha, kterou vytvoříte, a volání metody set na událost dokončení úkolu s hodnotou tohoto typu způsobí, že se přidružený úkol dokončí, a poskytne tuto hodnotu v důsledku jejich pokračování.

Pokud událost dokončení úkolu není nikdy signalizována, všechny úkoly, které se z něho vytvoří, se při destruktuře zruší.

`task_completion_event` se chová jako inteligentní ukazatel a měl by být předán podle hodnoty.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task_completion_event`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks. h

**Obor názvů:** souběžnost

## <a name="set"></a>stanovenými

Nastaví událost dokončení úkolu.

```cpp
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Parametry

*_Result*<br/>
Výsledek, pomocí kterého se má tato událost nastavit

### <a name="return-value"></a>Návratová hodnota

Metoda vrátí **hodnotu true** , pokud byla úspěšná při nastavení události. Vrátí **hodnotu false** , pokud je již událost nastavena.

### <a name="remarks"></a>Poznámky

V případě existence více nebo souběžných volání `set`, pouze první volání bude úspěšné a výsledek (pokud existuje) bude uložen v události dokončení úkolu. Zbývající sady budou ignorovány a metoda vrátí hodnotu false. Když nastavíte událost dokončení úkolu, všechny úlohy vytvořené z této události se okamžitě dokončí a jejich pokračování (pokud nějaké) se naplánuje. Objekty dokončování úloh, které mají `_ResultType` jiné než **void** , předají hodnotu jejich pokračování.

## <a name="set_exception"></a>set_exception

Šíří výjimku pro všechny úlohy přidružené k této události.

```cpp
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Parametry

*_E*<br/>
Typ výjimky

*_Except*<br/>
Výjimka, která se má nastavit

*_ExceptionPtr*<br/>
Ukazatel na výjimku, který má být nastaven.

### <a name="return-value"></a>Návratová hodnota

## <a name="ctor"></a>task_completion_event

Vytvoří objekt `task_completion_event`.

```cpp
task_completion_event();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
