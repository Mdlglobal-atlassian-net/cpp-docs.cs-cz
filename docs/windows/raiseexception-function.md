---
title: RaiseException – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5426d639ffb8655466239232da7672b89564bfae
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020106"
---
# <a name="raiseexception-function"></a>RaiseException – funkce
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
### <a name="parameters"></a>Parametry  
 *hr*  
 Kód výjimky výjimek vyvolaných; To znamená, HRESULT neúspěšnou operaci.  
  
 *dwExceptionFlags*  
 Příznak, který označuje výjimce (hodnota příznaku je nula), nebo noncontinuable výjimky (hodnota příznaku je nenulová). Výjimkou je ve výchozím nastavení, co vznikla nevykonatelná.  
  
## <a name="remarks"></a>Poznámky  
 Vyvolá výjimku v volajícího vlákna.  
  
 Další informace najdete v článku Windows `RaiseException` funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)