---
title: Asweak – funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: b0f4645a6008b954833bf282971a0d3912e1d598
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653141"
---
# <a name="asweak-function"></a>AsWeak – funkce
Získá nestálý odkaz pro zadanou instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Ukazatel na typ parametru *p*.  
  
 *p*  
 Instance typu.  
  
 *pWeak*  
 Když tato operace dokončí, ukazatel na Slabý odkaz na parametr *p*.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je tato operace úspěšná; v opačném případě chybu HRESULT určující příčinu selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)