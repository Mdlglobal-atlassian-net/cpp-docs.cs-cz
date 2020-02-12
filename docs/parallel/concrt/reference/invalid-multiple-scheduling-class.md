---
title: invalid_multiple_scheduling – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: a8b2a045ce94562dcba0019bc03aaa90c4d384a9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140908"
---
# <a name="invalid_multiple_scheduling-class"></a>invalid_multiple_scheduling – třída

Tato třída popisuje výjimku vyvolanou při vícenásobném naplánování `task_handle` objektu pomocí metody `run` objektu `task_group` nebo `structured_task_group` bez toho, aby bylo volání metody `wait` nebo `run_and_wait`.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|Přetíženo. Vytvoří objekt `invalid_multiple_scheduling`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_multiple_scheduling

Vytvoří objekt `invalid_multiple_scheduling`.

```cpp
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_handle – třída](task-handle-class.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[spouštěl](task-group-class.md)<br/>
[Počkej](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group – třída](structured-task-group-class.md)
