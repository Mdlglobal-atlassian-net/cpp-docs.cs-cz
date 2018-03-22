---
title: Weakref::weakref – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c215006412a1ab882792546e575b6f448529a652
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef – konstruktor
Inicializuje novou instanci třídy WeakRef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatelů, reference nebo deklarátor odkazu na existující objekt, který inicializuje objekt aktuální WeakRef.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje objekt WeakRef prázdný. Druhý konstruktor inicializuje objekt WeakRef od ukazatele rozhraní IWeakReference. Třetí konstruktor inicializuje objekt WeakRef z odkazů na ComPtr\<IWeakReference > objektu. Konstruktory čtvrté a páté inicializuje objekt WeakRef z jiného objektu WeakRef.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)