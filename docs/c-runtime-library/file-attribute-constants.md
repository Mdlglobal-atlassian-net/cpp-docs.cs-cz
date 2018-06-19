---
title: Konstanty atributu souboru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 178082356eb08130879cd3b4f2118cbf75e451ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390263"
---
# <a name="file-attribute-constants"></a>Konstanty atributu souboru
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <io.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto konstanty zadejte aktuální atributy soubor nebo adresář zadaný funkce.  
  
 Atributy jsou reprezentované pomocí následující konstanty manifestu:  
  
 `_A_ARCH`  
 Archivu. Nastavte vždy, když je soubor změnit a vymazat příkazem BACKUP. Hodnota: 0x20  
  
 `_A_HIDDEN`  
 Skrytého souboru. Se seznámili s obvykle pomocí příkazu DIR, pokud se používá možnost /AH. Vrací informace o normální soubory, jakož i soubory s tímto atributem. Hodnota: 0x02  
  
 `_A_NORMAL`  
 Normální. Soubor můžou číst nebo zapisovat do bez omezení. Hodnota: 0x00  
  
 `_A_RDONLY`  
 Jen pro čtení. Soubor nelze otevřít pro zápis a nedá se vytvořit soubor se stejným názvem. Hodnota: 0x01  
  
 `_A_SUBDIR`  
 Podadresář. Hodnota: 0x10  
  
 `_A_SYSTEM`  
 Systémový soubor. Se seznámili s obvykle pomocí příkazu DIR, pokud se používá možnost /AS. Hodnota: 0x04  
  
 Je možné kombinovat více konstant s operátor OR (&#124;).  
  
## <a name="see-also"></a>Viz také  
 [Název souboru – funkce hledání](../c-runtime-library/filename-search-functions.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)