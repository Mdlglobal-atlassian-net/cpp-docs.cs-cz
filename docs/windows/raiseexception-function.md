---
title: "Raiseexception – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::RaiseException
dev_langs: C++
helpviewer_keywords: RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f64d0e38bb92f9ebe3954b47ece29184cbf1a73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)