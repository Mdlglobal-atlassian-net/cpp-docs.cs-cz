---
title: "Závažná chyba C1103 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1103
dev_langs:
- C++
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f35bcec3b89e8e6c95740d1efb2dbbe98851f1a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1103"></a>Závažná chyba C1103
Závažná chyba při importu progid: 'zprávy.  
  
 Kompilátor zjistila potíže Import knihovny typů.  Například nelze zadat knihovny typů s progid a také určit `no_registry`.  
  
 Další informace najdete v tématu [#import – direktiva](../../preprocessor/hash-import-directive-cpp.md).  
  
 Následující příklad vytvoří C1103:  
  
```  
// C1103.cpp  
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```