---
title: "task_continuation_context – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
dev_langs:
- C++
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41cd6fa1dd219eb7179209839f0176deff43345c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context – třída
`task_continuation_context` Třída umožňuje určit, kam chcete pokračování spouštění. Je užitečné k použití této třídy z prostředí Windows Runtime aplikace. Pro aplikace Windows Runtime kontext provádění úkolů pokračování je určené modulem runtime a nejde konfigurovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class task_continuation_context : public details::_ContextCallback;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_current_winrt_context](#get_current_winrt_context)|Vrátí objekt úkolů pokračování kontextu, který představuje aktuální kontext winrt přístup z více vláken.|  
|[use_arbitrary](#use_arbitrary)|Vytvoří kontext pokračování úlohy, která umožňuje modulu Runtime zvolte kontext spuštění pro pokračování.|  
|[use_current](#use_current)|Vrátí objekt úkolů pokračování kontext, který představuje aktuální kontext spuštění.|  
|[use_default](#use_default)|Vytvoří výchozí úkolů pokračování kontext.|  
|[use_synchronous_execution](#use_synchronous_execution)|Vrátí objekt úkolů pokračování kontext, který představuje kontext synchronní zpracování.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  

## <a name="get_current_winrt_context"></a> get_current_winrt_context
 Vrátí objekt úkolů pokračování kontextu, který představuje aktuální kontext WinRT přístup z více vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Aktuální kontext prostředí Windows Runtime přístup z více vláken. Vrátí prázdný task_continuation_context Pokud volat z kontextu Windows Runtime.  
  
## <a name="remarks"></a>Poznámky  
 `get_current_winrt_context` Metoda zaznamená kontextu volajícího prostředí Windows Runtime přístup z více vláken. Vrátí prázdný kontext pro volající Windows Runtime.  
  
 Hodnoty vrácené `get_current_winrt_context` slouží k označení modulu runtime, by měl pokračování spouštění v modelu objektu apartment zaznamenané kontextu (STA vs MTA), bez ohledu na to, jestli je předchozí úlohou apartment vědět. Izolovaný prostor vědět úloh je úkol, který rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo úlohu, která je následníky takových úloh.  
  
 Tato metoda je podobná `use_current` metoda, ale je také k dispozici pro nativní kód C++ bez C + +/ CX rozšíření podpory. Je určena pro použití pro pokročilé uživatele zápis C + +/ CX bez ohledu na kód knihovny pro nativní a prostředí Windows Runtime volající. Pokud potřebujete tuto funkci, doporučujeme `use_current` metodu, která je k dispozici pouze C + +/ CX klientů.  
  
  
##  <a name="use_arbitrary"></a> use_arbitrary – 

 Vytvoří kontext pokračování úlohy, která umožňuje modulu Runtime zvolte kontext spuštění pro pokračování.  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kontext pokračování úlohy, která představuje libovolného umístění.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se používá tento kontext pokračování pokračování spustí v kontextu, které modul runtime rozhodne, i když je předchozí úlohou apartment vědět.  
  
 `use_arbitrary` umožňuje vypnout výchozí chování pro pokračování v úloze objektu apartment vědět vytvořené v STA  
  
 Tato metoda je pouze k dispozici pro aplikace Windows Runtime.  
  
##  <a name="use_current"></a> use_current – 

 Vrátí objekt úkolů pokračování kontext, který představuje aktuální kontext spuštění.  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuálním kontextu spuštění.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zaznamená kontextu prostředí Windows Runtime volajícího, aby pokračování lze spustit v pravém typu apartment.  
  
 Hodnoty vrácené `use_current` slouží k označení modulu runtime, by měl pokračování spouštění v kontextu zaznamenané (STA vs MTA) bez ohledu na to, zda je předchozí úlohou apartment vědět. Izolovaný prostor vědět úloh je úkol, který rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo úlohu, která je následníky takových úloh.  
  
 Tato metoda je pouze k dispozici pro aplikace Windows Runtime.  
  
##  <a name="use_default"></a> use_default – 

 Vytvoří výchozí úkolů pokračování kontext.  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí kontext pokračování.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí kontext se používá, pokud nezadáte pokračování kontextu při volání `then` metoda. Ve Windows aplikace pro systém Windows 7 a níže, a také aplikací klasické pracovní plochy v systému Windows 8 a vyšší modul runtime určuje, kde budou spuštěny při pokračování úlohy. Výchozí kontext pokračování pro pokračování v úloze vědět objektu apartment je však v aplikaci pomocí prostředí Windows Runtime, nastavení typu apartment kde `then` je volána.  
  
 Izolovaný prostor vědět úloh je úkol, který rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo úlohu, která je následníky takových úloh. Proto pokud naplánujete pokračování na objektu apartment vědět úkolu v STA Windows Runtime, pokračování bude vykonán v této STA  
  
 Pokračování na úlohu vědět-objektu apartment bude spuštěn v kontextu, které vybere modul Runtime.  

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution  
Vrátí objekt úkolů pokračování kontext, který představuje kontext synchronní zpracování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Kontext synchronní zpracování.  
  
## <a name="remarks"></a>Poznámky  
 `use_synchronous_execution` Metoda vynutí úkolů pokračování synchronně spustit v kontextu, způsobuje dokončení předchozí úlohou.  
  
 Pokud předchozí úlohou již dokončena při pokračování je připojena, pokračování spouští synchronně na kontext, který se připojí pokračování.  
  
 
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
