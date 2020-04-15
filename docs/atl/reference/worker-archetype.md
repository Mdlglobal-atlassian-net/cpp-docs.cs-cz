---
title: Archetyp pracovníka
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: b0b32232d7386df0c0f13a1c3af1003369b906e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329350"
---
# <a name="worker-archetype"></a>Archetyp pracovníka

Třídy, které odpovídají *archetypu pracovního* procesu, poskytují kód pro zpracování pracovních položek zařazených do fronty ve fondu vláken.

**Implementace**

Chcete-li implementovat třídu odpovídající tomuto archetypu, musí třída poskytovat následující funkce:

|Metoda|Popis|
|------------|-----------------|
|[Initialize](#initialize)|Volána k inicializaci objektu pracovníka před všechny požadavky jsou předány [execute](#execute).|
|[Spuštění](#execute)|Nazývá se zpracování pracovní položky.|
|[Terminate](#terminate)|Volána k zrušení inicializaci objektu pracovníka poté, co byly předány všechny požadavky [na execute](#execute).|

|Typedef|Popis|
|-------------|-----------------|
|[Requesttype](#requesttype)|Typedef pro typ pracovní položky, které mohou být zpracovány třídou pracovníka.|

Typická *třída pracovníka* vypadá takto:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Stávající implementace**

Tyto třídy odpovídají tomuto archetypu:

|Třída|Popis|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky z fondu vláken a předá je pracovnímu objektu, který je vytvořen a zničen pro každý požadavek.|

**Použití**

Tyto parametry šablony očekávají, že třída bude odpovídat tomuto archetypu:

|Název parametru|Používá|
|--------------------|-------------|
|*Pracovník*|[Fond cthreadpoolu](../../atl/reference/cthreadpool-class.md)|
|*Pracovník*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Spustit

Nazývá se zpracování pracovní položky.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parametry

*Požadavek*<br/>
Pracovní položka, která má být zpracována. Pracovní položka je stejného `RequestType`typu jako .

*pvWorkerParam*<br/>
Vlastní parametr, kterému rozumí třída pracovníka. Také předán `WorkerArchetype::Initialize` `Terminate`a .

*přeskakované*<br/>
Ukazatel na [překrývající se](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) strukturu použitou k vytvoření fronty, ve které byly pracovní položky zařazeny do fronty.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Inicializovat

Nazývá se inicializovat objekt pracovníka před `WorkerArchetype::Execute`všechny požadavky jsou předány .

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Vlastní parametr, kterému rozumí třída pracovníka. Také předán `WorkerArchetype::Terminate` `WorkerArchetype::Execute`a .

### <a name="return-value"></a>Návratová hodnota

Vrátit HODNOTU TRUE na úspěch, FALSE na selhání.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType

Typedef pro typ pracovní položky, které mohou být zpracovány třídou pracovníka.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Poznámky

Tento typ musí být použit `WorkerArchetype::Execute` jako první parametr a musí být možné je přehodit do ULONG_PTR a z ní.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Ukončit

Volána k zrušení inicializace objektu `WorkerArchetype::Execute`pracovníka poté, co byly předány všechny požadavky ).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parametry

*pvParam*<br/>
Vlastní parametr, kterému rozumí třída pracovníka. Také předán `WorkerArchetype::Initialize` `WorkerArchetype::Execute`a .

## <a name="see-also"></a>Viz také

[Koncepty](../../atl/active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
