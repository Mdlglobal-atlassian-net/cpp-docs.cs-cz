---
title: "Ithreadproxy – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs: C++
helpviewer_keywords: IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc0808d7b6eae3db64695d2d3e0b40d092361a6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ithreadproxy-structure"></a>IThreadProxy – struktura
Abstrakci pro vlákno provádění. V závislosti na tom `SchedulerType` klíčem zásad plánovače vytvoříte Resource Manager udělí můžete vlákno proxy server, který je zálohovaný díky regulární vlákno Win32 nebo které lze plánovat vlákna (UMS) uživatelského režimu. Vlákna UMS jsou podporované v operačních systémech 64bitové verze Windows 7 a vyšší.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ithreadproxy::getid –](#getid)|Vrací jedinečný identifikátor pro proxy server přístup z více vláken.|  
|[Ithreadproxy::switchout –](#switchout)|Zrušíte kontext z kořenového adresáře základní virtuálních procesorů.|  
|[Ithreadproxy::switchto –](#switchto)|Provede přepínač spolupráci kontext z aktuálně prováděné kontextu na jiný.|  
|[Ithreadproxy::yieldtosystem –](#yieldtosystem)|Způsobí, že volání podproces yield provádění na jiné vlákno, který je připraven ke spuštění na aktuální procesoru. Operační systém vybere další vlákno spouštění.|  
  
## <a name="remarks"></a>Poznámky  
 Vlákno proxy jsou připojeného k provádění kontexty reprezentována rozhraní `IExecutionContext` jako prostředek k odeslání práci.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IThreadProxy`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getid"></a>Ithreadproxy::getid – metoda  
 Vrací jedinečný identifikátor pro proxy server přístup z více vláken.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo jedinečný identifikátor.  
  
##  <a name="switchout"></a>Ithreadproxy::switchout – metoda  
 Zrušíte kontext z kořenového adresáře základní virtuálních procesorů.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `switchState`  
 Označuje stav proxy přístup z více vláken, který provádí přepínač. Parametr je typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Poznámky  
 Použití `SwitchOut` Pokud je potřeba zrušit přidružení kontext z kořene virtuálních procesorů je prováděna, z jakéhokoli důvodu. V závislosti na hodnotě můžete předat v parametru `switchState`, a zda je prováděna v kořenovém adresáři virtuálních procesorů, volání se vrátí okamžitě nebo blokovat přístup z více vláken proxy spojený s kontextem. Jedná se o chybu volat `SwitchOut` s parametrem nastavena na `Idle`. Díky tomu bude mít za následek [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka.  
  
 `SwitchOut`je užitečné, když chcete snížit počet virtuálních procesorů adresáře, které má vaše scheduler, protože Resource Manager sdělil, abyste tak učinit, nebo požadovaný kořenový dočasné oversubscribed virtuálních procesorů a hotovi s ním. V takovém případě by měla vyvolat metodu [IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4) na kořenový virtuální procesor, před provedením volání `SwitchOut` s parametrem `switchState` nastavena na `Blocking`. To bude blokovat přístup z více vláken proxy a obnoví spuštění, když kořenová různých virtuálních procesorů v Plánovači je možné provést. Blokování vláken proxy může být obnoven voláním funkce `SwitchTo` přepnout do kontextu spuštění tento proxy server přístup z více vláken. Proxy vlákno, může pokračovat i pomocí jeho přidružené kontextu aktivovat kořenové virtuálních procesorů. Další informace o tom, jak to udělat najdete v tématu [ivirtualprocessorroot::Activate –](ivirtualprocessorroot-structure.md#activate).  
  
 `SwitchOut`mohou být využity také když chcete znovu inicializovat virtuálních procesorů, takže ho může aktivovat, pokud v budoucnu program buď blokování vláken proxy nebo dočasně probíhá odpojování od kořenu virtuálních procesorů je spuštěn na a Plánovač ho odesílá práci pro. Použití `SwitchOut` s parametrem `switchState` nastavena na `Blocking` Pokud chcete blokovat proxy přístup z více vláken. Může být později obnoveno buď pomocí `SwitchTo` nebo `IVirtualProcessorRoot::Activate` uvedených výše. Použití `SwitchOut` s parametrem nastavena na `Nesting` Pokud chcete dočasně odpojit tento proxy server vlákno z kořene virtuálních procesorů je spuštěn na a Plánovač virtuálních procesorů je přidružen. Volání metody `SwitchOut` s parametrem `switchState` nastavena na `Nesting` při je prováděna v kořenovém adresáři virtuálních procesorů způsobí kořenu k znovu inicializovat a aktuální vlákno proxy Chcete pokračovat v provádění bez nutnosti jeden. Vlákno proxy se považuje za opustili Plánovač dokud zavolá [ithreadproxy::switchout –](#switchout) metoda s `Blocking` později v čase. Druhé volání `SwitchOut` s parametrem nastavena na `Blocking` má vrátit zpět kontextu stav blokování, může být obnoven, a to buď `SwitchTo` nebo `IVirtualProcessorRoot::Activate` v Plánovači ji odpojit z. Vzhledem k tomu, že nebyla spouštění v kořenovém adresáři virtuálních procesorů žádná opětovná inicializace probíhá.  
  
 Inicializace virtuálních procesorů kořenové se neliší od nové kořenové virtuálních procesorů, které vašeho scheduleru byla udělena Resource Manager. Můžete ho pro provedení aktivací kontext provádění prostřednictvím `IVirtualProcessorRoot::Activate`.  
  
 `SwitchOut`musí být voláno na `IThreadProxy` rozhraní, které představuje aktuálně prováděné vlákno nebo výsledky nejsou definovány.  
  
 Tato metoda v knihovny a hlavičky, která jsou součástí sady Visual Studio 2010, nemusí provádět žádné parametr a není znovu inicializovat kořenu virtuálních procesorů. Chcete-li zachovat původní chování, výchozí hodnota parametru `Blocking` pochází.  
  
##  <a name="switchto"></a>Ithreadproxy::switchto – metoda  
 Provede přepínač spolupráci kontext z aktuálně prováděné kontextu na jiný.  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Spolupráce při přepnout do kontextu spuštění.  
  
 `switchState`  
 Označuje stav proxy přístup z více vláken, který provádí přepínač. Parametr je typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k přepnutí z kontextu jeden spuštění na jinou, z [iexecutioncontext::Dispatch –](iexecutioncontext-structure.md#dispatch) metoda první kontextu spuštění. Metoda přidruží kontext provádění `pContext` s proxy přístup z více vláken, pokud ještě není spojen s jednou. Vlastnictví aktuální vlákno proxy je dáno hodnota zadaná `switchState` argument.  
  
 Použijte hodnotu `Idle` Pokud chcete vrátit do Správce prostředků aktuálně prováděné proxy přístup z více vláken. Volání metody `SwitchTo` s parametrem `switchState` nastavena na `Idle` způsobí, že kontext provádění `pContext` spustit provádění na základní provádění prostředku. Vlastnictví tento proxy server vlákno se přenáší do Resource Manager a předpokládá se, že mají být vráceny od kontextu spuštění `Dispatch` metoda krátce po `SwitchTo` vrátí k dokončení přenosu. Kontext spuštění, který byl odeslání proxy přístup z více vláken je oddělen z proxy serveru přístup z více vláken a plánovače může opakovaně ji používat nebo zničit jako považuje za vhodné.  
  
 Použijte hodnotu `Blocking` když chcete tento proxy server vlákno zadat stav blokování. Volání metody `SwitchTo` s parametrem `switchState` nastavena na `Blocking` způsobí, že kontext provádění `pContext` spustí provádění a blokování aktuální vlákno proxy, dokud nebude obnovená. Plánovač uchovává vlastnictví proxy vlákno po proxy přístup z více vláken v `Blocking` stavu. Blokování vláken proxy může být obnoven voláním funkce `SwitchTo` přepnout do kontextu spuštění tento proxy server přístup z více vláken. Proxy vlákno, může pokračovat i pomocí jeho přidružené kontextu aktivovat kořenové virtuálních procesorů. Další informace o tom, jak to udělat najdete v tématu [ivirtualprocessorroot::Activate –](ivirtualprocessorroot-structure.md#activate).  
  
 Použijte hodnotu `Nesting` Pokud chcete dočasně odpojit tento proxy server vlákno z kořene virtuálních procesorů je spuštěn na a Plánovač ho odesílá práci pro. Volání metody `SwitchTo` s parametrem `switchState` nastavena na `Nesting` způsobí, že kontext provádění `pContext` zahájí provádění a aktuální vlákno proxy také pokračuje v provádění bez nutnosti kořenové virtuálních procesorů. Vlákno proxy se považuje za opustili Plánovač dokud zavolá [ithreadproxy::switchout –](#switchout) metoda později v čase. `IThreadProxy::SwitchOut` Metoda může blokovat proxy přístup z více vláken dokud nebude k dispozici ho přeplánovat kořenové virtuálních procesorů.  
  
 `SwitchTo`musí být voláno na `IThreadProxy` rozhraní, které představuje aktuálně prováděné vlákno nebo výsledky nejsou definovány. Funkce vyvolá `invalid_argument` Pokud parametr `pContext` je nastaven na `NULL`.  
  
##  <a name="yieldtosystem"></a>Ithreadproxy::yieldtosystem – metoda  
 Způsobí, že volání podproces yield provádění na jiné vlákno, který je připraven ke spuštění na aktuální procesoru. Operační systém vybere další vlákno spouštění.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Při volání serverem proxy vlákno zajišťoval regulární Windows vlákno, `YieldToSystem` se chová stejně jako funkce systému Windows `SwitchToThread`. Ale, že při volání z uživatelského režimu které lze plánovat vláken (UMS), `SwitchToThread` funkce deleguje úlohy výběr další vlákno spustit na uživatele Plánovač režimu, není operační systém. K dosažení požadované účinku přepnutí na jiný připravené vlákno v systému, použít `YieldToSystem`.  
  
 `YieldToSystem`musí být voláno na `IThreadProxy` rozhraní, které představuje aktuálně prováděné vlákno nebo výsledky nejsou definovány.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Iexecutioncontext – struktura](iexecutioncontext-structure.md)   
 [Struktura rozhraní IScheduler](ischeduler-structure.md)   
 [IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)
