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
ms.openlocfilehash: 5839edd90f61f9f4aa96ea1d921d2179660be554
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461207"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo – metoda
Určuje, zda ID zadané rozhraní může být převeden na jednotlivé specializace určené parametry jiné než výchozí šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
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