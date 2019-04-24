---
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: f29b8e61fbfbdb0f373e3e7510cb3f1fe0b9cc2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319847"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru .dll nebo .exe, pro které chcete najít odpovídající soubor PDB.

**: PODROBNÉ**<br/>
(Volitelné) Oznámí všechny adresáře, ve kterém byl proveden pokus o najít soubor .pdb.

## <a name="remarks"></a>Poznámky

/ PDBPATH bude hledat podél stejné cesty, které ladicí program bude hledat soubor .pdb a oznámí odpovídajících, pokud existuje, soubory s příponou .pdb do souboru zadaného v počítači *filename*.

Při používání ladicího programu sady Visual Studio, může dojít k potížím, skutečnost, že ladicí program používá soubor PDB pro jinou verzi souboru, který ladíte.

/ PDBPATH bude hledat soubory s příponou .pdb v následujících umístěních:

- Zkontrolujte umístění, ve které se nachází spustitelný soubor.

- Zkontrolujte umístění zapsané do spustitelného souboru PDB. Toto je obvykle umístění v době, kdy byl propojený obrázek.

- Zkontrolujte podél cesty pro hledání nakonfigurovaný v integrovaném vývojovém prostředí sady Visual Studio.

- Zkontrolujte podél cest v _NT_SYMBOL_PATH a _NT_ALT_SYMBOL_PATH proměnné prostředí.

- Zkontrolujte v adresáři Windows.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)<br/>
[/PDBALTPATH (použití alternativní cesty PDB)](pdbaltpath-use-alternate-pdb-path.md)
