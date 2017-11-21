---
title: "Závažná chyba C1104 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1104
dev_langs: C++
helpviewer_keywords: C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7a3f7fbff36f998716bc6639ccb718b1699ccf80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1104"></a>Závažná chyba C1104
Závažná chyba při importu ID knihovny: 'zprávy.  
  
 Kompilátor zjistila potíže Import knihovny typů.  Například nelze zadat knihovny typů s ID knihovny a také určit `no_registry`.  
  
 Další informace najdete v tématu [#import – direktiva](../../preprocessor/hash-import-directive-cpp.md).  
  
 Následující příklad vytvoří C1104:  
  
```  
// C1104.cpp  
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104  
```