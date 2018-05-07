---
title: Chyba kompilátoru prostředků RC2101 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2101
dev_langs:
- C++
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b07f6211e1cc36bd471b04126e724e42eb610641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2101"></a>Chyba kompilátoru prostředků RC2101
Neplatný direktivě v souboru předběžně zpracované RC  
  
 Kompilátor prostředků soubor obsahuje **#pragma** – direktiva.  
  
 Použití **#ifndef** direktivy preprocesoru s RC_INVOKED konstanta, že kompilátor prostředků definuje, pokud ho zpracuje vloženého souboru. Místo **#pragma** direktivy uvnitř bloku kódu, které nejsou předmětem zpracování, pokud je definován RC_INVOKED konstanta. Kód v bloku je zpracovat pouze kompilátor C/C++ a ne kompilátor prostředků. Následující vzorový kód ukazuje tento postup:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma** direktivy preprocesoru nemá žádný význam. RC soubor. **#Include** direktivy preprocesoru se často v používá. RC soubor zahrnout soubor hlaviček (soubor projektu na základě vlastní hlavičky nebo standardní hlavičku souborů dodaných společností Microsoft s jedním z jeho produktů). Některé z těchto zahrnout soubory obsahují **#pragma** – direktiva. Protože soubor záhlaví může obsahovat jeden nebo více další hlavičkové soubory, soubor, který obsahuje je problematický **#pragma** – direktiva nemusí být hned zjevné.  
  
 **#Ifndef** RC_INVOKED technika můžete řídit včetně soubory hlaviček v projektu na základě hlavičkových souborů.