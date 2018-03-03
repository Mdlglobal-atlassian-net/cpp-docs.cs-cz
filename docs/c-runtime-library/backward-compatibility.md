---
title: "Zpětná kompatibilita | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8ffcc5ab1f50c474ed0ecf4d014419111682b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita
Pro kompatibilitu mezi verzemi produktu, knihovna OLDNAMES. LIB mapuje názvy starého na nové názvy. Například `open` mapuje `_open`. Je nutné explicitně propojit s OLDNAMES. LIB jenom v případě, že je kompilovat s následující kombinace možností příkazového řádku:  
  
-   `/Zl`(vypuštění názvu výchozí knihovny ze souboru objektu) a `/Ze` (výchozí nastavení – pomocí rozšíření Microsoft)  
  
-   `/link`(řízení linkeru), `/NOD` (hledání žádné výchozí knihovny), a`/Ze`  
  
 Další informace o parametrech příkazového řádku kompilátoru najdete v tématu [referenční dokumentace kompilátoru](../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita](../c-runtime-library/compatibility.md)