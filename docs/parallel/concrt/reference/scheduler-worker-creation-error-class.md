---
title: scheduler_worker_creation_error – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
dev_langs:
- C++
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d050ee426817c04518a41b515f30ac348bf7d86
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400169"
---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error – třída

Tato třída popisuje výjimku vyvolanou z důvodu selhání při vytváření kontextu spuštění pracovního procesu v modulu Runtime souběžnosti.

## <a name="syntax"></a>Syntaxe

```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|Přetíženo. Vytvoří `scheduler_worker_creation_error` objektu.|

## <a name="remarks"></a>Poznámky

Toto se obvykle výjimka při volání do operačního systému vytvořit kontexty provádění z v rámci modulu Runtime souběžnosti se nezdaří. Kontexty spuštění jsou vlákna, které jsou spouštěny úkoly v modulu Runtime souběžnosti. Kód chyby, která by obvykle vrácená z volání metody Win32 `GetLastError` je převedena na hodnotu typu `HRESULT` a je možné načíst pomocí metody základní třídy `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> scheduler_worker_creation_error –

Vytvoří `scheduler_worker_creation_error` objektu.

```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

*_Hresult*<br/>
`HRESULT` Hodnotou chyby, který způsobil výjimku.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
