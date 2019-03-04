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
ms.openlocfilehash: caef1c62ff09ffb76f74d4a1453e9d59dcb7d45b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265493"
---
# <a name="taskcanceled-class"></a>task_canceled – třída

Tato třída popisuje výjimku vyvolanou vrstvou úkolů PPL, aby bylo možné zrušit aktuální úlohu. Je také vyvolané `get()` metodu na [úloh](/visualstudio/extensibility/debugger/task-class-internal-members), případě zrušené úlohy.

## <a name="syntax"></a>Syntaxe

```
class task_canceled : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_canceled](#ctor)|Přetíženo. Vytvoří `task_canceled` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`task_canceled`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> task_canceled –

Vytvoří `task_canceled` objektu.

```
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
