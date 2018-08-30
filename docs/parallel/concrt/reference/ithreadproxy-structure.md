---
title: Ithreadproxy – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2542be130c75166f8716c76df547c72fad7c2250
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196897"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy – struktura
Abstrakce vlákna exekuce. V závislosti na tom `SchedulerType` klíče zásad plánovače vytvoříte, Resource Manageru, udělí se vám proxy vlákna, která je založená na regulárních vlákno Win32 nebo uživatelským režimem plánovatelná vlákna (UMS). UMS vlákna jsou podporované v 64bitových systémech s verzí Windows 7 a vyšší.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IThreadProxy::GetId](#getid)|Vrací jedinečný identifikátor pro proxy vlákna.|  
|[IThreadProxy::SwitchOut](#switchout)|Zrušíte kontext ze základního kořenového virtuálního procesoru.|  
|[IThreadProxy::SwitchTo](#switchto)|Provede přepnutí kooperativní kontextu z aktuálně prováděné kontext na jiný.|  
|[Ithreadproxy::yieldtosystem –](#yieldtosystem)|Způsobí, že volající vlákno pozastavit provádění na jiný podproces, který je připraven ke spuštění na aktuální procesoru. Operační systém zvolí další vlákno má být proveden.|  
  
## <a name="remarks"></a>Poznámky  
 Proxy vlákna jsou spojeny s kontexty provádění reprezentovaný rozhraním `IExecutionContext` jako způsob, kterému dodává práci.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IThreadProxy`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getid"></a>  Ithreadproxy::getid – metoda  
 Vrací jedinečný identifikátor pro proxy vlákna.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo jedinečný identifikátor.  
  
##  <a name="switchout"></a>  IThreadProxy::SwitchOut – metoda  
 Zrušíte kontext ze základního kořenového virtuálního procesoru.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `switchState`  
 Označuje stav proxy vlákna, které provádí přepínač. Parametr je typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Poznámky  
 Použití `SwitchOut` potřebujete zrušit přiřazení kontextu z kořene virtuálního procesoru, který je spuštěn, z jakéhokoli důvodu. V závislosti na hodnotě předané v parametru `switchState`, a zda je prováděna na kořenovém adresáři virtuálního procesoru, volání se okamžitě vrátí nebo zablokuje vlákno proxy spojené s kontextem. Jedná se o chybu volání `SwitchOut` s parametrem nastaveným na `Idle`. To povede [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky.  
  
 `SwitchOut` je užitečné, když chcete snížit počet kořenů virtuálního procesoru, který má váš Plánovač, protože Resource Manageru můžete k tomu pokyn, nebo požádal dočasné přetížený kořen virtuálního procesoru a jste s ním hotovi. V tomto případě byste měli vyvolat metodu [IVirtualProcessorRoot::Remove](https://msdn.microsoft.com/ad699b4a-1972-4390-97ee-9c083ba7d9e4) v kořenovém adresáři virtuálního procesoru před provedením volání do `SwitchOut` s parametrem `switchState` nastavena na `Blocking`. To bude blokovat vlákno proxy a provádění bude pokračovat, pokud je k dispozici ke spuštění jiný kořen virtuálního procesoru v plánovači. Proxy blokovaného vlákna lze obnovit voláním funkce `SwitchTo` přepnutí na kontext vykonávání tohoto proxy vlákna. Můžete také pokračovat v proxy vlákna pomocí jeho přidruženého kontextu k aktivaci kořenu virtuálního procesoru. Další informace o tom, jak to provést, najdete v části [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 `SwitchOut` může také sloužit Pokud chcete znovu inicializovat virtuální procesor, takže může být aktivován v budoucnosti buď zablokováním proxy vlákna nebo dočasným odpojením od kořenu virtuálního procesoru je spuštěn na a Plánovač ho, kterému dodává práci pro. Použití `SwitchOut` s parametrem `switchState` nastavena na `Blocking` Pokud chcete blokovat proxy vlákna. To lze později obnovit buď pomocí `SwitchTo` nebo `IVirtualProcessorRoot::Activate` jak bylo uvedeno výše. Použití `SwitchOut` s parametrem nastaveným na `Nesting` když chcete dočasně odpojit toto proxy vlákna od kořene virtuálního procesoru, který je spuštěn na a Plánovač je přidružen virtuální procesor. Volání `SwitchOut` s parametrem `switchState` nastavena na `Nesting` při provádění na kořenovém adresáři virtuálního procesoru způsobí, že kořenový opakování inicializace odběrů a aktuální podproces proxy bude pokračovat, aniž by to bylo nutné. Proxy vlákna se považuje za opustilo Plánovač, dokud se volá [IThreadProxy::SwitchOut](#switchout) metodu s `Blocking` později v čase. Druhé volání `SwitchOut` s parametrem nastaveným na `Blocking` má vrátit kontext do blokovaného stavu tak, aby jej šlo obnovit buď `SwitchTo` nebo `IVirtualProcessorRoot::Activate` v Plánovači odpojena od. Protože spuštění v kořenovém adresáři virtuálního procesoru, žádná opětovná inicializace neprobíhá probíhá.  
  
 Kořen reinicializovaný virtuálního procesoru se nijak neliší od zcela nový kořen virtuálního procesoru, které váš Plánovač bylo uděleno správcem prostředků. Můžete ho použít pro spuštění jeho aktivací kontextem spuštění pomocí `IVirtualProcessorRoot::Activate`.  
  
 `SwitchOut` musí být volána na `IThreadProxy` rozhraní, které představuje aktuálně spuštěné vlákno nebo výsledky nejsou definovány.  
  
 V knihovnách a záhlavích, která jsou součástí sady Visual Studio 2010 tato metoda nebere parametr a neinicializuje kořenový virtuální procesor. Pro zachování původního chování, výchozí hodnota parametru `Blocking` pochází.  
  
##  <a name="switchto"></a>  Ithreadproxy::switchto – metoda  
 Provede přepnutí kooperativní kontextu z aktuálně prováděné kontext na jiný.  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Spolupráce při přepnutí do kontextu spuštění.  
  
 `switchState`  
 Označuje stav proxy vlákna, které provádí přepínač. Parametr je typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k přepínání z jednoho spuštění kontextu do jiného, z [iexecutioncontext::Dispatch –](iexecutioncontext-structure.md#dispatch) metoda první kontext spuštění. Metoda přidruží kontextu spuštění `pContext` s proxy vlákna, pokud ještě není spojen s jednou. Hodnota zadaná pro je určena vlastnictví aktuální podproces proxy `switchState` argument.  
  
 Použijte hodnotu `Idle` kdy budete chtít vrátit do Správce prostředků aktuálně prováděné proxy vlákna. Volání `SwitchTo` s parametrem `switchState` nastavena na `Idle` způsobí, že kontextu spuštění `pContext` spustit provádění na tento základní prostředek spravovat spouštění. Vlastnictví tohoto proxy vlákna je převedeno do Resource Manageru a očekává se vrátí z kontextu spuštění `Dispatch` metoda krátce po `SwitchTo` vrátí, aby bylo možné dokončit přenos. Kontext spuštění, který byl odesílání proxy vlákna je oddělen od proxy vlákna a Plánovač je bezplatné ji znovu použít nebo zničit jako považuje za vhodné.  
  
 Použijte hodnotu `Blocking` Pokud chcete toto proxy vlákna vstupovat do blokovaného stavu. Volání `SwitchTo` s parametrem `switchState` nastavena na `Blocking` způsobí, že kontextu spuštění `pContext` spustit provádění, a blokovat aktuální proxy vlákna, dokud nebude obnovená. Plánovač uchovává vlastnictví proxy vlákna po v proxy vlákna `Blocking` stavu. Proxy blokovaného vlákna lze obnovit voláním funkce `SwitchTo` přepnutí na kontext vykonávání tohoto proxy vlákna. Můžete také pokračovat v proxy vlákna pomocí jeho přidruženého kontextu k aktivaci kořenu virtuálního procesoru. Další informace o tom, jak to provést, najdete v části [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 Použijte hodnotu `Nesting` když chcete dočasně odpojit toto proxy vlákna od kořene virtuálního procesoru, který je spuštěn na a Plánovač ho, kterému dodává práci pro. Volání `SwitchTo` s parametrem `switchState` nastavena na `Nesting` způsobí, že kontextu spuštění `pContext` spustit provádění a aktuální proxy vlákna také pokračuje v provádění bez nutnosti kořen virtuálního procesoru. Proxy vlákna se považuje za opustilo Plánovač, dokud se volá [IThreadProxy::SwitchOut](#switchout) metoda později v čase. `IThreadProxy::SwitchOut` Metoda může blokovat proxy vlákna, dokud nebude k dispozici ho přeplánovat kořenovém adresáři virtuálního procesoru.  
  
 `SwitchTo` musí být volána na `IThreadProxy` rozhraní, které představuje aktuálně spuštěné vlákno nebo výsledky nejsou definovány. Funkce vyvolá `invalid_argument` Pokud parametr `pContext` je nastavena na `NULL`.  
  
##  <a name="yieldtosystem"></a>  Ithreadproxy::yieldtosystem – metoda  
 Způsobí, že volající vlákno pozastavit provádění na jiný podproces, který je připraven ke spuštění na aktuální procesoru. Operační systém zvolí další vlákno má být proveden.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Když se zavolá pomocí proxy vlákna se opírá o pravidelných Windows vlákno, `YieldToSystem` se chová stejně jako funkce Windows `SwitchToThread`. Nicméně, při volání z uživatelského režimu plánovatelná vlákna (UMS), `SwitchToThread` funkce deleguje úlohy spustit Plánovač režimu uživatele, ne operačního systému další vlákno výběr. Chcete-li dosáhnout požadovaný účinek přepnutí do jiného vlákna připravená na systém, použijte `YieldToSystem`.  
  
 `YieldToSystem` musí být volána na `IThreadProxy` rozhraní, které představuje aktuálně spuštěné vlákno nebo výsledky nejsou definovány.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [Iexecutioncontext – struktura](iexecutioncontext-structure.md)   
 [Ischeduler – struktura](ischeduler-structure.md)   
 [IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)
