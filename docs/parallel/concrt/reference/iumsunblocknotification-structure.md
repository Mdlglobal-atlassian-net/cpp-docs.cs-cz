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
ms.openlocfilehash: d4fd95b1f11ed6edac26cb03e41e8b650acfafa3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139973"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification – struktura

Představuje oznámení z Správce prostředků, který proxy vlákno zablokovalo a aktivovalo návrat do určeného časového kontextu plánovače, který je odblokovaný a připravený k naplánování. Toto rozhraní je po přeplánování přidruženého kontextu spuštění, který je vrácen z metody `GetContext`, neplatné.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IUMSUnblockNotification –:: GetContext](#getcontext)|Vrátí rozhraní `IExecutionContext` pro kontext spuštění přidružený k proxy vlákna, které bylo odblokováno. Až tato metoda vrátí a podkladový kontext spuštění byl přeplánován prostřednictvím volání metody `IThreadProxy::SwitchTo`, toto rozhraní již není platné.|
|[IUMSUnblockNotification –:: Getnextunblocknotification –](#getnextunblocknotification)|Vrátí další `IUMSUnblockNotification` rozhraní v řetězci vráceném z metody `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUMSUnblockNotification`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="getcontext"></a>IUMSUnblockNotification –:: GetContext – Metoda

Vrátí rozhraní `IExecutionContext` pro kontext spuštění přidružený k proxy vlákna, které bylo odblokováno. Až tato metoda vrátí a podkladový kontext spuštění byl přeplánován prostřednictvím volání metody `IThreadProxy::SwitchTo`, toto rozhraní již není platné.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IExecutionContext` pro kontext spuštění do proxy vlákna, které odblokovalo.

## <a name="getnextunblocknotification"></a>IUMSUnblockNotification –:: Getnextunblocknotification – – metoda

Vrátí další `IUMSUnblockNotification` rozhraní v řetězci vráceném z metody `IUMSCompletionList::GetUnblockNotifications`.

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Další `IUMSUnblockNotification` rozhraní v řetězci vráceném z metody `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)
