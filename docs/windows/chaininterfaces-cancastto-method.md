---
title: Chaininterfaces::cancastto – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ff24ac92e5e84cb85127ef6e33805928fabd6f60
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647528"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo – metoda
Určuje, zda ID zadané rozhraní může být převeden na jednotlivé specializace určené parametry jiné než výchozí šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Identifikátor rozhraní.  
  
 *ppv*  
 Ukazatel na poslední ID rozhraní, který byl úspěšně převeden.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud všechny operace přetypování bylo úspěšné; jinak **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)