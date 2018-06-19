---
title: Kompilátoru (úroveň 1) upozornění C4041 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd8c933522e523329c41ebe666a5a7e3c198cb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286094"
---
# <a name="compiler-warning-level-1-c4041"></a>C4041 kompilátoru upozornění (úroveň 1)
omezení kompilátoru: ukončení prohlížeče výstup  
  
 Informace o prohlížeči překročil limit kompilátoru.  
  
 Toto upozornění může být způsobeno kompilujete s [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informace o prohlížeči včetně lokální proměnné).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Kompilace s /Fr (informace o prohlížeči bez místní proměnné).  
  
2.  Zakážete prohlížeče výstup (Kompilovat bez /FR nebo /Fr).