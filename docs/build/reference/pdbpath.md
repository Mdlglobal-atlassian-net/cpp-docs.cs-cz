---
title: -PDBPATH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 274c4a3742d99b1e4702ed332206b78dacebccbd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373665"
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
 [/PDBALTPATH (použití alternativní cesty PDB)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)