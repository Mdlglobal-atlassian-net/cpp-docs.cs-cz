---
title: "Createclassfactory – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::CreateClassFactory
dev_langs: C++
helpviewer_keywords: CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5ac438e233c675b6d650af83354edd36f877602d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="createclassfactory-function"></a>CreateClassFactory – funkce
Vytvoří objekt factory, který vytváří instance pro zadanou třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 Kombinace jednoho nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnot výčtu.  
  
 `entry`  
 Ukazatel na [creatormap –](../windows/creatormap-structure.md) obsahující inicializace a registrační informace o parametru `riid`.  
  
 `riid`  
 Odkaz na rozhraní ID.  
  
 `ppFactory`  
 Pokud tato operace dokončí úspěšně, ukazatel na objekt pro vytváření tříd.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="remarks"></a>Poznámky  
 Chybu assert jsou vydávány, pokud parametr šablony `Factory` není odvozen z rozhraní IClassFactory.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Namespace Microsoft::WRL::Wrappers::details](../windows/microsoft-wrl-wrappers-details-namespace.md)