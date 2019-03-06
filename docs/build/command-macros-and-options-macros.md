---
title: Příkazová makra a makra možností
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: daf8c243f95f7cc12a3d3b1c5cf16f5a384c9671
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418294"
---
# <a name="command-macros-and-options-macros"></a>Příkazová makra a makra možností

Příkazová makra jsou předdefinované pro produkty společnosti Microsoft. Makra možností představují možnosti k těmto produktům a nejsou definovaná ve výchozím nastavení. Obě se používají předdefinované odvozených pravidel a můžete používat v blocích popisů nebo uživatelem definované odvozená pravidla. Příkazová makra lze redefinovat představující část nebo všechny z příkazového řádku, včetně možnosti. Makra možností vygenerovat řetězec s hodnotou null v případě Nedefinováno.

|Produkt společnosti Microsoft|Příkaz – Makro|Definován jako|Možnosti – makro|
|-----------------------|-------------------|----------------|-------------------|
|MASM|**AS**|ml|**AFLAGS**|
|Základní kompilátoru|**BC**|bc|**BFLAGS**|
|Kompilátor jazyka C|**CC**|cl|**CFLAGS**|
|Kompilátor C++|**CPP**|cl|**CPPFLAGS**|
|Kompilátor C++|**CXX**|cl|**CXXFLAGS**|
|kompilátor prostředků|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Viz také:

[Speciální makra NMAKE](../build/special-nmake-macros.md)
