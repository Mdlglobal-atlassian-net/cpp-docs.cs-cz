---
title: Runtimeclassbaset::asiid – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1174db6702fc68b01f60491ef203265bbd6f4c14
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607424"
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ, který implementuje rozhraní ID určené parametrem *riid*.  
  
 *Implementuje*  
 Proměnné určené parametrem šablony typu *T*.  
  
 *riid*  
 ID rozhraní, který se má načíst.  
  
 *ppvObject*  
 Pokud je tato operace úspěšná, ukazatel na ukazatel na rozhraní určené parametrem *riid*.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.  
  
## <a name="remarks"></a>Poznámky  
 Načte ukazatel na ID zadané rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Runtimeclassbaset – struktura](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)