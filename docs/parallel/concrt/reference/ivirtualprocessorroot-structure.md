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
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139886"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot – struktura

Abstrakce pro hardwarové vlákno, ve kterém se dá spustit proxy vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IVirtualProcessorRoot:: Activate](#activate)|Způsobí, že proxy vlákna přidružené k rozhraní kontextu spuštění `pContext` spustit v tomto kořenovém adresáři virtuálního procesoru.|
|[IVirtualProcessorRoot::D eactivate](#deactivate)|Způsobí, že proxy serveru vlákna aktuálně probíhá v rámci této kořenové složky virtuálního procesoru a zastavilo odesílání kontextu spuštění. Proxy vlákna bude pokračovat ve spuštění při volání metody `Activate`.|
|[IVirtualProcessorRoot:: EnsureAllTasksVisible –](#ensurealltasksvisible)|Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů budou viditelná pro všechny procesory v systému. Zajišťuje, aby bylo na všech procesorech provedeno celé ohraničení paměti před tím, než se metoda vrátí.|
|[IVirtualProcessorRoot:: getId –](#getid)|Vrátí jedinečný identifikátor kořene virtuálního procesoru.|

## <a name="remarks"></a>Poznámky

Každý kořen virtuálního procesoru má přidružený prostředek spuštění. Rozhraní `IVirtualProcessorRoot` dědí z rozhraní [IExecutionResource](iexecutionresource-structure.md) . Několik kořenových adresářů virtuálních procesorů může odpovídat stejnému základnímu hardwarovému vláknu.

Správce prostředků uděluje adresářům virtuálního procesoru plánovači v reakci na požadavky na prostředky. Plánovač může k provedení práce použít kořen virtuálního procesoru a aktivovat ho pomocí kontextu spuštění.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="activate"></a>IVirtualProcessorRoot:: Activate – metoda

Způsobí, že proxy vlákna přidružené k rozhraní kontextu spuštění `pContext` spustit v tomto kořenovém adresáři virtuálního procesoru.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Rozhraní do kontextu spuštění, který bude odeslán v tomto kořenovém adresáři virtuálního procesoru.

### <a name="remarks"></a>Poznámky

Správce prostředků poskytne proxy vlákna, pokud není přidruženo k rozhraní kontextu spuštění `pContext`

Metodu `Activate` lze použít k zahájení provádění práce na novém kořenu virtuálního procesoru vráceném Správce prostředků nebo pro pokračování v proxy vlákna v kořenovém adresáři virtuálního procesoru, který byl deaktivován nebo se chystá deaktivovat. Další informace o deaktivaci najdete v tématu [IVirtualProcessorRoot::D eactivate](#deactivate) . Při obnovování deaktivovaného kořene virtuálního procesoru se parametr `pContext` musí shodovat s parametrem použitým k deaktivaci kořene virtuálního procesoru.

Jakmile se kořenový adresář virtuálního procesoru aktivuje poprvé, můžou další páry volání `Deactivate` a `Activate` vzájemně navzájem. To znamená, že je přijatelné, aby Správce prostředků dostal volání `Activate` předtím, než přijme `Deactivate` volání, pro které bylo určeno.

Když aktivujete kořen virtuálního procesoru, budete signalizovat Správce prostředků, že tento kořen virtuálního procesoru je v tuto chvíli zaneprázdněný prací. Pokud váš Plánovač nemůže najít žádnou práci, která má být vykonána v tomto kořenu, očekává se, že vyvoláte metodu `Deactivate`, která Správce prostředků, že kořen virtuálního procesoru je nečinný. Správce prostředků používá tato data k vyrovnávání zatížení systému.

`invalid_argument` je vyvolána, pokud argument `pContext` hodnotu `NULL`.

`invalid_operation` je vyvolána, pokud argument `pContext` nepředstavuje kontext spuštění, který byl naposledy odeslán kořenem virtuálního procesoru.

Postup aktivace kořene virtuálního procesoru zvyšuje úroveň předplatného podkladového vlákna hardwaru o jednu. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="deactivate"></a>IVirtualProcessorRoot::D eactivate – metoda

Způsobí, že proxy serveru vlákna aktuálně probíhá v rámci této kořenové složky virtuálního procesoru a zastavilo odesílání kontextu spuštění. Proxy vlákna bude pokračovat ve spuštění při volání metody `Activate`.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext, který je aktuálně odesílán tímto kořenem.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota. Hodnota **true** značí, že proxy vlákna vráceného z metody `Deactivate` v reakci na volání metody `Activate`. Hodnota `false` označuje, že se proxy vlákno vrátilo z metody v reakci na událost oznámení v Správce prostředků. V Plánovači vláken plánovatelná v uživatelském režimu (UMS) to znamená, že se položky zobrazily v seznamu pro doplňování Scheduleru a Plánovač je vyžaduje k jejich zpracování.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k dočasnému zastavení provádění kořene virtuálního procesoru, když v Plánovači nemůžete najít žádnou práci. Volání metody `Deactivate` musí pocházet z metody `Dispatch` kontextu spuštění, se kterým se kořen virtuálního procesoru naposledy aktivoval. Jinými slovy, proxy vlákna, které volá metodu `Deactivate`, musí být ten, který se aktuálně provádí v kořenu virtuálního procesoru. Volání metody v kořenovém adresáři virtuálního procesoru, na kterém neprovádíte, by mohlo vést k nedefinovanému chování.

Deaktivovaný kořen virtuálního procesoru může být probuzený voláním metody `Activate` se stejným argumentem, který byl předán metodě `Deactivate`. Scheduler zodpovídá za to, že jsou spárována volání metod `Activate` a `Deactivate`, ale není nutné je přijímat v určitém pořadí. Správce prostředků může zpracovat příjem volání metody `Activate` předtím, než přijme volání metody `Deactivate`, pro kterou byla určena.

Pokud je kořenový adresář virtuálního procesoru awakens a návratová hodnota z `Deactivate` metoda je hodnota **false**, Scheduler by měl dotazovat se na seznam pro doplňování UMS prostřednictvím metody `IUMSCompletionList::GetUnblockNotifications`, jednat na tyto informace a pak znovu zavolat `Deactivate` metody. Tato hodnota by se měla opakovat až do doby, kdy metoda `Deactivate` vrátí hodnotu `true`.

`invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu NULL.

`invalid_operation` je vyvolána, pokud není kořenový adresář virtuálního procesoru nikdy aktivován nebo pokud argument `pContext` nepředstavuje kontext spuštění, který byl naposledy odeslán kořenem virtuálního procesoru.

Proces deaktivace kořene virtuálního procesoru sníží úroveň předplatného podkladového vlákna hardwaru o jednu. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot:: EnsureAllTasksVisible – – metoda

Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů budou viditelná pro všechny procesory v systému. Zajišťuje, aby bylo na všech procesorech provedeno celé ohraničení paměti před tím, než se metoda vrátí.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext, který je aktuálně odesílán z tohoto kořene virtuálního procesoru.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete najít užitečnou, pokud chcete synchronizovat deaktivaci kořene virtuálního procesoru s přidáním nové práce do plánovače. Z důvodů výkonu se můžete rozhodnout přidat pracovní položky do plánovače bez provedení bariéry paměti, což znamená, že pracovní položky přidané vláknem spuštěným na jednom procesoru nejsou okamžitě viditelné pro všechny ostatní procesory. Když použijete tuto metodu spolu s metodou `Deactivate`, můžete zajistit, že Plánovač neaktivuje všechny kořenové adresáře virtuálních procesorů, zatímco pracovní položky existují v kolekcích plánovače.

Volání metody `EnsureAllTasksVisibleThe` musí pocházet z metody `Dispatch` kontextu spuštění, se kterým se kořen virtuálního procesoru naposledy aktivoval. Jinými slovy, proxy vlákna, které volá metodu `EnsureAllTasksVisible`, musí být ten, který se aktuálně provádí v kořenu virtuálního procesoru. Volání metody v kořenovém adresáři virtuálního procesoru, na kterém neprovádíte, by mohlo vést k nedefinovanému chování.

`invalid_argument` je vyvolána, pokud argument `pContext` hodnotu `NULL`.

`invalid_operation` je vyvolána, pokud není kořenový adresář virtuálního procesoru nikdy aktivován nebo pokud argument `pContext` nepředstavuje kontext spuštění, který byl naposledy odeslán kořenem virtuálního procesoru.

## <a name="getid"></a>IVirtualProcessorRoot:: getId – – metoda

Vrátí jedinečný identifikátor kořene virtuálního procesoru.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Celočíselný identifikátor.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
