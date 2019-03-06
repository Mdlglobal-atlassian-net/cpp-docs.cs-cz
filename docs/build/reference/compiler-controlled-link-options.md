---
title: Možnosti LINK řízené kompilátorem
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 3fed75b18ead80b8367eb1254793d632629efeff
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426703"
---
# <a name="compiler-controlled-link-options"></a>Možnosti LINK řízené kompilátorem

CL – kompilátor automaticky volá propojení, pokud nezadáte možnost /c. CL poskytuje určitou kontrolu nad linkeru prostřednictvím parametrů příkazového řádku a argumenty. Následující tabulka shrnuje funkce, které ovlivňují propojování v CL.

|Cl – specifikace|CL akci, která má vliv na odkaz|
|----------------------|---------------------------------|
|Libovolnou příponou názvu než .c, .cxx, .cpp nebo .def|Předá název souboru jako vstup pro odkaz|
|*Název souboru*.def|/ DEF předá:*filename*.def|
|/F*číslo*|Průchody/Stack:*číslo*|
|/FD*název souboru*|Předá/pdb:*název souboru*|
|/FE*název souboru*|Předá/OUT:*název souboru*|
|/Fm*filename*|Předá parametr/map:*název souboru*|
|/Gy|Vytvoří zabalených funkcí (sekvence Comdat); Povolí propojování na úrovní funkcí|
|/LD|Předá/DLL|
|/LDd|Předá/DLL|
|/link|ODKAZ se předá zbytek příkazového řádku|
|/MD nebo/MT|Umístí do souboru .obj název výchozí knihovny|
|/ MDd nebo/MTD|Umístí do souboru .obj název výchozí knihovny. Definuje symbol **_DEBUG**|
|/nologo|/ Nologo předá|
|/Zd|Předá/Debug|
|Zi nebo/Z7|Předá/Debug|
|/Zl|Vynechá výchozí název knihovny ze souboru .obj|

Další informace najdete v tématu [– možnosti kompilátoru](../../build/reference/compiler-options.md).

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
