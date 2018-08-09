---
title: Invokehelper::Invoke – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56f7f77284d855a2d9a737c8694efdd357d0a6fb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011497"
---
# <a name="invokehelperinvoke-method"></a>InvokeHelper::Invoke – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
### <a name="parameters"></a>Parametry  
 *arg1*  
 Argument 1.  
  
 *arg2*  
 Argument 2.  
  
 *arg3*  
 Argument 3.  
  
 *arg4*  
 Argument 4.  
  
 *arg5*  
 Argument 5.  
  
 *arg6*  
 Argument 6.  
  
 *arg7*  
 Argument 7.  
  
 *arg8*  
 Argument 8.  
  
 *arg9*  
 Argument 9.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.  
  
## <a name="remarks"></a>Poznámky  
 Volá obslužnou rutinu události, jehož předpis obsahuje zadaný počet argumentů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Invokehelper – struktura](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)