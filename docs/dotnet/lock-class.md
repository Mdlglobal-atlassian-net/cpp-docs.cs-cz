---
title: "Lock – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c2f2a8e371803d33a2c42508ec595681ada3bab8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lock-class"></a>lock – třída
Tato třída automatizuje trvá zámku pro synchronizaci přístup k objektu z více vláken.  Když se získá zámek a když způsobem zničena verzích zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Poznámky  
 `lock`je dostupná pouze pro objekty CLR a lze použít pouze v kódu CLR.  
  
 Interně používá třída lock <xref:System.Threading.Monitor> synchronizovat přístup. Při synchronizaci najdete v části tohoto tématu najdete podrobnější informace.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\lock.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [Zámek](../dotnet/lock.md)   
 [lock – členy](../dotnet/lock-members.md)