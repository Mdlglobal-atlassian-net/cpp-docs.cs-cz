---
title: task_group – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
dev_langs:
- C++
helpviewer_keywords:
- task_group class
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7ee8fa674174d95c3e538889f6d5538be049b70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020717"
---
# <a name="taskgroup-class"></a>task_group – třída
`task_group` Třída reprezentuje kolekci paralelní práce, které mohou čekat nebo bylo zrušeno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class task_group;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_group](#ctor)|Přetíženo. Sestaví nový `task_group` objektu.|  
|[~ task_group – destruktor](#dtor)|Odstraní `task_group` objektu. Očekává se, že volání buď `wait` nebo `run_and_wait` metodu na objekt před destruktor prováděný, pokud je destruktor se provádí v důsledku uvolnění z důvodu výjimky zásobníku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zrušit](#cancel)|Díky nezaručené pokus o zrušení podstromě pracovní kořenovým adresářem v této skupině úloh. Každá úloha naplánována na skupinu úloh bude zrušena přechodně Pokud je to možné.|  
|[is_canceling –](#is_canceling)|Určuje, jestli je skupina úloh aktuálně uprostřed zrušením informuje volající. Neznamená to nutně, který `cancel` byla volána metoda `task_group` objektu (i když například jistě kvalifikuje tuto metodu za účelem vrácení `true`). To může být případ, který `task_group` objektu je probíhá vloženě a další skupinu úloh nahoru ve stromové struktuře práce byla zrušena. V případech, jako jsou tyto kde můžete určit modul runtime zrušení budou směrovat přes to předem `task_group` objektu, `true` vrátí se také.|  
|[Spuštění](#run)|Přetíženo. Naplánuje úlohy na `task_group` objektu. Pokud `task_handle` objekt je předán jako parametr `run`, volající zodpovídá za správu životnosti `task_handle` objektu. Provést menší a od používání verze, která přebírá odkaz na verzi metody, která přebírá odkaz na objekt funkce, jako parametr zahrnuje přidělení haldy uvnitř modulu runtime, který může být `task_handle` objektu. Verze, která přebírá parametr `_Placement` způsobí, že na tendenční směrem k provádění v místě určeném v parametru úlohy.|  
|[run_and_wait](#run_and_wait)|Přetíženo. Naplánuje úlohy spustit vložené na kontext volání za pomoci `task_group` objekt pro zrušení plnou podporu. Funkce vyčká, dokud všechny práce na `task_group` objekt buď dokončí nebo byla zrušena. Pokud `task_handle` objekt je předán jako parametr `run_and_wait`, volající zodpovídá za správu životnosti `task_handle` objektu.|  
|[Počkej](#wait)|Počká, dokud nebudou všechny práce na `task_group` objekt buď dokončí nebo byla zrušena.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od velmi omezeném `structured_task_group` třídy, `task_group` třídy je mnohem více obecné konstrukce. Nemá žádný z těchto omezení popsal [structured_task_group](structured-task-group-class.md). `task_group` objekty může bezpečně použít napříč vlákny a využít způsoby volného tvaru. Nevýhodou `task_group` konstruktor je, že nemusí fungovat stejně jako `structured_task_group` vytvořit pro úlohy, které provádějí malé množství práce.  
  
 Další informace najdete v tématu [paralelismus](../task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task_group`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="cancel"></a> Zrušit 

 Díky nezaručené pokus o zrušení podstromě pracovní kořenovým adresářem v této skupině úloh. Každá úloha naplánována na skupinu úloh bude zrušena přechodně Pokud je to možné.  
  
```  
void cancel();  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../cancellation-in-the-ppl.md).  
  
##  <a name="is_canceling"></a> is_canceling – 

 Určuje, jestli je skupina úloh aktuálně uprostřed zrušením informuje volající. Neznamená to nutně, který `cancel` byla volána metoda `task_group` objektu (i když například jistě kvalifikuje tuto metodu za účelem vrácení `true`). To může být případ, který `task_group` objektu je probíhá vloženě a další skupinu úloh nahoru ve stromové struktuře práce byla zrušena. V případech, jako jsou tyto kde můžete určit modul runtime zrušení budou směrovat přes to předem `task_group` objektu, `true` vrátí se také.  
  
```  
bool is_canceling();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, zda `task_group` objekt je uprostřed zrušení (nebo je zaručeno, že bude za chvíli).  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../cancellation-in-the-ppl.md).  
  
##  <a name="run"></a> Spuštění 

 Naplánuje úlohy na `task_group` objektu. Pokud `task_handle` objekt je předán jako parametr `run`, volající zodpovídá za správu životnosti `task_handle` objektu. Provést menší a od používání verze, která přebírá odkaz na verzi metody, která přebírá odkaz na objekt funkce, jako parametr zahrnuje přidělení haldy uvnitř modulu runtime, který může být `task_handle` objektu. Verze, která přebírá parametr `_Placement` způsobí, že na tendenční směrem k provádění v místě určeném v parametru úlohy.  
  
```  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func  
);  
  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func,  
   location& _Placement  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle,  
   location& _Placement  
);  
```  
  
### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ objektu funkce, která bude volána k provedení tělo popisovač úkolu.  
  
*_Func*<br/>
Funkce, která bude volána k vyvolání tělo úkolu. To může být výraz lambda nebo jiného objektu, která podporuje verzi operátoru volání funkce s podpisem `void operator()()`.  
  
*_Umístění.*<br/>
Odkaz na umístění, ve kterém úloha reprezentována `_Func` parametrů by se měl spustit.  
  
*_Task_handle*<br/>
Popisovač se plánované práce. Všimněte si, že má volající odpovědnost za dobu života tohoto objektu. Modul runtime bude očekávat, že chcete za provozu, dokud buď `wait` nebo `run_and_wait` byla volána metoda v tomto `task_group` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime plánuje spouštění na pozdější dobu, což může být po volání funkce vrátí zadaný pracovní funkce. Tato metoda používá [task_handle –](task-handle-class.md) objekt pro uložení kopie zadané pracovní funkce. Proto změny stavu, ke kterým dochází v objekt funkce, který můžete předat této metodě se nezobrazí v kopii tohoto objektu funkce. Kromě toho Ujistěte se, že doba platnosti objektů, které můžete předat ukazatelem nebo odkazem na pracovní funkce nadále platné, dokud pracovní funkce vrátí.  
  
 Pokud `task_group` destructs v důsledku uvolnění z výjimky zásobníku, nepotřebujete k zajištění, že má bylo provedeno volání buď `wait` nebo `run_and_wait` metody. V takovém případě se zrušit a čekání na úlohu reprezentována destruktor odpovídajícím způsobem `_Task_handle` parametr dokončit.  
  
 Metoda vyvolá [invalid_multiple_scheduling –](invalid-multiple-scheduling-class.md) výjimku, pokud úloha zpracování určené pomocí `_Task_handle` parametr již byla plánována do objektu skupiny úloh prostřednictvím `run` – metoda a jestli se žádné intervenující volání na buď `wait` nebo `run_and_wait` metoda na této skupině úloh.  
  
##  <a name="run_and_wait"></a> run_and_wait – 

 Naplánuje úlohy spustit vložené na kontext volání za pomoci `task_group` objekt pro zrušení plnou podporu. Funkce vyčká, dokud všechny práce na `task_group` objekt buď dokončí nebo byla zrušena. Pokud `task_handle` objekt je předán jako parametr `run_and_wait`, volající zodpovídá za správu životnosti `task_handle` objektu.  
  
```  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   const _Function& _Func  
);  
```  
  
### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ objektu funkce, která bude volána k provedení tělo úkolu.  
  
*_Task_handle*<br/>
Popisovač pro úlohy, které se používají ke spouštění vložený kontext volání. Všimněte si, že má volající odpovědnost za dobu života tohoto objektu. Modul runtime bude pokračovat očekávat, že živé až `run_and_wait` metoda dokončí provádění.  
  
*_Func*<br/>
Funkce, která bude volána k vyvolání tělo práce. To může být výraz lambda nebo jiného objektu, která podporuje verzi operátoru volání funkce s podpisem `void operator()()`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, jestli bylo čekání uspokojeno nebo skupina úloh se zrušila, kvůli operaci zrušit explicitní nebo výjimky z jednoho z jejích úkolů. Další informace najdete v tématu [task_group_status –](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jedna nebo více úloh naplánovaných pro toto `task_group` objekt může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více následujících úloh naplánovaných pro toto `task_group` objekt dojde k výjimce, modul runtime vybere jeden takový výjimka jeho výběru a šířit z volání `run_and_wait` metody.  
  
 Po návratu z `run_and_wait` metoda `task_group` objektu, modul runtime obnoví objekt do čistého stavu, kde ho můžete znovu použít. Jedná se o tento případ kde `task_group` byl zrušen.  
  
 V ostatním cesta spuštění, je nutné pověření k buď tuto metodu volat nebo `wait` metody před destruktor `task_group` spustí.  
  
##  <a name="ctor"></a> task_group – 

 Sestaví nový `task_group` objektu.  
  
```  
task_group();  
  
task_group(  
   cancellation_token _CancellationToken  
);  
```  
  
### <a name="parameters"></a>Parametry  
*_CancellationToken*<br/>
Token zrušení pro přidružení k této skupině úloh. Skupiny úloh se zruší, pokud je token zrušen.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří konstruktor, který přijímá token zrušení `task_group` , která budou zrušeny při zrušení zdroje přidružené k tokenu. Také poskytuje explicitní rušícího tokenu izoluje této skupiny úloh ze implicitní zrušení z nadřazené skupiny s tokenem jiný nebo žádný token.  
  
##  <a name="dtor"></a> ~ task_group – 

 Odstraní `task_group` objektu. Očekává se, že volání buď `wait` nebo `run_and_wait` metodu na objekt před destruktor prováděný, pokud je destruktor se provádí v důsledku uvolnění z důvodu výjimky zásobníku.  
  
```  
~task_group();  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud spuštění destruktoru v důsledku normálního provedení (například není uvolnění zásobníku z důvodu výjimky) a ani `wait` ani `run_and_wait` metod, destruktor může vyvolat [missing_wait –](missing-wait-class.md) došlo k výjimce.  
  
##  <a name="wait"></a> Počkej 

 Počká, dokud nebudou všechny práce na `task_group` objekt buď dokončí nebo byla zrušena.  
  
```  
task_group_status wait();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, jestli bylo čekání uspokojeno nebo skupina úloh se zrušila, kvůli operaci zrušit explicitní nebo výjimky z jednoho z jejích úkolů. Další informace najdete v tématu [task_group_status –](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jedna nebo více úloh naplánovaných pro toto `task_group` objekt může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více následujících úloh naplánovaných pro toto `task_group` objekt dojde k výjimce, modul runtime vybere jeden takový výjimka jeho výběru a šířit z volání `wait` metody.  
  
 Volání `wait` na `task_group` objekt se obnoví do čistého stavu, kde ho můžete znovu použít. Jedná se o tento případ kde `task_group` byl zrušen.  
  
 V ostatním cesta spuštění, je nutné pověření k buď tuto metodu volat nebo `run_and_wait` metody před destruktor `task_group` spustí.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [structured_task_group – třída](structured-task-group-class.md)   
 [task_handle – třída](task-handle-class.md)