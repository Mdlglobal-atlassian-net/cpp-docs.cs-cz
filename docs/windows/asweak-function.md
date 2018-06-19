---
title: Asweak – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 039d210e9a204c485e2f44c39ea87b4d35089d88
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854821"
---
# <a name="asweak-function"></a>AsWeak – funkce
Načte slabé odkaz na zadané instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Ukazatel na typ parametru `p`.  
  
 `p`  
 Instance typu.  
  
 `pWeak`  
 Když tato operace dokončí, ukazatel na slabé odkaz na parametr `p`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je tato operace úspěšná. v opačném chybu HRESULT, která určuje příčinu selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)