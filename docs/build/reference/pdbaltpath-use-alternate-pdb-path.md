---
title: /PDBALTPATH (Použít alternativní cestu PDB)
ms.date: 11/04/2016
f1_keywords:
- /pdbaltpath
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
ms.openlocfilehash: 22bc53858aca3b037655829bd7449049971ca79f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419181"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (Použít alternativní cestu PDB)

```
/PDBALTPATH:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Název a cesta k souboru pro soubor .pdb.

## <a name="remarks"></a>Poznámky

Pomocí této možnosti můžete zadat alternativní umístění pro soubor databáze programu (PDB) v kompilované binární soubor. Za normálních okolností linkeru zaznamenává umístění souboru .pdb v binárních souborech, které vytvoří. Tuto možnost můžete zadat jinou cestu a název souboru pro soubor .pdb. Informace, opatřeného /PDBALTPATH nezmění umístění nebo název souboru PDB skutečné; změní informace, které linker zapisuje v binárním souboru. To umožňuje zadat cestu, která je nezávislá struktura souborů počítače sestavení. Dvě běžné použití této možnosti se zadejte síťovou cestu nebo soubor, který nemá žádné informace o cestě.

Hodnota *pdb_file_name* může být libovolný řetězec, proměnné prostředí, nebo **_PDB %**. Linker se rozbalí proměnné prostředí, jako například **adresáře % SystemRoot %**, na jeho hodnotu. Linker definuje proměnné prostředí **_PDB %** a **_EXT %**. **_PDB %** rozšíří na název souboru PDB skutečný soubor bez jakýchkoli informací o cestě a **_EXT %** je rozšíření generované spustitelné soubory.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)<br/>
[/PDBPATH](../../build/reference/pdbpath.md)
