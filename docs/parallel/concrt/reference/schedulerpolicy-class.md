---
title: "SchedulerPolicy – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs:
- C++
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fc8873fc4516b3c79685eacc91d3d4426b80901
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy – třída
`SchedulerPolicy` Třída obsahuje sadu páry klíč/hodnota, jeden pro každý prvek zásady, které řídí chování instance plánovače.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class SchedulerPolicy;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SchedulerPolicy](#ctor)|Přetíženo. Vytvoří novou zásadu Plánovač a naplní s hodnotami pro [zásad klíče](concurrency-namespace-enums.md) nepodporuje plánovače Concurrency Runtime a správce prostředků.|  
|[~SchedulerPolicy Destructor](#dtor)|Zničí zásad plánovače.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|Načte hodnotu klíče zásad zadán jako `key` parametr.|  
|[Setconcurrencylimits –](#setconcurrencylimits)|Současně nastaví `MinConcurrency` a `MaxConcurrency` zásad na `SchedulerPolicy` objektu.|  
|[Setpolicyvalue –](#setpolicyvalue)|Nastaví jako zadána hodnota klíče zásad `key` parametr a vrátí původní hodnotu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Přiřadí zásady plánovače z jiné zásady plánovače.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o zásady, které se dá řídit pomocí `SchedulerPolicy` třídy najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h, concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getpolicyvalue"></a> Getpolicyvalue – 

 Načte hodnotu klíče zásad zadán jako `key` parametr.  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč zásad načíst hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud klíč určeného `key` je podporován, hodnota zásady pro klíč přetypovat `unsigned int`.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metodu [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pro klíčem neplatná zásada.  
  
##  <a name="operator_eq"></a> operátor = 

 Přiřadí zásady plánovače z jiné zásady plánovače.  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>Parametry  
 `_RhsPolicy`  
 Zásada přiřazení k této zásadě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na zásady plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Často je nejpohodlnější způsob, jak definovat nové zásady plánovače zkopírujte existující zásady a upravit pomocí `SetPolicyValue` nebo `SetConcurrencyLimits` metody.  
  
##  <a name="ctor"></a> SchedulerPolicy 

 Vytvoří novou zásadu Plánovač a naplní s hodnotami pro [zásad klíče](concurrency-namespace-enums.md) nepodporuje plánovače Concurrency Runtime a správce prostředků.  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>Parametry  
 `_PolicyKeyCount`  
 Počet klíč/hodnota páry následujících `_PolicyKeyCount` parametr.  
  
 `_SrcPolicy`  
 Zdrojová zásada pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktoru vytvoří nové zásady plánovače, kde všechny zásady, budou inicializována na jejich výchozí hodnoty.  
  
 Druhý konstruktor vytvoří novou zásadu scheduler, která používá styl s názvem parametru inicializace. Hodnoty po `_PolicyKeyCount` je zadán parametr jako páry klíč/hodnota. Žádné zásady klíč, který není zadaný v tomto konstruktoru bude mít výchozí hodnotu. Tento konstruktor může vyvolat výjimky [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) nebo [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).  
  
 Třetí konstruktor je kopírovacího konstruktoru. Často je nejpohodlnější způsob, jak definovat nové zásady plánovače zkopírujte existující zásady a upravit pomocí `SetPolicyValue` nebo `SetConcurrencyLimits` metody.  
  
##  <a name="dtor"></a> ~ SchedulerPolicy 

 Zničí zásad plánovače.  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits">Setconcurrencylimits –</a> 

 Současně nastaví `MinConcurrency` a `MaxConcurrency` zásad na `SchedulerPolicy` objektu.  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>Parametry  
 `_MinConcurrency`  
 Hodnota `MinConcurrency` klíč zásad.  
  
 `_MaxConcurrency`  
 Hodnota `MaxConcurrency` klíč zásad.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá výjimku [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) Pokud je hodnota zadaná u `MinConcurrency` je větší než zadaná pro zásady `MaxConcurrency` zásad.  
  
 Můžete také vyvolat metodu [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pro ostatní neplatné hodnoty.  
  
##  <a name="setpolicyvalue">Setpolicyvalue –</a> 

 Nastaví jako zadána hodnota klíče zásad `key` parametr a vrátí původní hodnotu.  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Zásady klíč k nastavení hodnoty.  
  
 `value`  
 Hodnota k nastavení zásad klíč.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud klíč určeného `key` je podporován, stará hodnota zásady pro klíč přetypovat `unsigned int`.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metodu [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) klíčem neplatná zásada nebo všechny zásady klíč, jehož hodnota nemůže být nastavena pomocí `SetPolicyValue` metoda.  
  
 Vyvolá metodu [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pro hodnotu, která není podporována pro klíč zadaný pomocí `key` parametr.  
  
 Všimněte si, že tato metoda není možné nastavit `MinConcurrency` nebo `MaxConcurrency` zásady. Pokud chcete nastavit tyto hodnoty, použijte [setconcurrencylimits –](#setconcurrencylimits) metoda.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [CurrentScheduler – třída](currentscheduler-class.md)   
 [Scheduler – třída](scheduler-class.md)   
 [Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



