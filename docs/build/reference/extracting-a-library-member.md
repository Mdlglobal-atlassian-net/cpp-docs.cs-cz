---
title: "Extrahování člena knihovny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Lib
dev_langs: C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38f45463bb76f858d1b88c059de57a4b8b86227e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="extracting-a-library-member"></a>Extrahování člena knihovny
Můžete vytvořit soubor objektu (.obj), který obsahuje kopii členem existující knihovny LIB. K extrakci kopii členem, použijte následující syntaxi:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 Tento příkaz vytvoří soubor .obj názvem *objectfile* obsahující kopii `member` z *knihovny*. `member` Název je malá a velká písmena. Můžete rozbalit pouze jednoho člena v jednom příkazu. / Out možnost je povinná; neexistuje žádný výchozí název výstupu. Pokud soubor nazývá *objectfile* již existuje v adresáři zadané (nebo aktuální adresář, je-li zadán žádný adresář s *objectfile*), extrahované *objectfile*nahradí existující soubor.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)