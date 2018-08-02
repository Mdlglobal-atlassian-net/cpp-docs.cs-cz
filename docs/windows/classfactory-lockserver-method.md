---
title: ClassFactory::lockserver – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 654ef60c924a14e861971c651899c8baea0300ef
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462703"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer – metoda
Zvýší nebo sníží počet podkladových objektů, které jsou sledovány aktuální **ClassFactory –** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hejna*  
 **Hodnota TRUE** se zvýší počet sledovaných objektů. **false** se sníží počet sledovaných objektů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_FAIL.  
  
## <a name="remarks"></a>Poznámky  
 ClassFactory – uchovává informace o objekty v základní instance [modulu](../windows/module-class.md) třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ClassFactory – třída](../windows/classfactory-class.md)