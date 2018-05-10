---
title: structured_task_group – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cca5d20b89df97e27529d656e9a6553fd8a1820
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="structuredtaskgroup-class"></a>structured_task_group – třída
`structured_task_group` Třída reprezentuje kolekci vysoce strukturovaných paralelní práce. Jednotlivé paralelní úlohy pro můžete fronty `structured_task_group` pomocí `task_handle` objekty a počkat na jejich dokončení nebo zrušte skupiny úloh před dokončením provádění, který bude všech úloh, které nebyly zahájení zpracování přerušeno.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[structured_task_group](#ctor)|Přetíženo. Vytvoří nový `structured_task_group` objektu.|  
|[~ structured_task_group – destruktor](#dtor)|Zničí `structured_task_group` objektu. Předpokládá se, že buď volání `wait` nebo `run_and_wait` metoda pro objekt před spuštěním destruktor, pokud je destruktor provádí na základě těchto zásobníku unwinding kvůli výjimce.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zrušit](#cancel)|Díky usilovně pokus o zrušení podstromu pracovní root v této skupině úloh. Každý úkol naplánovat na skupině úloh bude získat zrušena přechodně Pokud je to možné.|  
|[is_canceling –](#is_canceling)|Informuje o volající, jestli je skupina úkolů aktuálně in the midst of zrušení. To nemusí znamenat, který `cancel` byla volána metoda `structured_task_group` objektu (i když například tato metoda vrátí vyfiltrování určitě `true`). Může být tento případ, `structured_task_group` objektu provádí vložené a další skupinu úkolů až ve stromové struktuře pracovní byla zrušena. V případech, například tyto kde můžete určit modulu runtime dopředu, který zrušení bude procházet přes tento `structured_task_group` objekt, `true` bude vrácen také.|  
|[Spustit](#run)|Přetíženo. Naplánuje úlohu na `structured_task_group` objektu. Volající spravuje životnost `task_handle` objekt předaná `_Task_handle` parametr. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.|  
|[run_and_wait](#run_and_wait)|Přetíženo. Plány úlohy ke spuštění vložené na kontext volání s pomocí `structured_task_group` objekt pro podporu úplné zrušení. Pokud `task_handle` objekt je předán jako parametr, který se `run_and_wait`, volající zodpovídá za správu životnost `task_handle` objektu. Funkce pak čeká, dokud všechny práci `structured_task_group` objekt buď dokončit nebo byla zrušena.|  
|[Počkej](#wait)|Čeká, dokud všechny práci `structured_task_group` již byla dokončena nebo je zrušena.|  
  
## <a name="remarks"></a>Poznámky  
 Existuje několik závažné omezení vztahujících se na využití `structured_task_group` objektu, aby získal výkonu:  
  
-   Jediný `structured_task_group` objektu nemůže být použit více vláken. Všechny operace v `structured_task_group` objekt musí být provedeny prostřednictvím vlákno, které vytvořil objekt. Existují dvě výjimky pro toto pravidlo členské funkce `cancel` a `is_canceling`. Objekt nemusí být v seznamu zachycení výrazu lambda a použít v rámci úlohy, pokud úloha je jedním z operace zrušení.  
  
-   Všechny úlohy naplánované `structured_task_group` objekt jsou naplánovány prostřednictvím `task_handle` objekty, které musí explicitně spravovat dobu životnosti.  
  
-   Více skupin může použít pouze v nezbytně vnořené pořadí. Pokud dva `structured_task_group` objekty jsou deklarovány, druhý probíhá deklarovaný (vnitřní jeden) musíte destruct než kterákoli metoda, s výjimkou `cancel` nebo `is_canceling` se volá na první z nich (vnější jeden). Tato podmínka platí v případě jednoduše deklarování více `structured_task_group` objektů v rámci stejné nebo funkčně vnořené obory, jakož i v případě úlohu, která je ve frontě `structured_task_group` prostřednictvím `run` nebo `run_and_wait` metody.  
  
-   Na rozdíl od Obecné `task_group` třídy, všechny stavy v `structured_task_group` třídy jsou poslední. Po zařazených do fronty úloh do skupiny a čekali na jejich dokončení, nesmíte používat stejnou skupinu znovu.  
  
 Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `structured_task_group`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="cancel"></a> Zrušit 

 Díky usilovně pokus o zrušení podstromu pracovní root v této skupině úloh. Každý úkol naplánovat na skupině úloh bude získat zrušena přechodně Pokud je to možné.  
  
```
void cancel();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="is_canceling"></a> is_canceling – 

 Informuje o volající, jestli je skupina úkolů aktuálně in the midst of zrušení. To nemusí znamenat, který `cancel` byla volána metoda `structured_task_group` objektu (i když například tato metoda vrátí vyfiltrování určitě `true`). Může být tento případ, `structured_task_group` objektu provádí vložené a další skupinu úkolů až ve stromové struktuře pracovní byla zrušena. V případech, například tyto kde můžete určit modulu runtime dopředu, který zrušení bude procházet přes tento `structured_task_group` objekt, `true` bude vrácen také.  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Sdělení, zda `structured_task_group` objektu je in the midst of zrušení (nebo záruku, že být zanedlouho).  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="run"></a> Spustit 

 Naplánuje úlohu na `structured_task_group` objektu. Volající spravuje životnost `task_handle` objekt předaná `_Task_handle` parametr. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.  
  
```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána provést text popisovač úloh.  
  
 `_Task_handle`  
 Popisovač pro pracovní naplánován. Všimněte si, že má volající odpovědnost za dobu životnosti tohoto objektu. Modul runtime bude pokračovat očekávat, že za provozu, dokud buď `wait` nebo `run_and_wait` byla volána metoda v tomto `structured_task_group` objektu.  
  
 `_Placement`  
 Odkaz na umístění, kde úloha reprezentována `_Task_handle` parametr má být spuštěn.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime vytvoří kopii pracovní funkce, která předat tuto metodu. Změny stavu, ke kterým došlo v objektu funkce, kterou předáte této metodě se nebude zobrazovat na vaší kopie tohoto objektu funkce.  
  
 Pokud `structured_task_group` destructs v důsledku z výjimku unwinding zásobníku, není nutné zaručit, že volání nebyly provedeny buď `wait` nebo `run_and_wait` metoda. V takovém případě destruktoru správně zruší a čekání na úlohu reprezentována `_Task_handle` parametr k dokončení.  
  
 Vyvolá [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) výjimka, pokud úloha zpracovat dané podle `_Task_handle` parametr již bylo naplánováno na objekt úlohy skupiny prostřednictvím `run` metoda a byla bez použité volání buď `wait` nebo `run_and_wait` metoda na této skupině úloh.  
  
##  <a name="run_and_wait"></a> run_and_wait – 

 Plány úlohy ke spuštění vložené na kontext volání s pomocí `structured_task_group` objekt pro podporu úplné zrušení. Pokud `task_handle` objekt je předán jako parametr, který se `run_and_wait`, volající zodpovídá za správu životnost `task_handle` objektu. Funkce pak čeká, dokud všechny práci `structured_task_group` objekt buď dokončit nebo byla zrušena.  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána při provádění úlohy.  
  
 `_Task_handle`  
 Popisovač pro úlohu, která se spustí vložené na kontext volání. Všimněte si, že má volající odpovědnost za dobu životnosti tohoto objektu. Modul runtime bude pokračovat očekávat, že za provozu, dokud `run_and_wait` metoda dokončí provádění.  
  
 `_Func`  
 Funkci, která bude volána k vyvolání text práce. To může být lambda nebo jiného objektu, která podporuje verzi operátor volání funkce s podpisem `void operator()()`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, zda byla splněna čekání nebo skupině úloh byla zrušena, z důvodu operace explicitní zrušit nebo výjimku hlášeny z jednoho z jeho úlohy. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jeden nebo více úloh naplánovaných k tomuto `structured_task_group` objekt může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více úloh naplánovaných k tomuto `structured_task_group` objekt vyvolá výjimku, použije modul runtime vyberte jeden takové výjimky jeho výběru a šířit z volání `run_and_wait` metoda.  
  
 Po návratu tato funkce `structured_task_group` objekt považován za konečného stavu a by se neměla používat. Všimněte si, že využití po `run_and_wait` metoda vrátí, bude mít za následek nedefinované chování.  
  
 V cestě k ostatním provádění, máte pověření k volání této metody nebo `wait` metody před destruktoru objektu `structured_task_group` provede.  
  
##  <a name="ctor"></a> structured_task_group 

 Vytvoří nový `structured_task_group` objektu.  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>Parametry  
 `_CancellationToken`  
 Token zrušení přidružení k této skupiny strukturovaných úloh. Skupiny strukturovaných úloh budou zrušeny, když je zrušeno token.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor, který přebírá token zrušení vytvoří `structured_task_group` , budou zrušeny, když se zruší zdrojový přidružené k tokenu. Token zrušení explicitní poskytuje také izoluje této skupiny strukturovaných úloh ze implicitní zrušení z nadřazené skupiny s token jiné nebo žádné token.  
  
##  <a name="dtor"></a> ~ structured_task_group 

 Zničí `structured_task_group` objektu. Předpokládá se, že buď volání `wait` nebo `run_and_wait` metoda pro objekt před spuštěním destruktor, pokud je destruktor provádí na základě těchto zásobníku unwinding kvůli výjimce.  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>Poznámky  
 Jestliže destruktoru běží jako výsledek normální spuštění (například není unwinding zásobníku kvůli výjimce) a ani `wait` ani `run_and_wait` metod, může vyvolat destruktoru [missing_wait](missing-wait-class.md) došlo k výjimce.  
  
##  <a name="wait"></a> Počkej 

 Čeká, dokud všechny práci `structured_task_group` již byla dokončena nebo je zrušena.  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, zda byla splněna čekání nebo skupině úloh byla zrušena, z důvodu operace explicitní zrušit nebo výjimku hlášeny z jednoho z jeho úlohy. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jeden nebo více úloh naplánovaných k tomuto `structured_task_group` objekt může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více úloh naplánovaných k tomuto `structured_task_group` objekt vyvolá výjimku, použije modul runtime vyberte jeden takové výjimky jeho výběru a šířit z volání `wait` metoda.  
  
 Po návratu tato funkce `structured_task_group` objekt považován za konečného stavu a by se neměla používat. Všimněte si, že využití po `wait` metoda vrátí, bude mít za následek nedefinované chování.  
  
 V cestě k ostatním provádění, máte pověření k volání této metody nebo `run_and_wait` metody před destruktoru objektu `structured_task_group` provede.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [task_group – třída](task-group-class.md)   
 [task_handle – třída](task-handle-class.md)
