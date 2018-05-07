---
title: Lock – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a860f79b740e0f34eef33b7a96e0236835f1f6b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lock-class"></a>lock – třída
Tato třída automatizuje trvá zámku pro synchronizaci přístup k objektu z více vláken.  Když se získá zámek a když způsobem zničena verzích zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Poznámky  
 `lock` je dostupná pouze pro objekty CLR a lze použít pouze v kódu CLR.  
  
 Interně používá třída lock <xref:System.Threading.Monitor> synchronizovat přístup. Při synchronizaci najdete v části tohoto tématu najdete podrobnější informace.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\lock.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [Zámek](../dotnet/lock.md)   
 [lock – členy](../dotnet/lock-members.md)