---
title: Zahrnutí názvů souboru v závorkách | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ba45c21029a428784e1c8410dcf42295aa6350f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="including-bracketed-filenames"></a>Zahrnutí názvů souboru v závorkách
**ANSI 3.8.2** metodu pro lokalizaci includable zdrojové soubory  
  
 Pro specifikace souborů uzavřených do ostrých závorek preprocesor neprohledává adresáře nadřazených souborů. Soubor "nadřazená" je soubor, který má [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivy v ní. Místo toho se začíná vyhledáním souboru v adresářích určených příkazovým řádkem kompilátoru za možností /I. Pokud není k dispozici možnost /I nebo selže, preprocesor používá proměnnou prostředí pro zahrnutí nalézt žádné soubory zahrnout v rámci lomené závorky. Proměnné prostředí zahrnout může obsahovat více cest oddělený středníkem (**;**). Pokud se více než jeden adresář se zobrazí jako součást možnost /I nebo v rámci proměnné prostředí zahrnout, preprocesor je prohledává v pořadí, ve kterém jsou zobrazeny.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)