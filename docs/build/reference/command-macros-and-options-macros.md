---
title: Příkazová makra a makra možností
description: Popisuje Předdefinovaná makra NMAKE pro nástroje sestavení a jejich možnosti.
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303181"
---
# <a name="command-macros-and-options-macros"></a>Příkazová makra a makra možností

Makra příkazů jsou předdefinovaná pro produkty Microsoftu. Možnosti makra představují možnosti pro tyto produkty a ve výchozím nastavení nejsou definovány. Obě jsou používány v předdefinovaných pravidlech odvození a lze je použít v blocích popisu nebo uživatelsky definovaným odvozenm pravidlem. Makra příkazu lze předefinovat tak, aby reprezentovala část nebo celý příkazový řádek, včetně možností. Makra možností generují řetězec s hodnotou null, pokud není definován vlevo.

|Produkt společnosti Microsoft|Makro příkazu|Definováno jako|Možnosti makra|
|-----------------------|-------------------|----------------|-------------------|
|Assembler maker|**AS**|ml, iasnebo ml64|**AFLAGS**|
|Kompilátor jazyka C|**CC**|cl|**CFLAGS**|
|Kompilátor C++|**CPP**|cl|**CPPFLAGS**|
|Kompilátor C++|**CXX**|cl|**CXXFLAGS**|
|kompilátor prostředků|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Viz také:

[Speciální makra NMAKE](special-nmake-macros.md)
