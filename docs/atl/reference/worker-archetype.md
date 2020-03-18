---
title: Pracovní proces Archetype
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 2e57c575ed778184cf319bb84e61f585fcfa2111
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509338"
---
# <a name="worker-archetype"></a>Pracovní proces Archetype

Třídy, které odpovídají Archetype *pracovního procesu* , poskytují kód pro zpracování pracovních položek zařazených do fronty ve fondu vláken.

**Implementace**

Chcete-li implementovat třídu, která odpovídá tomuto Archetype, třída musí poskytovat následující funkce:

|Metoda|Popis|
|------------|-----------------|
|[Initialize](#initialize)|Volá se, aby se inicializoval objekt pracovního procesu před předáním všech požadavků, které se mají [provést](#execute).|
|[Execute](#execute)|Volá se, aby se zpracovala pracovní položka.|
|[Terminate](#terminate)|Volá se, aby se zrušila inicializace objektu pracovního procesu po předání všech požadavků, které se mají [provést](#execute).|

|Definic|Popis|
|-------------|-----------------|
|[Třídy](#requesttype)|Definice typu pracovní položky, která může být zpracována třídou pracovního procesu.|

Typická třída *pracovního procesu* vypadá takto:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Existující implementace**

Tyto třídy odpovídají tomuto archetype:

|Třída|Popis|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Přijímá žádosti z fondu vláken a předává je do objektu pracovního procesu, který je vytvořen a zničen pro každý požadavek.|

**Použití**

Tyto parametry šablony očekávají, že třída bude vyhovovat tomuto archetype:

|Název parametru|Používáno v|
|--------------------|-------------|
|*Zaměstnanec*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Zaměstnanec*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

## <a name="execute"></a>WorkerArchetype:: Execute

Volá se, aby se zpracovala pracovní položka.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parametry

*Request*<br/>
Pracovní položka, která má být zpracována. Pracovní položka je stejného typu jako `RequestType`.

*pvWorkerParam*<br/>
Vlastní parametr, který rozumí třída pracovního procesu. Také předán `WorkerArchetype::Initialize` a `Terminate`.

*pOverlapped*<br/>
Ukazatel na [PŘEkrývající](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) se strukturu použitou k vytvoření fronty, na které byly pracovní položky zařazeny do fronty.

## <a name="initialize"></a>WorkerArchetype:: Initialize

Volá se, aby se inicializoval objekt pracovního procesu před předáním všech požadavků do `WorkerArchetype::Execute`.

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Vlastní parametr, který rozumí třída pracovního procesu. Také předán `WorkerArchetype::Terminate` a `WorkerArchetype::Execute`.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, což je FALSE při selhání.

## <a name="requesttype"></a>WorkerArchetype:: RequestType

Definice typu pracovní položky, která může být zpracována třídou pracovního procesu.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Poznámky

Tento typ musí být použit jako první parametr `WorkerArchetype::Execute` a musí být schopný přetypování do a z ULONG_PTR.

## <a name="terminate"></a>WorkerArchetype:: terminate

Volá se, aby se zrušila inicializace objektu pracovního procesu po předání všech požadavků do `WorkerArchetype::Execute`).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Vlastní parametr, který rozumí třída pracovního procesu. Také předán `WorkerArchetype::Initialize` a `WorkerArchetype::Execute`.

## <a name="see-also"></a>Viz také

[Koncepty](../../atl/active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
