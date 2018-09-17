---
title: Příkazová makra a makra možností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c66295a42fff6a2e6dde5205fb5d9139e6eceb6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705533"
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