---
title: "Chaininterfaces::cancastto – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99738f9c5335ede5dafe60e35b3104951f5fb556
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo – metoda
Určuje, zda zadaný rozhraní ID lze převést na každý specializací definované parametry jiné než výchozí šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identifikátor rozhraní.  
  
 `ppv`  
 Ukazatel na ID poslední rozhraní, která byla úspěšně přetypování.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud se všechny operace přetypování úspěšně; v opačném `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Chaininterfaces – struktura](../windows/chaininterfaces-structure.md)