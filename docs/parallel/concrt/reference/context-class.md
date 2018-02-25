---
title: "Třída kontextu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
dev_langs:
- C++
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9195ec68a47e2ed528a42bb018cfba6316101a0c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="context-class"></a>Context – třída
Představuje abstrakci pro kontextu spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class Context;
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~Context Destructor](#dtor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Blok](#block)|Blokuje aktuálního kontextu.|  
|[CurrentContext](#currentcontext)|Vrací ukazatel na aktuálním kontextu.|  
|[Getid –](#getid)|Vrátí identifikátor pro kontext, který je jedinečná v rámci scheduler, do které patří kontextu.|  
|[GetScheduleGroupId](#getschedulegroupid)|Vrátí identifikátor pro skupinu plán, kontext právě pracuje.|  
|[GetVirtualProcessorId](#getvirtualprocessorid)|Vrátí identifikátor virtuální procesor, který kontextu je právě prováděných v.|  
|[ID](#id)|Vrátí identifikátor pro aktuální kontext, který je jedinečné v rámci scheduler, do které patří aktuální kontext.|  
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Vrátí informace, zda kolekce úloh, které je právě prováděných vložené v aktuálním kontextu je in the midst of active zrušení (nebo bude zanedlouho).|  
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Určuje, zda kontext je blokovaný synchronně. Synchronně zablokuje, pokud explicitně provedli akci, která vedla k blokování považuje za kontextu.|  
|[Přidělit nadměrnému počtu procesů](#oversubscribe)|Další virtuální procesor vloží do plánovače po dobu trvání blok kódu při vyvolání na kontext provádění na jednom z virtuálních procesorů v této plánovače.|  
|[ScheduleGroupId](#schedulegroupid)|Vrátí identifikátor pro aktuální kontext pracuje na skupině plán.|  
|[Odblokování](#unblock)|Odblokuje kontextu a způsobí, že aby se spustitelného.|  
|[VirtualProcessorId](#virtualprocessorid)|Vrátí identifikátor pro virtuální procesor, který spouští v aktuálním kontextu.|  
|[YIELD –](#yield)|Předá provádění, takže můžete provést další kontext. Pokud žádný další kontext je k dispozici yield k, Plánovač přispět k jiné vlákno operačního systému.|  
  
## <a name="remarks"></a>Poznámky  
 Plánovač Concurrency Runtime (najdete v části [Plánovač](scheduler-class.md)) kontexty provádění používá k provedení práce ve frontě k němu vaše aplikace. Vlákno Win32 je příkladem kontextu spuštění operačního systému Windows.  
  
 Kdykoli se rovná počet virtuálních procesorů udělit pomocí Správce prostředků úroveň souběžnosti plánovače. Virtuálního procesoru je abstrakci pro zpracování prostředků a mapy na vlákno hardwaru v základním systému. Pouze kontextu jedné Plánovač můžete spustit na virtuálních procesorů v daném okamžiku.  
  
 Je spolupráci ve své podstatě Plánovač a spouštění kontextu přispět jeho virtuálních procesorů na jiný kontext kdykoli Pokud si přeje přechod do stavu čekání. Při čekání ho ji nelze obnovit, dokud nebude k dispozici virtuální procesor od Plánovač začne její provedení.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Context`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="block"></a> Blok 

 Blokuje aktuálního kontextu.  
  
```
static void __cdecl Block();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
 Zjistí, pokud kontext volání běží na virtuálních procesorů, virtuálních procesorů jiného spustitelného kontextu spouštět ani může potenciálně vytvořte novou.  
  
 Po `Block` byla volána metoda nebo bude volán, musí spárujte ho s volání [Odblokovat](#unblock) metoda z jiné kontext spuštění v pořadí pro něj spustit znovu. Uvědomte si, že je mezi bodem, kde kód publikuje jeho kontext pro jiné vlákno, abyste mohli volat kritické období `Unblock` metoda a bod, kde volat metodu skutečné na `Block` Přišla žádost. Během této doby nesmí volání libovolné metody, které můžete zase blokovat a odblokovat vlastní důvodů (například získání zámku). Volání `Block` a `Unblock` metoda nekontrolovat Důvod blokování a odblokování. Pouze jeden objekt by měl mít vlastnictví `Block` -  `Unblock` pár.  
  
 Tuto metodu můžete vyvolat různé výjimky, včetně [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).  
  
##  <a name="dtor"></a> ~Context 

```
virtual ~Context();
```  
  
##  <a name="currentcontext"></a> CurrentContext – 

 Vrací ukazatel na aktuálním kontextu.  
  
```
static Context* __cdecl CurrentContext();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuálním kontextu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
##  <a name="getid">Getid –</a> 

 Vrátí identifikátor pro kontext, který je jedinečná v rámci scheduler, do které patří kontextu.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor pro kontext, který je jedinečná v rámci scheduler, do které patří kontextu.  
  
##  <a name="getschedulegroupid"></a> GetScheduleGroupId 

 Vrátí identifikátor pro skupinu plán, kontext právě pracuje.  
  
```
virtual unsigned int GetScheduleGroupId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor pro skupinu plánu kontextu je aktuálně pracujete.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota z této metody je okamžitou vzorkování plán skupiny, která spouští v kontextu. Pokud tato metoda je volána v jiném kontextu než aktuální kontext, hodnota může být zastaralé okamžikem, je vrácena a nelze spoléhat. Tato metoda se obvykle používá pro ladění nebo trasování pouze pro účely.  
  
##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId 

 Vrátí identifikátor virtuální procesor, který kontextu je právě prováděných v.  
  
```
virtual unsigned int GetVirtualProcessorId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud kontext je aktuálně spuštěných na virtuálních procesorů, identifikátor pro virtuální procesor, který kontextu je právě prováděných v; jinak hodnota `-1`.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota z této metody je okamžitou vzorkování virtuální procesor, který spouští v kontextu. Tato hodnota může být zastaralé okamžikem, je vrácena a nelze spoléhat. Tato metoda se obvykle používá pro ladění nebo trasování pouze pro účely.  
  
##  <a name="id"></a> Id 

 Vrátí identifikátor pro aktuální kontext, který je jedinečné v rámci scheduler, do které patří aktuální kontext.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud aktuální kontext je připojen k plánovače, identifikátor pro aktuální kontext, který je jedinečná v rámci scheduler, do které patří aktuální kontext; jinak hodnota `-1`.  
  
##  <a name="iscurrenttaskcollectioncanceling"></a> Iscurrenttaskcollectioncanceling – 

 Vrátí informace, zda kolekce úloh, které je právě prováděných vložené v aktuálním kontextu je in the midst of active zrušení (nebo bude zanedlouho).  
  
```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud plánovače je připojen k volání kontextu a skupinu úloh je prováděna úloha vložené v tomto kontextu, sdělení, zda této skupiny úloh je in the midst of active zrušení (nebo bude zanedlouho); jinak hodnota `false`.  
  
##  <a name="issynchronouslyblocked"></a> Issynchronouslyblocked – 

 Určuje, zda kontext je blokovaný synchronně. Synchronně zablokuje, pokud explicitně provedli akci, která vedla k blokování považuje za kontextu.  
  
```
virtual bool IsSynchronouslyBlocked() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jestli je blokována synchronně kontextu.  
  
### <a name="remarks"></a>Poznámky  
 Synchronně zablokuje, pokud explicitně provedli akci, která vedla k blokování považuje za kontextu. Pro přístup z více vláken Plánovač, to by znamenat přímého volání `Context::Block` metoda nebo na synchronizační objekt, který byl vytvořený pomocí `Context::Block` metoda.  
  
 Vrácená hodnota z tato metoda je okamžitou ukázka jestli kontextu synchronně blokováno. Tato hodnota může být zastaralé okamžikem, je vrácena a lze použít pouze velmi výjimečné situace.  
  
##  <a name="operator_delete"></a> delete – operátor 

 A `Context` objekt zničen interně modulem runtime. Nelze explicitně odstranit.  
  
```
void operator delete(void* _PObject);
```  
  
### <a name="parameters"></a>Parametry  
 `_PObject`  
 Ukazatel na objekt, který má být odstraněna.  
  
##  <a name="oversubscribe">Přidělit nadměrnému počtu procesů</a> 

 Další virtuální procesor vloží do plánovače po dobu trvání blok kódu při vyvolání na kontext provádění na jednom z virtuálních procesorů v této plánovače.  
  
```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```  
  
### <a name="parameters"></a>Parametry  
 `_BeginOversubscription`  
 Pokud `true`, jako ukazatel toho, že má být přidána velmi virtuálního procesoru po dobu trvání Překryvný odběr. Pokud `false`, jako ukazatel toho, že Překryvný odběr, měli byste ukončit a měla by být odebrána dříve přidané virtuálních procesorů.  
  
##  <a name="schedulegroupid"></a> ScheduleGroupId 

 Vrátí identifikátor pro aktuální kontext pracuje na skupině plán.  
  
```
static unsigned int __cdecl ScheduleGroupId();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud aktuální kontext je připojena k plánovače a funguje na skupinu plán, identifikátor pro Plánovač skupiny, kterou aktuální kontext pracuje na; jinak hodnota `-1`.  
  
##  <a name="unblock">Odblokování</a> 

 Odblokuje kontextu a způsobí, že aby se spustitelného.  
  
```
virtual void Unblock() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Je perfektně právní pro volání `Unblock` metodu pro dřívější než odpovídající volání [bloku](#block) metoda. Stejně dlouho jako volání `Block` a `Unblock` metody jsou správně spárovat, modul runtime správně zpracovává přirozené soupeření buď řazení. `Unblock` Volání přicházející před `Block` volání jednoduše Neguje účinku `Block` volání.  
  
 Existuje několik výjimek, které může být vyvolána z této metody. Pokud se pokusí volání kontextu `Unblock` metoda sám na sobě, [context_self_unblock](context-self-unblock-class.md) dojde k výjimce. Pokud volání `Block` a `Unblock` nejsou správně spárované (například dvě volání `Unblock` jsou vytvářeny pro kontext, který běží v současné době), [context_unblock_unbalanced](context-unblock-unbalanced-class.md) dojde k výjimce.  
  
 Uvědomte si, že je mezi bodem, kde kód publikuje jeho kontext pro jiné vlákno, abyste mohli volat kritické období `Unblock` metoda a bod, kde volat metodu skutečné na `Block` Přišla žádost. Během této doby nesmí volání libovolné metody, které můžete zase blokovat a odblokovat vlastní důvodů (například získání zámku). Volání `Block` a `Unblock` metoda nekontrolovat Důvod blokování a odblokování. Pouze jeden objekt by měl mít vlastnictví `Block` a `Unblock` pár.  
  
##  <a name="virtualprocessorid"></a> Virtualprocessorid – 

 Vrátí identifikátor pro virtuální procesor, který spouští v aktuálním kontextu.  
  
```
static unsigned int __cdecl VirtualProcessorId();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud aktuální kontext je připojen k plánovače, identifikátor pro virtuální procesor, který je aktuální kontext provádění na; jinak hodnota `-1`.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota z této metody je okamžitou vzorkování virtuální procesor, který spouští v aktuálním kontextu. Tato hodnota může být zastaralé okamžikem, je vrácena a nelze spoléhat. Tato metoda se obvykle používá pro ladění nebo trasování pouze pro účely.  
  
##  <a name="yield">YIELD –</a> 

 Předá provádění, takže můžete provést další kontext. Pokud žádný další kontext je k dispozici yield k, Plánovač přispět k jiné vlákno operačního systému.  
  
```
static void __cdecl Yield();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
##  <a name="yieldexecution"></a> YieldExecution 

 Předá provádění, takže můžete provést další kontext. Pokud žádný další kontext je k dispozici yield k, Plánovač přispět k jiné vlákno operačního systému.  
  
```
static void __cdecl YieldExecution();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
 Tato funkce je nového v [!INCLUDE[vs_dev14](../../../ide/includes/vs_dev14_md.md)] a je stejný jako [Yield](#yield) funkce ale není v konfliktu s makro Yield v odkazující na Windows.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Scheduler – třída](scheduler-class.md)   
 [Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



