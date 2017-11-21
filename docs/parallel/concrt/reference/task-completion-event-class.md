---
title: "task_completion_event – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
dev_langs: C++
helpviewer_keywords: task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78c5cb9bdd1da0876abacda48000a914c884d25a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="taskcompletionevent-class"></a>task_completion_event – třída
`task_completion_event` Třída umožňuje zpozdit provádění úlohy, dokud je podmínka nebo spustit úlohu v reakci na externí událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_ResultType`  
 Typ výsledku této `task_completion_event` třídy.  
  
 `T`  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_completion_event](#ctor)|Vytvoří `task_completion_event` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[nastavení](#set)|Přetíženo. Nastaví událost dokončení úlohy.|  
|[set_exception –](#set_exception)|Přetíženo. Rozšíří výjimku na všechny úlohy přidružené k této události.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí úlohy vytvořené z události dokončení úlohy při váš scénář vyžaduje, abyste vytvoření úlohy, která se dokončí, a tím jeho pokračování pro ně naplánováno spuštění v určitém okamžiku v budoucnu. `task_completion_event` Musí mít stejný typ jako úlohu, můžete vytvořit a volání metody set u události dokončení úlohy s hodnotou typu bude přidružené úlohu dokončit a zadat tuto hodnotu v důsledku k jeho pokračování.  
  
 Pokud nikdy signalizace událostí dokončení úkolů, když je destructed budou zrušeny všechny úkoly vytvořené z něj.  
  
 `task_completion_event`chová se jako inteligentní ukazatel a mají být předány podle hodnoty.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task_completion_event`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="set"></a>nastavení 

 Nastaví událost dokončení úlohy.  
  
```
bool set(_ResultType _Result) const ;

bool set() const ;
```  
  
### <a name="parameters"></a>Parametry  
 `_Result`  
 Výsledek, který má nastavená Tato událost se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí metoda `true` Pokud bylo úspěšné. v nastavení události. Vrátí `false` Pokud události je již nastaven.  
  
### <a name="remarks"></a>Poznámky  
 Za přítomnosti více souběžných volání nebo `set`, pouze první volání bude úspěšné a její výsledek (pokud existuje) bude uložen v události dokončení úlohy. Zbývající sady jsou ignorovány a metoda vrátí hodnotu false. Když nastavíte o událost dokončení úkolů, všechny úlohy vytvořené z událostí okamžitě dokončí, a jeho pokračování, pokud existuje, bude naplánována. Úloha dokončení objekty, které mají `_ResultType` jiné než `void` předá hodnotu jejich pokračování.  
  
##  <a name="set_exception"></a>set_exception – 

 Rozšíří výjimku na všechny úlohy přidružené k této události.  
  
```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```  
  
### <a name="parameters"></a>Parametry  
 `_E`  
 `_Except`  
 `_ExceptionPtr`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="ctor"></a>task_completion_event 

 Vytvoří `task_completion_event` objektu.  
  
```
task_completion_event();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
