---
title: Diagnostika vytištěná podle funkce assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c219669d018dc8c4cb038e90dffd1137877f422
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert
**ANSI 4.2** diagnostiky tištěné a chování při ukončení **assert** – funkce  
  
 **Assert** funkce vytiskne diagnostické zprávy a volání **abort** rutiny, pokud výraz hodnotu false (0). Diagnostická zpráva má tvar  
  
 **Kontrolní výraz systému se nezdařilo**: *výraz ***, soubor** *filename ***, řádku** *linenumber*  
  
 kde název souboru je název zdrojového souboru a číslo řádku je číslo řádku výrazu, který v tomto zdrojovém souboru selhal. V případě, že je výraz pravdivý (nenulový), nedojde k žádné akci.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)