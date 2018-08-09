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
ms.openlocfilehash: 93b1c8fa12e06984a2bffdd90419c481d8897b94
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646238"
---
# <a name="activateinstance-function"></a>ActivateInstance – funkce
Zaregistruje a načte instanci zadaného typu definované v ID zadané třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
### <a name="parameters"></a>Parametry  
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