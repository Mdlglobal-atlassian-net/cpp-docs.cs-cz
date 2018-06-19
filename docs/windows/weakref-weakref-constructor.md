---
title: Weakref::weakref – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae70dabdd86fedf82c26c0c7d9a09d842e2310e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891045"
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