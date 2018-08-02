---
title: ClassFactory::Release – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 49da2002-f9d6-4d7f-8a65-48c20b1bf99f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 293c95bb95feb1fa021fa742a90939c6680e7b0d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460638"
---
# <a name="classfactoryrelease-method"></a>ClassFactory::Release – metoda
Sníží počet odkaz pro aktuální **ClassFactory –** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ClassFactory – třída](../windows/classfactory-class.md)