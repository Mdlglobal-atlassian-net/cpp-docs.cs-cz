---
title: Chyba kompilátoru prostředků RW2001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 077260b615d0a5adf32278d8857df5b8f74b7e5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321097"
---
# <a name="resource-compiler-error-rw2001"></a>Chyba kompilátoru prostředků RW2001
Neplatný direktivě v souboru předběžně zpracované RC  
  
 RC soubor obsahuje **#pragma** – direktiva.  
  
 Použití **#ifndef** direktivy preprocesoru s **RC_INVOKED** konstantní, že kompilátor prostředků definuje, pokud ho zpracuje vloženého souboru. Místo **#pragma** direktivy uvnitř bloku kódu, který není při zpracování **RC_INVOKED** je definována konstanta. Kód v bloku je zpracovat pouze kompilátor C/C++ a ne kompilátor prostředků. Následující vzorový kód ukazuje tento postup:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma** direktivy preprocesoru nemá žádný význam. RC soubor. **#Include** direktivy preprocesoru se často v používá. RC soubor zahrnout soubor hlaviček (soubor projektu na základě vlastní hlavičky nebo standardní hlavičku souborů dodaných společností Microsoft s jedním z jeho produktů). Některé z těchto zahrnout soubory obsahují **#pragma** – direktiva. Protože soubor záhlaví může obsahovat jeden nebo více další hlavičkové soubory, soubor, který obsahuje je problematický **#pragma** – direktiva nemusí být hned zjevné.  
  
 **#Ifndef RC_INVOKED** technika můžete řídit včetně soubory hlaviček v projektu na základě hlavičkových souborů.