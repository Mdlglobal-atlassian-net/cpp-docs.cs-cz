---
title: "Mutex::mutex – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs: C++
helpviewer_keywords: Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2a0187c26f8f0a170881d0b683cb462a0a24b81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex – konstruktor
Inicializuje novou instanci třídy Mutex.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Popisovač, nebo odkaz rvalue do popisovače na objekt Mutex.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje objekt Mutex od Zadaný popisovač. Druhý konstruktor inicializuje objekt Mutex od Zadaný popisovač a pak se posouvá vlastnictví mutex jako aktuální objekt Mutex.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –
 
 ## <a name="see-also"></a>Viz také
 [Mutex – třída](../windows/mutex-class1.md)