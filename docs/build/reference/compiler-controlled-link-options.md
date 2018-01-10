---
title: "Možnosti LINK řízené kompilátorem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc899fc7f1fc8c1805648e72e14ef13853841c90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-controlled-link-options"></a>Možnosti LINK řízené kompilátorem
CL – kompilátor automaticky zavolá odkaz, pokud zadáte možnost /c. CL poskytuje určitou kontrolu nad linkeru prostřednictvím možnosti příkazového řádku a argumenty. Následující tabulka shrnuje funkce v CL, které ovlivňují propojování.  
  
|Specifikace CL|CL akce, která má vliv na odkaz|  
|----------------------|---------------------------------|  
|Libovolnou příponou názvu než .c .cxx, sada nebo .def|Předá název souboru jako vstup pro odkaz|  
|*Název souboru*.def|/ DEF předá:*filename*.def|  
|/F*číslo*|Předává /STACK:*číslo*|  
|/FD*filename*|/ Pdb předá:*filename*|  
|/FE*filename*|Předá/OUT:*filename*|  
|/FM*filename*|/ Map předává:*filename*|  
|/Gy|Vytvoří zabalené funkce (COMDATs); Povolí propojení na úrovni – funkce|  
|/LD|Předá/DLL|  
|/ LDd|Předá/DLL|  
|/link|Předává zbytek příkazového řádku pro odkaz|  
|/MD nebo/MT|V souboru .obj umístí názvu výchozí knihovny|  
|/ MDd nebo /MTd|V souboru .obj umístí názvu výchozí knihovny. Definuje symbol **_DEBUG –**|  
|/nologo|/ Nologo předá|  
|/Zd|Předává/Debug|  
|/Zi nebo /Z7|Předává/Debug|  
|/Zl|Vynechá názvu výchozí knihovny ze souboru .obj|  
  
 Další informace najdete v tématu [– možnosti kompilátoru](../../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)