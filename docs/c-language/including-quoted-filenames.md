---
title: Včetně názvů souboru v uvozovkách | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80f6afbc503b52d1ef620050bf5592eb84e75fa9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383218"
---
# <a name="including-quoted-filenames"></a>Zahrnutí názvů souboru v uvozovkách
**ANSI 3.8.2** podporu uvozovkách názvy pro includable zdrojové soubory  
  
 Pokud zadáte jednoznačnou kompletní specifikaci cesty k souboru zahrnutí mezi dvě sady dvojitých uvozovek (" "), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.  
  
 Pro zadané jako soubory zahrnout [#include](../preprocessor/hash-include-directive-c-cpp.md) "cesta specifikace", adresář hledání začíná adresáře nadřazeném souboru a potom pokračuje prostřednictvím adresáře všechny soubory nadřazený. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdrojový soubor, který se právě zpracovává. Pokud není dostupný žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání bude pokračovat, jako kdyby měla název souboru uzavřené v lomených závorkách.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)