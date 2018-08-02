---
title: Criticalsection::trylock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1b9d238d4f5475475e5dc367aae196937630a0e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465419"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock – metoda
Pokusy o zadání kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno trvá vlastnictví kritický oddíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *cs*  
 Kritický oddíl uživatelem zadaného objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu, pokud byly úspěšně uloženy kritický oddíl nebo aktuální vlákno již vlastní kritický oddíl. Nula v případě jiné vlákno již vlastní kritický oddíl.  
  
## <a name="remarks"></a>Poznámky  
 První **trylock –** aktuální objekt kritický oddíl má vliv na funkce. Druhá **trylock –** funkce ovlivňuje kritickou sekci zadané uživatelem.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [CriticalSection – třída](../windows/criticalsection-class.md)