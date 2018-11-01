---
title: Příkazová makra a makra možností
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: f18cfd6ada235485a5fe47bdc94b49631b9abbbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601302"
---
# <a name="command-macros-and-options-macros"></a>Příkazová makra a makra možností

Příkazová makra jsou předdefinované pro produkty společnosti Microsoft. Makra možností představují možnosti k těmto produktům a nejsou definovaná ve výchozím nastavení. Obě se používají předdefinované odvozených pravidel a můžete používat v blocích popisů nebo uživatelem definované odvozená pravidla. Příkazová makra lze redefinovat představující část nebo všechny z příkazového řádku, včetně možnosti. Makra možností vygenerovat řetězec s hodnotou null v případě Nedefinováno.

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