---
title: "Pracovní Archetype | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a408af2ac7de2f71c98467e08c49187c346304e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="worker-archetype"></a>Archetype pracovního procesu
Třídy, které odpovídají *pracovní* archetype zadejte kód, který proces pracovních položek ve frontě na fondu vláken.  
  
 **Implementace**  
  
 K implementaci třídy, který odpovídá této archetype, musí třída poskytují následující funkce:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Inicializace](#initialize)|Volat za účelem inicializace pracovní objekt před všechny žádosti do [Execute](#execute).|  
|[Spuštění](#execute)|Volá se při zpracování pracovní položky.|  
|[Ukončení](#terminate)|K inicializaci objektu worker po všechny požadavky byly předány volané [Execute](#execute).|  
  
|Definice TypeDef|Popis|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Definice typu pro typ pracovní položky, která může být zpracována podle třídy pracovního procesu.|  
  
 Typické *pracovní* třída vypadá takto:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Existující implementace**  
  
 Tyto třídy vyhovovat tento archetype:  
  
|Třída|Popis|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky od fondu vláken a předává je na objekt pracovního procesu, který je vytvořen a zničen pro každý požadavek.|  
  
 **Použití**  
  
 Tyto parametry šablony očekávat třídy tak, aby odpovídala tento archetype:  
  
|Název parametru|Používá|  
|--------------------|-------------|  
|*Pracovního procesu*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*Pracovního procesu*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
Volá se při zpracování pracovní položky.  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>Parametry  
 `request`  
 Pracovní položka, která mají být zpracovány. Pracovní položky je stejného typu jako `RequestType`.  
  
 `pvWorkerParam`  
 Vlastní parametr rozumí třída pracovního procesu. Také předaný `WorkerArchetype::Initialize` a `Terminate`.  
  
 `pOverlapped`  
 Ukazatel [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) struktura používaná k vytvoření fronty, na které pracovní položky byly ve frontě.  
  
## <a name="initialize"></a>WorkerArchetype::Initialize
Volat za účelem inicializace pracovní objekt před všechny žádosti do `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 `pvParam`  
 Vlastní parametr rozumí třída pracovního procesu. Také předaný `WorkerArchetype::Terminate` a `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
## <a name="requesttype"></a>WorkerArchetype::RequestType
Definice typu pro typ pracovní položky, která může být zpracována podle třídy pracovního procesu.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Poznámky  
 Tento typ je nutné použít jako první parametr `WorkerArchetype::Execute` a musí být schopný se přetypovat do a z ULONG_PTR.  
  
## <a name="terminate"></a>WorkerArchetype::Terminate
K inicializaci objektu worker po všechny požadavky byly předány volané `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 `pvParam`  
 Vlastní parametr rozumí třída pracovního procesu. Také předaný `WorkerArchetype::Initialize` a `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Viz také  
 [Archetypes](../../atl/reference/atl-archetypes.md)   
 [Koncepty](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM plochy součásti](../../atl/atl-com-desktop-components.md)



