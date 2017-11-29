---
title: "Zahrnutí názvů souboru v závorkách | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f118417a7ed2fdf8cad77775e144b81655c56916
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="including-bracketed-filenames"></a>Zahrnutí názvů souboru v závorkách
**ANSI 3.8.2** metodu pro lokalizaci includable zdrojové soubory  
  
 Pro specifikace souborů uzavřených do ostrých závorek preprocesor neprohledává adresáře nadřazených souborů. Soubor "nadřazená" je soubor, který má [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivy v ní. Místo toho se začíná vyhledáním souboru v adresářích určených příkazovým řádkem kompilátoru za možností /I. Pokud není k dispozici možnost /I nebo selže, preprocesor používá proměnnou prostředí pro zahrnutí nalézt žádné soubory zahrnout v rámci lomené závorky. Proměnné prostředí zahrnout může obsahovat více cest oddělený středníkem (**;**). Pokud se více než jeden adresář se zobrazí jako součást možnost /I nebo v rámci proměnné prostředí zahrnout, preprocesor je prohledává v pořadí, ve kterém jsou zobrazeny.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)