---
title: "Iumsthreadproxy – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs: C++
helpviewer_keywords: IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 87ac2a36c83e6b05e671c0110b054325d53fc887
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy – struktura
Abstrakci pro vlákno provádění. Pokud chcete vašeho scheduleru udělit oprávnění uživatelského režimu které lze plánovat vláken (UMS), nastavte hodnotu pro element zásad plánovače `SchedulerKind` k `UmsThreadDefault`a implementovat `IUMSScheduler` rozhraní. UMS vláken jsou pouze podporované v operačních systémech 64bitové verze Windows 7 a vyšší.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Iumsthreadproxy::entercriticalregion –](#entercriticalregion)|Voláno k zadání důležité oblasti. Když uvnitř důležité oblasti, nebude sledovat Plánovač asynchronní blokování operace, které dojít během oblasti. To znamená, že nebude znovu zadat Plánovač pro stránkování, pozastavení vláken, volání asynchronní procedur jádra (APCs) a tak dále, UMS vlákna.|  
|[Iumsthreadproxy::enterhypercriticalregion –](#enterhypercriticalregion)|Voláno k zadání technologie hyper důležité oblasti. Když uvnitř technologie hyper důležité oblasti, nebude sledovat Plánovač žádné blokování operace, které dojít během oblasti. To znamená, že plánovač nebude znovu zadat pro blokování volání funkcí, pokusy o získání zámku chyb stránek, které bloku vláken pozastavení, volání asynchronní procedur jádra (APCs) a tak dále, pro UMS vláken.|  
|[Iumsthreadproxy::exitcriticalregion –](#exitcriticalregion)|Volá, aby bylo možné ukončit důležité oblasti.|  
|[Iumsthreadproxy::exithypercriticalregion –](#exithypercriticalregion)|Volá, aby bylo možné ukončit technologie hyper důležité oblasti.|  
|[Iumsthreadproxy::getcriticalregiontype –](#getcriticalregiontype)|Vrátí jaký druh důležité oblasti proxy vlákno je v rámci. Protože technologie hyper důležité oblasti jsou nadmnožinou důležité oblasti, pokud je zadán kód důležité oblasti a pak technologie hyper důležité oblasti, `InsideHyperCriticalRegion` bude vrácen.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Ithreadproxy –](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="entercriticalregion"></a>Iumsthreadproxy::entercriticalregion – metoda  
 Voláno k zadání důležité oblasti. Když uvnitř důležité oblasti, nebude sledovat Plánovač asynchronní blokování operace, které dojít během oblasti. To znamená, že nebude znovu zadat Plánovač pro stránkování, pozastavení vláken, volání asynchronní procedur jádra (APCs) a tak dále, UMS vlákna.  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové hloubka důležité oblasti. Důležité oblasti jsou vícenásobné.  
  
##  <a name="enterhypercriticalregion"></a>Iumsthreadproxy::enterhypercriticalregion – metoda  
 Voláno k zadání technologie hyper důležité oblasti. Když uvnitř technologie hyper důležité oblasti, nebude sledovat Plánovač žádné blokování operace, které dojít během oblasti. To znamená, že plánovač nebude znovu zadat pro blokování volání funkcí, pokusy o získání zámku chyb stránek, které bloku vláken pozastavení, volání asynchronní procedur jádra (APCs) a tak dále, pro UMS vláken.  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové hloubka technologie hyper důležité oblasti. Technologie Hyper důležité oblasti jsou vícenásobné.  
  
### <a name="remarks"></a>Poznámky  
 Plánovač musí být neobvykle opatrní metody, který volá a co uzamkne ji získá v těchto oblastech. Pokud na zámku, která se nachází cokoli, co je zodpovědná za plánování plánovač bloky kódu v takové oblasti, může následovat vzájemného zablokování.  
  
##  <a name="exitcriticalregion"></a>Iumsthreadproxy::exitcriticalregion – metoda  
 Volá, aby bylo možné ukončit důležité oblasti.  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové hloubka důležité oblasti. Důležité oblasti jsou vícenásobné.  
  
##  <a name="exithypercriticalregion"></a>Iumsthreadproxy::exithypercriticalregion – metoda  
 Volá, aby bylo možné ukončit technologie hyper důležité oblasti.  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové hloubka technologie hyper důležité oblasti. Technologie Hyper důležité oblasti jsou vícenásobné.  
  
##  <a name="getcriticalregiontype"></a>Iumsthreadproxy::getcriticalregiontype – metoda  
 Vrátí jaký druh důležité oblasti proxy vlákno je v rámci. Protože technologie hyper důležité oblasti jsou nadmnožinou důležité oblasti, pokud je zadán kód důležité oblasti a pak technologie hyper důležité oblasti, `InsideHyperCriticalRegion` bude vrácen.  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ důležité oblasti proxy vlákno je v rámci.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Struktura rozhraní IUMSScheduler](iumsscheduler-structure.md)