---
title: "Criticalsection::trylock – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs: C++
helpviewer_keywords: TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2bd717e3a91d2e0210adced36e33a89f3752fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock – metoda
Pokusy o zadání kritická sekce bez blokování. Pokud je volání úspěšné, volající vlákno převezme vlastnictví kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cs`  
 Objekt zadaného uživatelem kritická sekce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obsahuje nenulovou hodnotu, pokud byly úspěšně uloženy kritická sekce nebo aktuální vlákno již vlastní kritická sekce. Nula, pokud jiné vlákno již vlastní kritická sekce.  
  
## <a name="remarks"></a>Poznámky  
 První **trylock –** funkce ovlivňuje aktuální objekt kritická sekce. Druhý **trylock –** funkce ovlivňuje kritická sekce zadaného uživatelem.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [CriticalSection – třída](../windows/criticalsection-class.md)