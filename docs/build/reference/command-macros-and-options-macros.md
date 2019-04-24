---
title: Příkazová makra a makra možností
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: c6dad7b50d265a1460a98747665d48051078163a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272435"
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

[Speciální makra NMAKE](special-nmake-macros.md)
