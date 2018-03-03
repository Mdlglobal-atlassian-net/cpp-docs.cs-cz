---
title: -PDBPATH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ccbcedbf9cdd376fa7d9bced5c9d49542cee9f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pdbpath"></a>/PDBPATH
```  
/PDBPATH[:VERBOSE] filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Název souboru .dll nebo .exe, pro kterou chcete najít odpovídající soubor PDB.  
  
 VERBOSE (volitelné)  
 Všechny adresáře, kde byl proveden pokus o soubor .pdb vyhledejte sestavy.  
  
## <a name="remarks"></a>Poznámky  
 / PDBPATH hledat počítače podél stejné cesty, které by vyhledejte soubor .pdb ladicího programu a oznámí odpovídajících, pokud existuje, soubory PDB soubor zadaný v *filename*.  
  
 Při použití ladicího programu sady Visual Studio, může dojít k potížím, vzhledem k tomu, že ladicí program používá soubor .pdb pro jinou verzi souboru, kterou ladíte.  
  
 / PDBPATH bude hledat soubory PDB podél následující cesty:  
  
-   Zkontrolujte umístění, kde je spustitelný soubor.  
  
-   Zkontrolujte umístění PDB zapsána do spustitelného souboru. Je to obvykle umístění v době, kdy bylo propojeno bitovou kopii.  
  
-   Zkontrolujte v cestě vyhledávání nakonfigurovaný v integrovaném vývojovém prostředí sady Visual Studio.  
  
-   Zkontrolujte podél cesty v _NT_SYMBOL_PATH a _NT_ALT_SYMBOL_PATH proměnné prostředí.  
  
-   Zkontrolujte v adresáři systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/ PDBALTPATH (použít alternativní cestu PDB)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)