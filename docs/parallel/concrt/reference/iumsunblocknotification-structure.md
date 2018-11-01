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
ms.openlocfilehash: 219e32cedb02d4ecab73390e33601de32f9b0992
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677965"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification – struktura

Představuje oznámení ze Správce prostředků, že proxy vlákna, která zablokuje a aktivuje návrat do plánovače určené plánování kontextu má odblokováno a je připravený k naplánování. Toto rozhraní je neplatný, jakmile vrácený kontext spuštění přidružené vlákno proxy, `GetContext` přeplánovat metody.

## <a name="syntax"></a>Syntaxe

```
struct IUMSUnblockNotification;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Iumsunblocknotification::getcontext –](#getcontext)|Vrátí `IExecutionContext` rozhraní pro provádění kontextu přidruženého k proxy vlákna, která má odblokováno. Po návratu tato metoda a změnil základního kontextu spuštění prostřednictvím volání `IThreadProxy::SwitchTo` metody tohoto rozhraní už není platný.|
|[Iumsunblocknotification::getnextunblocknotification –](#getnextunblocknotification)|Vrátí Další `IUMSUnblockNotification` rozhraní v řetězu certifikátů, metoda vrátí `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUMSUnblockNotification`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="getcontext"></a>  Iumsunblocknotification::getcontext – metoda

Vrátí `IExecutionContext` rozhraní pro provádění kontextu přidruženého k proxy vlákna, která má odblokováno. Po návratu tato metoda a změnil základního kontextu spuštění prostřednictvím volání `IThreadProxy::SwitchTo` metody tohoto rozhraní už není platný.

```
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Návratová hodnota

`IExecutionContext` Rozhraní pro kontext spuštění pro proxy vlákna, která má odblokováno.

##  <a name="getnextunblocknotification"></a>  Iumsunblocknotification::getnextunblocknotification – metoda

Vrátí Další `IUMSUnblockNotification` rozhraní v řetězu certifikátů, metoda vrátí `IUMSCompletionList::GetUnblockNotifications`.

```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Další `IUMSUnblockNotification` rozhraní v řetězu certifikátů, metoda vrátí `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)
