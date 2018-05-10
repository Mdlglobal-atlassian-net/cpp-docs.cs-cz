---
title: Ivirtualprocessorroot – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
dev_langs:
- C++
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9620ee391b525356bfdb50b00d7e76c03b480815
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot – struktura
Abstrakci pro hardware vláken, ve kterém můžete spustit vlákno proxy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ivirtualprocessorroot::Activate –](#activate)|Způsobí, že proxy vlákno přidružené k rozhraní kontext provádění `pContext` spustit provádění v této kořenové virtuálních procesorů.|  
|[Ivirtualprocessorroot::Deactivate –](#deactivate)|Způsobí, že proxy vlákno aktuálně spuštěných v kořenovém adresáři tohoto virtuálního procesoru zastavit odesílání kontextu spuštění. Vlákno proxy bude pokračovat v provádění na volání `Activate` metoda.|  
|[Ivirtualprocessorroot::ensurealltasksvisible –](#ensurealltasksvisible)|Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů se viditelné pro všechny procesory systému. Zajišťuje, že ochranná úplné paměti provedl na všechny procesory než metoda vrátí.|  
|[IVirtualProcessorRoot::GetId](#getid)|Vrací jedinečný identifikátor pro kořenovou virtuální procesor.|  
  
## <a name="remarks"></a>Poznámky  
 Každý procesor virtuálního kořenového má k přidružené provádění prostředku. `IVirtualProcessorRoot` Rozhraní dědí z [iexecutionresource –](iexecutionresource-structure.md) rozhraní. Několik virtuálních procesorů kořeny nemusí odpovídat stejný základní hardware vlákno.  
  
 Resource Manager uděluje virtuálních procesorů kořeny plánovače v reakci na požadavky na prostředky. Plánovače můžete použít kořenové virtuálních procesorů pro práci aktivací s kontextu spuštění.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Iexecutionresource –](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="activate"></a>  Ivirtualprocessorroot::Activate – metoda  
 Způsobí, že proxy vlákno přidružené k rozhraní kontext provádění `pContext` spustit provádění v této kořenové virtuálních procesorů.  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Rozhraní pro provádění kontext, který bude odeslán na této kořenové virtuálních procesorů.  
  
### <a name="remarks"></a>Poznámky  
 Správce prostředků bude zadat proxy přístup z více vláken, pokud není přidružené rozhraní kontext spuštění `pContext`  
  
 `Activate` Metodu lze použít ke spuštění provádění pracovní na nový kořen virtuálních procesorů vrátil pomocí Správce prostředků, nebo obnovit proxy přístup z více vláken v kořenovém adresáři virtuálních procesorů, který má deaktivováno nebo je chcete deaktivovat. V tématu [ivirtualprocessorroot::Deactivate –](#deactivate) Další informace o deaktivaci. Pokud se obnovení kořenové deaktivované virtuálních procesorů, parametr `pContext` musí být stejný jako parametr používá deaktivace kořenu virtuálních procesorů.  
  
 Jakmile kořenové virtuálních procesorů aktivován poprvé, následných páry volání `Deactivate` a `Activate` mohou soupeřit mezi sebou. To znamená, že je přijatelné pro Resource Manager přijímat volání `Activate` před obdrží `Deactivate` byla určena pro volání.  
  
 Když aktivujete kořenové virtuálních procesorů, můžete signál Resource Manager, že tohoto kořenového adresáře virtuálních procesorů je momentálně zaneprázdněné. s pracovní. Pokud vaše scheduler nemůže najít veškerou práci, provést v této kořenové, očekává se má být vyvolán `Deactivate` metoda informuje o Resource Manager nečinný kořenu virtuálních procesorů. Správce prostředků používá tato data pro systém Vyrovnávání zatížení.  
  
 `invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu `NULL`.  
  
 `invalid_operation` je vyvolána, pokud argument `pContext` nepředstavuje kontext spuštění, který byl naposledy odeslaných pomocí tohoto kořenového virtuálních procesorů.  
  
 V rámci aktivace kořenové virtuálních procesorů zvyšuje úroveň předplatného základní hardware vlákno o jednu. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="deactivate"></a>  Ivirtualprocessorroot::Deactivate – metoda  
 Způsobí, že proxy vlákno aktuálně spuštěných v kořenovém adresáři tohoto virtuálního procesoru zastavit odesílání kontextu spuštění. Vlákno proxy bude pokračovat v provádění na volání `Activate` metoda.  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Kontext, který je aktuálně provedenou tohoto kořenového adresáře.  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota. Hodnota `true` označuje, že vlákno proxy vrácena z `Deactivate` metoda v reakci na volání `Activate` metoda. Hodnota `false` označuje, že vlákno proxy vrátila z metody v reakci na oznámení událostí ve Správci prostředků. V uživatelském režimu které lze plánovat (UMS) podprocesu plánovače to označuje, že se nezobrazují položky v seznamu dokončení plánovače a Plánovač je potřeba zpracovat je.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody dočasně pozastavit provádění kořenové virtuálních procesorů, když nelze najít veškerou práci ve vašem scheduler. Volání `Deactivate` metoda musí pocházet z uvnitř `Dispatch` metodu kontext provádění, která s poslední aktivace kořenu virtuálních procesorů. Jinými slovy, vlákno proxy vyvolání `Deactivate` metoda musí být ten, který je aktuálně spuštěných v kořenovém adresáři virtuálních procesorů. Volání metody v kořenovém adresáři virtuálních procesorů, které nejsou provádění na může mít za následek nedefinované chování.  
  
 Kořenové deaktivované virtuálních procesorů může být probouzet pomocí volání `Activate` metoda s stejný argument, který byl předán v `Deactivate` metoda. Plánovač je odpovědný za dodržování, který volá, aby se `Activate` a `Deactivate` metody jsou spárovat, ale nejsou požadované k přijetí v určitém pořadí. Resource Manager může zpracovávat přijetí volání `Activate` metoda před obdrží volání `Deactivate` metoda je určená pro.  
  
 Pokud awakens kořenové virtuálních procesorů a návratovou hodnotou z `Deactivate` metoda je hodnota `false`, Plánovač má seznamu dokončení UMS pomocí dotazu `IUMSCompletionList::GetUnblockNotifications` metoda, fungují v těchto informací a následně volání `Deactivate`metoda znovu. To je třeba opakovat, dokud `Deactivate` vrátí metoda hodnotu `true`.  
  
 `invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu `NULL`.  
  
 `invalid_operation` je vyvolána, pokud kořenu virtuálních procesorů nikdy aktivován, nebo argument `pContext` nepředstavuje kontext spuštění, který byl naposledy odeslaných pomocí tohoto kořenového virtuálních procesorů.  
  
 V rámci deaktivace kořenové virtuálních procesorů sníží úroveň předplatného základní hardware vlákno jeden. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="ensurealltasksvisible"></a>  Ivirtualprocessorroot::ensurealltasksvisible – metoda  
 Způsobí, že data uložená v hierarchii paměti jednotlivých procesorů se viditelné pro všechny procesory systému. Zajišťuje, že ochranná úplné paměti provedl na všechny procesory než metoda vrátí.  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Kontext, který je aktuálně provedenou tohoto kořenového adresáře virtuálních procesorů.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může najít užitečné, pokud chcete synchronizovat deaktivace kořenové virtuálních procesorů s přidáním nové práci do plánovače. Z důvodů výkonu můžete rozhodnout pro přidání pracovních položek do vašeho scheduleru bez provádění bariéry paměti, což znamená, pracovní položky přidal vlákno provádění na jeden procesor nejsou okamžitě viditelné pro všechny ostatní procesory. Pomocí této metody ve spojení s `Deactivate` kořeny metoda můžete zajistit, že vaše scheduler není deaktivovat všech virtuálních procesorů, když existují pracovních položek v kolekcích vašeho scheduleru.  
  
 Volání `EnsureAllTasksVisibleThe` metoda musí pocházet z uvnitř `Dispatch` metodu kontext provádění, která s poslední aktivace kořenu virtuálních procesorů. Jinými slovy, vlákno proxy vyvolání `EnsureAllTasksVisible` metoda musí být ten, který je aktuálně spuštěných v kořenovém adresáři virtuálních procesorů. Volání metody v kořenovém adresáři virtuálních procesorů, které nejsou provádění na může mít za následek nedefinované chování.  
  
 `invalid_argument` je vyvolána, pokud argument `pContext` má hodnotu `NULL`.  
  
 `invalid_operation` je vyvolána, pokud kořenu virtuálních procesorů nikdy aktivován, nebo argument `pContext` nepředstavuje kontext spuštění, který byl naposledy odeslaných pomocí tohoto kořenového virtuálních procesorů.  
  
##  <a name="getid"></a>  Ivirtualprocessorroot::getid – metoda  
 Vrací jedinečný identifikátor pro kořenovou virtuální procesor.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor celé číslo.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
