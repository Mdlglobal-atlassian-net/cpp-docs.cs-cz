---
title: IExecutionContext – struktura
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 45d65a5e16121d39233c3ceb801933aa1f5a5f8e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138913"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext – struktura

Rozhraní do kontextu spuštění, který může běžet na daném virtuálním procesoru a musí být přepnuty do komutovaného kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IExecutionContext::D-patch](#dispatch)|Metoda, která je volána, když proxy vlákna spustí provádění určitého kontextu spuštění. To by mělo být hlavní rutina pracovního procesu pro váš Plánovač.|
|[IExecutionContext:: getId –](#getid)|Vrací jedinečný identifikátor pro kontext spuštění.|
|[IExecutionContext:: GetProxy](#getproxy)|Vrátí rozhraní k proxy vlákna, které spouští tento kontext.|
|[IExecutionContext:: getschedule](#getscheduler)|Vrátí rozhraní ke Scheduleru, do kterého tento kontext spuštění patří.|
|[IExecutionContext:: SetProxy –](#setproxy)|Přidruží proxy vlákna k tomuto kontextu spuštění. Přidružený proxy vlákna vyvolá tuto metodu přímo předtím, než začne spouštět `Dispatch` metody kontextu.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastního plánovače, který rozhraní s Správce prostředků Concurrency Runtime, bude nutné implementovat rozhraní `IExecutionContext`. Vlákna vytvořená Správce prostředků provádějí v rámci plánovače práci, a to spuštěním metody `IExecutionContext::Dispatch`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IExecutionContext`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="dispatch"></a>IExecutionContext::D metoda-patch

Metoda, která je volána, když proxy vlákna spustí provádění určitého kontextu spuštění. To by mělo být hlavní rutina pracovního procesu pro váš Plánovač.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatchState*<br/>
Ukazatel na stav, pod kterým je tento kontext spuštění odesílán. Další informace o stavu odeslání najdete v tématu [DispatchState](dispatchstate-structure.md).

## <a name="getid"></a>IExecutionContext:: getId – – metoda

Vrací jedinečný identifikátor pro kontext spuštění.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný celočíselný identifikátor.

### <a name="remarks"></a>Poznámky

Použijte metodu `GetExecutionContextId` k získání jedinečného identifikátoru pro objekt, který implementuje rozhraní `IExecutionContext`, před použitím rozhraní jako parametru pro metody dodané Správce prostředků. Očekává se, že vrátíte stejný identifikátor při vyvolání funkce `GetId`.

Identifikátor získaný z jiného zdroje může mít za následek nedefinované chování.

## <a name="getproxy"></a>IExecutionContext:: GetProxy – Metoda

Vrátí rozhraní k proxy vlákna, které spouští tento kontext.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IThreadProxy`. Pokud proxy vlákna kontextu spuštění nebylo inicializováno s voláním `SetProxy`, funkce musí vracet `NULL`.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá metodu `SetProxy` v kontextu spuštění s rozhraním `IThreadProxy` jako parametr, před vstupem metody `Dispatch` v kontextu. Očekává se, že tento argument uložíte a vrátíte ho v voláních `GetProxy()`.

## <a name="getscheduler"></a>IExecutionContext:: getschedule – metoda

Vrátí rozhraní ke Scheduleru, do kterého tento kontext spuštění patří.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IScheduler`.

### <a name="remarks"></a>Poznámky

Chcete-li spustit kontext spuštění s platným `IScheduler`m rozhraním, než ho použijete jako parametr do metod dodaných Správce prostředků.

## <a name="setproxy"></a>IExecutionContext:: SetProxy – – metoda

Přidruží proxy vlákna k tomuto kontextu spuštění. Přidružený proxy vlákna vyvolá tuto metodu přímo předtím, než začne spouštět `Dispatch` metody kontextu.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parametry

*pThreadProxy*<br/>
Rozhraní pro proxy vlákna, které se chystá zadat metodu `Dispatch` v tomto kontextu spuštění.

### <a name="remarks"></a>Poznámky

Očekáváte, že uložíte parametr `pThreadProxy` a vrátíte ho při volání metody `GetProxy`. Správce prostředků garantuje, že proxy vlákna přidružené k kontextu spuštění se nezmění, dokud proxy vlákna provádí metodu `Dispatch`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)
