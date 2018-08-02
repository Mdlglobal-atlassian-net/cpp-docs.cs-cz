---
title: Activateinstance – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 413bf73d5aeaef2c210be89f3c6f4ca3a4254ba4
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461968"
---
# <a name="activateinstance-function"></a>ActivateInstance – funkce
Zaregistruje a načte instanci zadaného typu definované v ID zadané třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ aktivace.  
  
 *activatableClassId*  
 Název ID třídy, která definuje parametr *T*.  
  
 *instance*  
 Když tato operace dokončí, odkaz na instanci *T*.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě chybu HRESULT určující příčinu chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Windows::Foundation –  
  
## <a name="see-also"></a>Viz také  
 [Windows::Foundation – obor názvů](../windows/windows-foundation-namespace.md)