---
title: scheduler_worker_creation_error – třída
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: e7f2763d7244be9e5e5b006b31b97c08e213a4f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142756"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error – třída

Tato třída popisuje výjimku vyvolanou v důsledku selhání vytvoření kontextu spuštění pracovního procesu v Concurrency Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|Přetíženo. Vytvoří objekt `scheduler_worker_creation_error`.|

## <a name="remarks"></a>Poznámky

Tato výjimka je obvykle vyvolána v případě, že volání operačního systému vytvoří kontexty provádění z Concurrency Runtime se nezdařila. Kontexty provádění jsou vlákna, která spouštějí úlohy v Concurrency Runtime. Kód chyby, který by byl obvykle vrácen z volání metody Win32 `GetLastError`, je převeden na hodnotu typu `HRESULT` a lze jej načíst pomocí metody základní třídy `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>scheduler_worker_creation_error

Vytvoří objekt `scheduler_worker_creation_error`.

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

*_Hresult*<br/>
Hodnota `HRESULT` chyby, která způsobila výjimku.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
