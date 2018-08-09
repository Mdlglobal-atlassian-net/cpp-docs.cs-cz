---
title: Criticalsection::criticalsection – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f87f95a0683f6b4440d2be8b770902a7e4ecde59
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644291"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection – konstruktor
Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může využívat pouze vláken v jednom procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *spincount*  
 Počet typu číselník pro objekt kritický oddíl. Výchozí hodnota je 0.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o kritických oddílů a spincounts, najdete v článku `InitializeCriticalSectionAndSpinCount` fungovat v **synchronizace** část jejich rozhraní Windows API.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [CriticalSection – třída](../windows/criticalsection-class.md)