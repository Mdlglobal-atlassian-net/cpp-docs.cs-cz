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
ms.openlocfilehash: 565f4b409f19d7ab70d536e977c13d628c30e882
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442195"
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
