---
title: "Lock – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs: C++
helpviewer_keywords: lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2c9e21612c227081e3558a8f7f3161f922711c20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Lock – členy třídy](../dotnet/lock-members.md)