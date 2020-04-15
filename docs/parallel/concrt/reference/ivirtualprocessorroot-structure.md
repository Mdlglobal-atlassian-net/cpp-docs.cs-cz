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
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364264"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot – struktura

Abstrakce pro hardwarové vlákno, na kterém může být spuštěn proxy vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IVirtualProcessorRoot::Aktivovat](#activate)|Způsobí, že proxy vlákna `pContext` přidružené k rozhraní kontextu spuštění spustit provádění v tomto kořenovém adresáři virtuálního procesoru.|
|[IVirtualProcessorRoot::Deaktivovat](#deactivate)|Způsobí, že proxy podproces aktuálně provádí v tomto kořenovém adresáři virtuálního procesoru zastavit odesílání kontextu spuštění. Proxy podproces bude pokračovat v provádění `Activate` při volání metody.|
|[iVirtualProcessorRoot::Zajistit všechny úkoly visible](#ensurealltasksvisible)|Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů, aby se stal viditelným pro všechny procesory v systému. Zajišťuje, že úplné paměti plot byl proveden na všechny procesory před vrátí metoda.|
|[IVirtualProcessorRoot::GetId](#getid)|Vrátí jedinečný identifikátor pro kořenový virtuální procesor.|

## <a name="remarks"></a>Poznámky

Každý kořen virtuálního procesoru má přidružený prostředek spuštění. Rozhraní `IVirtualProcessorRoot` dědí z rozhraní [IExecutionResource.](iexecutionresource-structure.md) Více kořenů virtuálního procesoru může odpovídat stejnému základnímu hardwarovému vláknu.

Správce prostředků uděluje kořeny virtuálních procesorů plánovačům v reakci na požadavky na prostředky. Plánovač můžete použít kořen ový virtuální procesor k provedení práce aktivací s kontextem spuštění.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot::Metoda aktivace

Způsobí, že proxy vlákna `pContext` přidružené k rozhraní kontextu spuštění spustit provádění v tomto kořenovém adresáři virtuálního procesoru.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Rozhraní kontextu spuštění, které bude odesláno v tomto kořenovém adresáři virtuálního procesoru.

### <a name="remarks"></a>Poznámky

Správce prostředků dodá proxy podproces, pokud není přidružen k rozhraní kontextu spuštění`pContext`

Tuto `Activate` metodu lze použít ke spuštění provádění práce na novém kořenovém adresáři virtuálního procesoru vráceném Správcem prostředků nebo k obnovení proxy vlákna v kořenovém adresáři virtuálního procesoru, který byl deaktivován nebo se chystá deaktivovat. Další informace o deaktivaci naleznete v tématu [IVirtualProcessorRoot::Deactivate.](#deactivate) Pokud pokračujete v deaktivovaném kořenovém `pContext` adresáři virtuálního procesoru, musí být parametr stejný jako parametr použitý k deaktivaci kořenového adresáře virtuálního procesoru.

Jakmile je kořen virtuálního procesoru poprvé aktivován, následné `Deactivate` `Activate` dvojice hovorů a mohou závodit mezi sebou. To znamená, že je přijatelné pro Správce `Activate` prostředků přijímat volání `Deactivate` před přijetím volání, pro které byl určen pro.

Když aktivujete kořenový virtuální procesor, signalizujete Správci prostředků, že tento kořen ový virtuální procesor je aktuálně zaneprázdněn prací. Pokud plánovač nemůže najít žádnou práci k provedení v tomto `Deactivate` kořenovém adresáři, očekává se, že vyvolá metodu informující Správce prostředků, že kořenový adresář virtuálního procesoru je nečinný. Správce prostředků používá tato data k vyrovnávání zatížení systému.

`invalid_argument`je vyvolána, `pContext` pokud argument `NULL`má hodnotu .

`invalid_operation`je vyvolána, `pContext` pokud argument nepředstavuje kontext spuštění, který byl naposledy odeslán tento kořen virtuálníprocesor.

Aktivace kořenového adresáře virtuálního procesoru zvyšuje úroveň předplatného základního hardwarového vlákna o jednu. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot::Deaktivovat metodu

Způsobí, že proxy podproces aktuálně provádí v tomto kořenovém adresáři virtuálního procesoru zastavit odesílání kontextu spuštění. Proxy podproces bude pokračovat v provádění `Activate` při volání metody.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Kontext, který je aktuálně odesílán tímto kořenem.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota. Hodnota **true** označuje, že proxy podproces uvrácené `Deactivate` z `Activate` metody v reakci na volání metody. Hodnota `false` označuje, že proxy podproces se vrátil z metody v reakci na událost oznámení ve Správci prostředků. V plánovači vláken v uživatelském režimu (UMS) to znamená, že položky se zobrazily v seznamu dokončení plánovače a plánovač je nutný k jejich zpracování.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete dočasně zastavit provádění kořenového adresáře virtuálního procesoru, když v plánovači nemůžete najít žádnou práci. Volání `Deactivate` metody musí pocházet z `Dispatch` metody kontextu spuštění, se kterou byl kořen virtuálního procesoru naposledy aktivován. Jinými slovy proxy vlákna s `Deactivate` odkazem na metodu musí být ten, který je aktuálně spuštěn v kořenovém adresáři virtuálního procesoru. Volání metody v kořenovém adresáři virtuálního procesoru, ve které neprovádíte, může mít za následek nedefinované chování.

Deaktivovaný kořen virtuálního procesoru může být `Activate` probuzen voláním metody se stejným `Deactivate` argumentem, který byl předán metodě. Plánovač je zodpovědný za zajištění, že `Activate` `Deactivate` volání a metody jsou spárovány, ale nemusí být přijaty v určitém pořadí. Správce prostředků může zpracovat příjem `Activate` volání metody před přijetím `Deactivate` volání metody, pro kterou byl určen.

Pokud kořen virtuálníprocesor probudí a vrácená `Deactivate` hodnota z metody je hodnota **false**, plánovač by `IUMSCompletionList::GetUnblockNotifications` měl dotaz seznamu dokončení UMS prostřednictvím metody, jednat podle této informace a následně volat metodu `Deactivate` znovu. To by mělo být opakováno, dokud `Deactivate` metoda vrátí hodnotu `true`.

`invalid_argument`je vyvolána, `pContext` pokud argument má hodnotu NULL.

`invalid_operation`je vyvolána, pokud kořen ový virtuální procesor `pContext` nebyl nikdy aktivován nebo argument nepředstavuje kontext spuštění, který byl naposledy odeslán tímto kořenem virtuálního procesoru.

Deaktivace kořenového adresáře virtuálního procesoru snižuje úroveň předplatného základního hardwarového vlákna o jednu. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot::EnsureAllTasksVisible Metoda

Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů, aby se stal viditelným pro všechny procesory v systému. Zajišťuje, že úplné paměti plot byl proveden na všechny procesory před vrátí metoda.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Kontext, který je právě odesílán tímto kořenem virtuálního procesoru.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete považovat za užitečnou, pokud chcete synchronizovat deaktivaci kořenového adresáře virtuálního procesoru s přidáním nové práce do plánovače. Z důvodů výkonu se můžete rozhodnout přidat pracovní položky do plánovače bez spuštění bariéry paměti, což znamená, že pracovní položky přidané podprocesem spuštěným na jednom procesoru nejsou okamžitě viditelné pro všechny ostatní procesory. Pomocí této metody ve `Deactivate` spojení s metodou můžete zajistit, že plánovač nedeaktivuje všechny kořeny virtuálního procesoru, zatímco pracovní položky existují v kolekcích plánovače.

Volání `EnsureAllTasksVisibleThe` metody musí pocházet z `Dispatch` metody kontextu spuštění, se kterou byl kořen virtuálního procesoru naposledy aktivován. Jinými slovy proxy vlákna s `EnsureAllTasksVisible` odkazem na metodu musí být ten, který je aktuálně spuštěn v kořenovém adresáři virtuálního procesoru. Volání metody v kořenovém adresáři virtuálního procesoru, ve které neprovádíte, může mít za následek nedefinované chování.

`invalid_argument`je vyvolána, `pContext` pokud argument `NULL`má hodnotu .

`invalid_operation`je vyvolána, pokud kořen ový virtuální procesor `pContext` nebyl nikdy aktivován nebo argument nepředstavuje kontext spuštění, který byl naposledy odeslán tímto kořenem virtuálního procesoru.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot::Metoda GetId

Vrátí jedinečný identifikátor pro kořenový virtuální procesor.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor celého čísla.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
