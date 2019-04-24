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
ms.openlocfilehash: bdf083e2ad418269e49e53dc164f2a60f693d5d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180209"
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

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)
