---
title: "Příkazová makra a makra možností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06f5d48395c0395a85c90096bf2dbad8627ac41a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-macros-and-options-macros"></a>Příkazová makra a makra možností
Makra příkazů jsou předdefinovány pro produkty společnosti Microsoft. Makra možností představují možnosti pro tyto produkty a nejsou definovaná ve výchozím nastavení. Jak se používají v předdefinované odvozená pravidla a mohou být používány bloky popisů nebo uživatelem definované odvozená pravidla. Makra příkazů může být předefinována představují část nebo všechny z příkazového řádku, včetně možnosti. Makra možností vygenerovat řetězec null, pokud není definovaná doleva.  
  
|Produkt společnosti Microsoft|Příkaz – Makro|Definován jako|Možnosti – makro|  
|-----------------------|-------------------|----------------|-------------------|  
|MASM|**STEJNĚ JAKO**|ml|**AFLAGS**|  
|Základní kompilátoru|**BC**|BC|**BFLAGS**|  
|Kompilátor jazyka C|**KOPIE**|cl|**CFLAGS**|  
|Kompilátor C++|**CPP**|cl|**CPPFLAGS**|  
|Kompilátor C++|**CXX**|cl|**CXXFLAGS**|  
|kompilátor prostředků|**RC**|RC|**RFLAGS**|  
  
## <a name="see-also"></a>Viz také  
 [Speciální makra NMAKE](../build/special-nmake-macros.md)