---
title: Raiseexception – funkce | Microsoft Docs
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
ms.openlocfilehash: 2af97ac13386db450318f4d1f384517a8dd77baf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882180"
---
# <a name="raiseexception-function"></a>RaiseException – funkce
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 Kód výjimky výjimky vyvolaných; To znamená, HRESULT operace se nezdařila.  
  
 `dwExceptionFlags`  
 Příznak, který indikuje výjimce (hodnota příznaku je nulová), nebo noncontinuable výjimky (hodnota příznaku je nenulové hodnoty). Ve výchozím nastavení je výjimka noncontinuable.  
  
## <a name="remarks"></a>Poznámky  
 Vyvolá výjimku v volající vlákno.  
  
 Další informace najdete v tématu Windows **raiseexception –** funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)