---
title: "Asyncbase::trytransitiontoerror – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs: C++
helpviewer_keywords: TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6da3d84e3e5e1ee0fd71da1cf59ec79497f81d35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError – metoda
Určuje, zda kód zadaný chyby můžete upravit stav vnitřní chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `error`  
 Chyba HRESULT.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud se změnil stav vnitřní chyba; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Tato operace změní chybový stav, jen pokud chybový stav je již nastavena na S_OK. Tato operace nemá žádný vliv, pokud chybový stav je již chyba zrušena, byla dokončena nebo uzavřený.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)