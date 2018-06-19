---
title: Zpětná kompatibilita | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9a04dec046435478ca621ad8f5e2e3c4323f3e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386235"
---
# <a name="backward-compatibility"></a>Zpětná kompatibilita
Pro kompatibilitu mezi verzemi produktu, knihovna OLDNAMES. LIB mapuje názvy starého na nové názvy. Například `open` mapuje `_open`. Je nutné explicitně propojit s OLDNAMES. LIB jenom v případě, že je kompilovat s následující kombinace možností příkazového řádku:  
  
-   `/Zl` (vypuštění názvu výchozí knihovny ze souboru objektu) a `/Ze` (výchozí nastavení – pomocí rozšíření Microsoft)  
  
-   `/link` (řízení linkeru), `/NOD` (hledání žádné výchozí knihovny), a `/Ze`  
  
 Další informace o parametrech příkazového řádku kompilátoru najdete v tématu [referenční dokumentace kompilátoru](../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita](../c-runtime-library/compatibility.md)