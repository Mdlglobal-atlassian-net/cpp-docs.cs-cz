---
title: IUMSUnblockNotification – struktura
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368061"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification – struktura

Představuje oznámení ze Správce prostředků, že proxy podproces, který zablokoval a spustil návrat do kontextu určeného plánování plánovače odblokoval a je připraven k naplánování. Toto rozhraní je neplatné, jakmile je přeplánován `GetContext` kontext přidruženého spuštění proxy vlákna vrácený z metody.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|Vrátí `IExecutionContext` rozhraní pro kontext spuštění přidružené k proxy podprocesu, který byl odblokován. Jakmile tato metoda vrátí a základní spuštění kontextu byla přeplánována prostřednictvím volání `IThreadProxy::SwitchTo` metody, toto rozhraní již není platný.|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Vrátí další `IUMSUnblockNotification` rozhraní v řetězci `IUMSCompletionList::GetUnblockNotifications`vrácené z metody .|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUMSUnblockNotification`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMSUnblockNotification::Metoda GetContext

Vrátí `IExecutionContext` rozhraní pro kontext spuštění přidružené k proxy podprocesu, který byl odblokován. Jakmile tato metoda vrátí a základní spuštění kontextu byla přeplánována prostřednictvím volání `IThreadProxy::SwitchTo` metody, toto rozhraní již není platný.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IExecutionContext` pro kontext spuštění proxy vlákna, který odblokoval.

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMSUnblockNotification::Metoda GetNextUnblockNotification

Vrátí další `IUMSUnblockNotification` rozhraní v řetězci `IUMSCompletionList::GetUnblockNotifications`vrácené z metody .

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Další `IUMSUnblockNotification` rozhraní v řetězci vrácené z metody `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)
