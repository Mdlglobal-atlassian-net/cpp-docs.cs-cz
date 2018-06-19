---
title: Extrahování člena knihovny | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc0dc67a6d9e4a3ff61aa3b82ac10b9eabcb94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371239"
---
# <a name="extracting-a-library-member"></a>Extrahování člena knihovny
Můžete vytvořit soubor objektu (.obj), který obsahuje kopii členem existující knihovny LIB. K extrakci kopii členem, použijte následující syntaxi:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 Tento příkaz vytvoří soubor .obj názvem *objectfile* obsahující kopii `member` z *knihovny*. `member` Název je malá a velká písmena. Můžete rozbalit pouze jednoho člena v jednom příkazu. / Out možnost je povinná; neexistuje žádný výchozí název výstupu. Pokud soubor nazývá *objectfile* již existuje v adresáři zadané (nebo aktuální adresář, je-li zadán žádný adresář s *objectfile*), extrahované *objectfile*nahradí existující soubor.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)