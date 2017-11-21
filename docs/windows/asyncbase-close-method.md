---
title: "Asyncbase::Close – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::Close
dev_langs: C++
helpviewer_keywords: Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dbdc52eec476b973c3d3549cfb0ff9413a46f6f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close – metoda
Ukončí asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud ukončí operaci, nebo je již uzavřen; v opačném E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Poznámky  
 Close() je výchozí implementaci třídy IAsyncInfo::Close a nemá žádné samotnou práci. Ve skutečnosti zavřít asynchronní operaci, potlačení OnClose() čistý virtuální metody.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)