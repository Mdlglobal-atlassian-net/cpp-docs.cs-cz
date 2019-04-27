---
title: Konstanty atributu souboru
ms.date: 11/04/2016
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
ms.openlocfilehash: 271459c33cdcc1110222871bdca06d3f04edb497
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343794"
---
# <a name="file-attribute-constants"></a>Konstanty atributu souboru

## <a name="syntax"></a>Syntaxe

```
#include <io.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty určit aktuální atributy souboru nebo adresáři určeném funkce.

Atributy jsou reprezentované prostřednictvím následujících konstant manifestu:

|Konstanta|Popis|
|-|-|
|`_A_ARCH`| Archivovat. Nastavte vždy, když je soubor změněn a vymazat příkazem BACKUP. Hodnota: 0x20|
|`_A_HIDDEN`| Skrytý soubor. Program používá obvykle u příkazu DIR, pokud se nepoužije možnost /AH. Vrátí informace o normální soubory, jakož i soubory k tomuto atributu. Hodnota: 0x02|
|`_A_NORMAL`| Normální. Soubor může číst nebo zapsat bez omezení. Hodnota: 0x00|
|`_A_RDONLY`| Jen pro čtení. Soubor nelze otevřít pro zápis a soubor se stejným názvem nejde vytvořit. Hodnota: 0x01|
|`_A_SUBDIR`| Podadresář. Hodnota: 0x10|
|`_A_SYSTEM`| Systém souborů. Program používá obvykle u příkazu DIR, pokud se nepoužije možnost /AS. Hodnota: 0x04|

Je možné kombinovat více konstant s operátor OR (&#124;).

## <a name="see-also"></a>Viz také:

[Funkce hledání názvů souborů](../c-runtime-library/filename-search-functions.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
