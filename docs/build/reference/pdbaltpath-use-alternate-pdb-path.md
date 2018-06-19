---
title: -PDBALTPATH (použít alternativní cestu PDB) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbaltpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dec06c3d6a8a981a059f173700e716431acc53a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374086"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (Použít alternativní cestu PDB)
```  
/PDBALTPATH:pdb_file_name  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *pdb_file_name*  
 Název a cesta k souboru pro soubor .pdb.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této možnosti můžete zadat alternativní umístění souboru databáze programu (.pdb) v kompilovaném binární soubor. Za normálních okolností linkeru zaznamenává umístění souboru PDB v binárních souborech, které vytvoří. Tuto možnost můžete zadejte jinou cestu a název souboru pro soubor .pdb. Informace poskytnuté s /PDBALTPATH nezmění umístění nebo název souboru skutečné pdb; změní informace, které linkeru zápisů v binární soubor. To umožňuje zadejte cestu, která je nezávislá strukturu souborů sestavení počítače. Dvě běžné používá pro tuto možnost mají zadejte síťovou cestu nebo soubor, který nemá žádné informace o cestě.  
  
 Hodnota *pdb_file_name* může být libovolný řetězec, proměnné prostředí, nebo **_PDB %**. Linkeru rozbalit proměnné prostředí, například **% SystemRoot %**, na jeho hodnotu. Proměnné prostředí definuje linkeru **_PDB %** a **_EXT %**. **% _PDB %** zasahuje do souboru PDB skutečné bez jakýchkoli informací o cestě název souboru a **_EXT %** , je rozšíření generovaného spustitelný soubor.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/PDBPATH](../../build/reference/pdbpath.md)