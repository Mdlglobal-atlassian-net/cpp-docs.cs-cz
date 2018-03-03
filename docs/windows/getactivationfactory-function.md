---
title: "Getactivationfactory – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6419ef4d48c3f151f8acfb49d40e10853f5d17f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="getactivationfactory-function"></a>GetActivationFactory – funkce
Načte objekt pro vytváření aktivace pro typ zadaný v parametru šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr šablony, který určuje typ objektu pro vytváření aktivace.  
  
 `activatableClassId`  
 Název třídy, která aktivace vytváření může vytvořit.  
  
 `factory`  
 Když tato operace dokončí, odkaz na aktivační objekt factory pro typ `T`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném chybu HRESULT, která označuje, proč jsou tato operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Windows::Foundation –  
  
## <a name="see-also"></a>Viz také  
 [Windows::Foundation – obor názvů](../windows/windows-foundation-namespace.md)