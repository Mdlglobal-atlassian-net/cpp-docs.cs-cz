---
title: "Runtimeclassbaset::asiid – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs: C++
helpviewer_keywords: AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 796718c4533bf8730ca7a4c733e5809fb0fde880
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, který implementuje rozhraní ID určený parametrem `riid`.  
  
 `implements`  
 Proměnné v typu zadaném pomocí parametru šablony `T`.  
  
 `riid`  
 ID rozhraní pro načtení.  
  
 `ppvObject`  
 Pokud je tato operace úspěšná, ukazatel na ukazatel na rozhraní určený parametrem `riid`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT popisující chybu.  
  
## <a name="remarks"></a>Poznámky  
 Načte ukazatel ID specifikované rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Runtimeclassbaset – struktura](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)