---
title: Možnosti LINK řízené kompilátorem
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: f631d0ebbbd9e60fe5d54aac6fb158461d3f4d38
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440106"
---
# <a name="compiler-controlled-link-options"></a>Možnosti LINK řízené kompilátorem

Kompilátor CL automaticky volá propojení, pokud nezadáte možnost/c. CL poskytuje určitou kontrolu nad linkerem prostřednictvím možností příkazového řádku a argumentů. Následující tabulka shrnuje funkce v CL, které ovlivňují propojování.

|Specifikace CL|Akce CL, která má vliv na odkaz|
|----------------------|---------------------------------|
|Libovolná přípona názvu souboru, která je jiná než. c,. příponu CXX,. cpp nebo. def|Předá název souboru jako vstup pro propojení.|
|*filename*. def|Průchod/DEF:*filename*. def|
|*Číslo* /f|Předává/STACK:*Number*|
|*Název souboru* /FD|Projde/PDB:*filename*|
|*Název souboru* /FE|Projde/OUT:*filename*|
|*Název souboru* /FM|Projde/MAP:*filename*|
|/Gy|Vytvoří zabalené funkce (sekvence COMDAT); povolí propojení na úrovni funkcí.|
|/LD|Projde/DLL|
|/LDd|Projde/DLL|
|/link|Předá zbytek příkazového řádku k propojení.|
|/MD nebo/MT|Umístí výchozí název knihovny v souboru. obj.|
|/MDd nebo/MTd|Umístí do souboru. obj název výchozí knihovny. Definuje symbol **_DEBUG**|
|/nologo|Projde/NOLOGO|
|/Zd|Předává/DEBUG|
|/Zi nebo/Z7|Předává/DEBUG|
|/Zl|Vynechává výchozí název knihovny ze souboru. obj.|

Další informace najdete v tématu [Možnosti kompilátoru MSVC](compiler-options.md).

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
