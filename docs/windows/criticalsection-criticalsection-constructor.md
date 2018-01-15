---
title: "Criticalsection::criticalsection – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs: C++
helpviewer_keywords: CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 532a7b2e046bbdb64db118741a939dadb049f081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection – konstruktor
Inicializuje objekt synchronizace, který je podobný objekt mutex, ale mohou být využívána pouze vláken v jednom procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `spincount`  
 Počet typu číselník pro objekt kritická sekce. Výchozí hodnota je 0.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o kritické oddíly a spincounts najdete v tématu **InitializeCriticalSectionAndSpinCount** funkce v části synchronizace jejich rozhraní API systému Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [CriticalSection – třída](../windows/criticalsection-class.md)
