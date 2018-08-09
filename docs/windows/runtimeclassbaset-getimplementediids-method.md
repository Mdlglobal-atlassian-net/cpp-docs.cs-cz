---
title: Runtimeclassbaset::getimplementediids – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a5c63a3b2dbbac934162f74abb8e742cc4418a7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018988"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ *implementuje* parametru.  
  
 *Implementuje*  
 Ukazatel na typ určený parametrem *T*.  
  
 *iidCount*  
 Maximální počet rozhraní ID pro načtení.  
  
 *IID*  
 Pokud se tato operace dokončí úspěšně, pole rozhraní implementovaný tímto typem ID *T*.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.  
  
## <a name="remarks"></a>Poznámky  
 Načte pole ID, které jsou implementovány pomocí zadaného typu rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClassBaseT – struktura](../windows/runtimeclassbaset-structure.md)