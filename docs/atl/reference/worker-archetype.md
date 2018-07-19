---
title: Archetyp pracovního procesu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75f9e974a2969fa817598556e3e043626a826970
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881302"
---
# <a name="worker-archetype"></a>Archetyp pracovního procesu
Třídy, které odpovídají *pracovního procesu* archetype zadejte kód pro proces pracovních položek ve frontě na fond vláken.  
  
 **Implementace**  
  
 Třídy musí implementovat třídu odpovídají této archetype, poskytují následující funkce:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Initialize](#initialize)|Volána k inicializaci objektu pracovního procesu, než jsou předány žádné požadavky [Execute](#execute).|  
|[Spuštění](#execute)|Volá se, aby zpracování pracovní položky.|  
|[ukončit](#terminate)|K inicializaci objektu pracovního procesu po všechny požadavky byly předány volané [Execute](#execute).|  
  
|Definice TypeDef|Popis|  
|-------------|-----------------|  
|[Typ RequestType](#requesttype)|Definice typu pro typ pracovní položky, které mohou být zpracovány třídy pracovního procesu.|  
  
 Typické *pracovního procesu* třídy vypadá takto:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Existující implementace**  
  
 Tyto třídy splňovat toto archetype:  
  
|Třída|Popis|  
|-----------|-----------------|  
|[Cnonstatelessworker –](../../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky od fondu vláken a předává je do objektu pracovního procesu, který je vytvořeno a zničeno pro každý požadavek.|  
  
 **Použití**  
  
 Tyto parametry šablony by měl třídy tak, aby odpovídal na tomto archetype:  
  
|Název parametru|Používá|  
|--------------------|-------------|  
|*Pracovního procesu*|[Cthreadpool –](../../atl/reference/cthreadpool-class.md)|  
|*Pracovního procesu*|[Cnonstatelessworker –](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
Volá se, aby zpracování pracovní položky.  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>Parametry  
 *Požadavek*  
 Pracovní položky ke zpracování. Pracovní položka je stejného typu jako `RequestType`.  
  
 *pvWorkerParam*  
 Vlastní parametr srozumitelné pro třídu pracovního procesu. Také předat `WorkerArchetype::Initialize` a `Terminate`.  
  
 *pOverlapped*  
 Ukazatel [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) struktura používaná k vytvoření fronty, na které pracovní položky byly ve frontě.  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
Volána k inicializaci objektu pracovního procesu, než jsou předány žádné požadavky `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 *pvParam*  
 Vlastní parametr srozumitelné pro třídu pracovního procesu. Také předat `WorkerArchetype::Terminate` a `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
Definice typu pro typ pracovní položky, které mohou být zpracovány třídy pracovního procesu.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Poznámky  
 Tento typ musí být použita jako první parametr `WorkerArchetype::Execute` a musí být schopné přetypování do a z ULONG_PTR.  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
K inicializaci objektu pracovního procesu po všechny požadavky byly předány volané `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 *pvParam*  
 Vlastní parametr srozumitelné pro třídu pracovního procesu. Také předat `WorkerArchetype::Initialize` a `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../../atl/active-template-library-atl-concepts.md)   
 [Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)



