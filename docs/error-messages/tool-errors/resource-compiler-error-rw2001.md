---
title: "Chyba kompilátoru prostředků RW2001 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW2001
dev_langs: C++
helpviewer_keywords: RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91ded0f0b07e34a633229a9e7a445029f091b5bf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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