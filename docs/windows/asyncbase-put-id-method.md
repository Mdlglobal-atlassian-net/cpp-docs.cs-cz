---
title: Asyncbase::put_id – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::put_Id
dev_langs:
- C++
helpviewer_keywords:
- put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e9a0203bd0da2ea62d015264c1f4e8c58fcae66
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463191"
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id – metoda
Nastaví popisovač asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
#### <a name="parameters"></a>Parametry  
 *id*  
 Popisovač nenulovou hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; jinak E_INVALIDARG nebo E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)