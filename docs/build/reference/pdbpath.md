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
ms.openlocfilehash: e59f36905bcb9eb379e2bc17c9041b81fd98a535
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420034"
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

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)<br/>
[/PDBALTPATH (použití alternativní cesty PDB)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)
