---
title: task_canceled – třída
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: b1436f921343843ee2b50888f00b6d470e513329
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142608"
---
# <a name="task_canceled-class"></a>task_canceled – třída

Tato třída popisuje výjimku vyvolanou vrstvou úloh PPL, aby se vynutilo zrušení aktuální úlohy. Je také vyvolána metodou `get()` v [úloze](/visualstudio/extensibility/debugger/task-class-internal-members)pro zrušený úkol.

## <a name="syntax"></a>Syntaxe

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_canceled](#ctor)|Přetíženo. Vytvoří objekt `task_canceled`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`task_canceled`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>task_canceled

Vytvoří objekt `task_canceled`.

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
