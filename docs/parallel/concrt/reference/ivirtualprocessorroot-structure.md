---
title: IVirtualProcessorRoot – struktura
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 6e3f874aa7c20494483172d7c7c3efee362cf6a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569868"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot – struktura

Abstrakce pro vlákno hardwaru, na kterém můžete spustit proxy vlákna.

## <a name="syntax"></a>Syntaxe

```
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IVirtualProcessorRoot::Activate](#activate)|Způsobí, že vlákno proxy spojené s rozhraním kontextu spuštění `pContext` spustit provádění na tomto kořenovém adresáři virtuálního procesoru.|
|[Ivirtualprocessorroot::Deactivate –](#deactivate)|Způsobí, že se právě spouští na tomto kořenovém adresáři virtuálního procesoru zastavit odesílání kontextu spuštění proxy vlákna. Podproces proxy bude pokračovat provádění volání `Activate` metody.|
|[Ivirtualprocessorroot::ensurealltasksvisible –](#ensurealltasksvisible)|Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů stane viditelným pro všechny procesory systému. Zajišťuje, že ohrazení paměti úplné spustila na všechny procesory než metoda vrátí.|
|[IVirtualProcessorRoot::GetId](#getid)|Vrací jedinečný identifikátor pro kořen virtuálního procesoru.|

## <a name="remarks"></a>Poznámky

Každý kořen virtuálního procesoru má prostředek přidružené spuštění. `IVirtualProcessorRoot` Rozhraní zdědí [iexecutionresource –](iexecutionresource-structure.md) rozhraní. Stejné základní vlákno hardwaru může odpovídat více kořenových adresářů virtuálního procesoru.

Resource Manager uděluje kořenových adresářů virtuálního procesoru plánovače v reakci na požadavky na prostředky. Plánovač můžete použít kořenovém adresáři virtuálního procesoru a provádí práci kontext spuštění jeho aktivací.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Iexecutionresource –](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="activate"></a>  IVirtualProcessorRoot::Activate – metoda

Způsobí, že vlákno proxy spojené s rozhraním kontextu spuštění `pContext` spustit provádění na tomto kořenovém adresáři virtuálního procesoru.

```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Rozhraní pro kontext spuštění, které se odesílají v tomto kořenovém adresáři virtuálního procesoru.

### <a name="remarks"></a>Poznámky

Resource Manager poskytne proxy vlákna, pokud jeden není přidružen rozhraní kontext spuštění `pContext`

`Activate` Metodu je možné spustit provádění práce na nový kořen virtuálního procesoru vrátil Resource Manageru nebo pokračovat v proxy vlákna v kořenovém adresáři virtuálního procesoru, který byl deaktivován nebo je chcete deaktivovat. Zobrazit [ivirtualprocessorroot::Deactivate –](#deactivate) Další informace o deaktivaci. Pokud pokračujete kořenu virtuálního procesoru deaktivované, parametr `pContext` musí být stejné jako parametr používá k deaktivaci kořen virtuálního procesoru.

Po aktivaci kořenu virtuálního procesoru poprvé, následující páry volání `Deactivate` a `Activate` může mít mezi sebou. To znamená, že je přijatelné pro správce prostředků, aby bylo možné uskutečnit hovor pro `Activate` předtím, než se dostane `Deactivate` byla určena pro volání.

Při aktivaci kořenu virtuálního procesoru, můžete signalizuje, že do Resource Manageru, že tato kořen virtuálního procesoru je momentálně zaneprázdněn v práci. Pokud váš Plánovač nelze najít žádnou práci se promítnou u tohoto kořenového adresáře, očekává se, který má být vyvolán `Deactivate` metodu informování Resource Manageru, že kořenový virtuální procesor je nečinný. Resource Manager používá tato data pro systém Vyrovnávání zatížení.

`invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu `NULL`.

`invalid_operation` je vyvolána, pokud argument `pContext` nepředstavuje kontextu spuštění, který byl naposledy odeslaných v tomto kořenovém adresáři virtuálního procesoru.

V rámci aktivaci kořenu virtuálního procesoru zvýší o 1 úroveň předplatného podkladové vlákno hardwaru. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

##  <a name="deactivate"></a>  Ivirtualprocessorroot::Deactivate – metoda

Způsobí, že se právě spouští na tomto kořenovém adresáři virtuálního procesoru zastavit odesílání kontextu spuštění proxy vlákna. Podproces proxy bude pokračovat provádění volání `Activate` metody.

```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext, který je právě provedenou tohoto kořenového adresáře.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota. Hodnotu **true** označuje, že proxy vlákna vrácena z `Deactivate` metody v reakci na volání `Activate` metoda. Hodnota `false` označuje, že vlákno proxy server vrátil z metody v reakci na události oznámení v Resource Manageru. V uživatelském režimu plánovatelná (UMS) podprocesu plánovače to znamená, že se nezobrazují položky v seznamu pro doplňování plánovače a Plánovač je vyžadován ke zpracování je.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k dočasnému zastavení provádění kořen virtuálního procesoru, pokud nemůže najít žádnou práci v váš plánovač. Volání `Deactivate` metoda musí pocházet z v rámci `Dispatch` metodu kontextu spuštění, která s poslední aktivace kořen virtuálního procesoru. Jinými slovy, proxy vlákna volání `Deactivate` metoda musí být ten, který aktuálně spouští v kořenovém adresáři virtuálního procesoru. Volání metody na kořenovém adresáři virtuálního procesoru, které se spouští na může mít za následek nedefinované chování.

Kořenu virtuálního procesoru deaktivované může být probouzet pomocí volání `Activate` metodou stejný argument, který byl předán v `Deactivate` metoda. Plánovač zodpovídá za to, která volá do `Activate` a `Deactivate` metody jsou párovány, ale nejsou vyžadovány pro další přijetí v určitém pořadí. Resource Manager dokáže zpracovat přijímají volání `Activate` metodu než obdrží volání `Deactivate` metoda je určená pro.

Pokud awakens kořen virtuálního procesoru a návratovou hodnotu z `Deactivate` metoda je hodnota **false**, Plánovač by měl seznamu dokončení UMS pomocí dotazu `IUMSCompletionList::GetUnblockNotifications` metoda zákona o informace a pak následně zavolat `Deactivate` metoda znovu. To je třeba opakovat, dokud `Deactivate` vrátí metoda hodnotu `true`.

`invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu NULL.

`invalid_operation` je vyvolána, pokud byl neaktivoval kořen virtuálního procesoru, nebo argument `pContext` nepředstavuje kontextu spuštění, který byl naposledy odeslaných v tomto kořenovém adresáři virtuálního procesoru.

V rámci deaktivace kořen virtuálního procesoru snižuje o jednu úroveň předplatného podkladové vlákno hardwaru. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

##  <a name="ensurealltasksvisible"></a>  Ivirtualprocessorroot::ensurealltasksvisible – metoda

Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů stane viditelným pro všechny procesory systému. Zajišťuje, že ohrazení paměti úplné spustila na všechny procesory než metoda vrátí.

```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext, který je právě provedenou tomto kořenovém adresáři virtuálního procesoru.

### <a name="remarks"></a>Poznámky

Tato metoda možná zjistíte užitečné, pokud chcete synchronizovat deaktivaci kořen virtuálního procesoru a uveďte novou práci do plánovače. Z důvodů výkonu můžete přidávat pracovní položky do váš Plánovač bez spuštění překážky paměti, což znamená, že pracovní položky přidané vlákno provádění na jeden procesor nejsou okamžitě viditelné pro všechny ostatní procesory. Pomocí této metody ve spojení s `Deactivate` metody můžete zajistit, že váš Plánovač není deaktivovat svůj virtuální procesor kořenových adresářů, zatímco pracovní položky neexistuje v kolekcích váš plánovač.

Volání `EnsureAllTasksVisibleThe` metoda musí pocházet z v rámci `Dispatch` metodu kontextu spuštění, která s poslední aktivace kořen virtuálního procesoru. Jinými slovy, proxy vlákna volání `EnsureAllTasksVisible` metoda musí být ten, který aktuálně spouští v kořenovém adresáři virtuálního procesoru. Volání metody na kořenovém adresáři virtuálního procesoru, které se spouští na může mít za následek nedefinované chování.

`invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu `NULL`.

`invalid_operation` je vyvolána, pokud byl neaktivoval kořen virtuálního procesoru, nebo argument `pContext` nepředstavuje kontextu spuštění, který byl naposledy odeslaných v tomto kořenovém adresáři virtuálního procesoru.

##  <a name="getid"></a>  Ivirtualprocessorroot::getid – metoda

Vrací jedinečný identifikátor pro kořen virtuálního procesoru.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor celé číslo.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
