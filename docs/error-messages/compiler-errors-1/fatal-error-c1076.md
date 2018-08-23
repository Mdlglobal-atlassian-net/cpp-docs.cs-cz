---
title: Závažná chyba C1076 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1076
dev_langs:
- C++
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c02cc55280202b9ce576dc1e771b3428837209c8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465674"
---
# <a name="fatal-error-c1076"></a>Závažná chyba C1076
Omezení kompilátoru: bylo dosaženo limitu interní haldy; pomocí parametru /Zm nastavte vyšší limit  
  
 Tuto chybu může způsobovat příliš mnoho symbolů nebo příliš mnoho instancí šablony.  
  
 Vyřešení této chyby:  
  
1.  Použití [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) možnost nastavit limit paměti kompilátoru na hodnotu zadanou v [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) chybovou zprávu. Další informace o nastavení této hodnoty v sadě Visual Studio, naleznete v části poznámky v [/Zm (zadat předkompilované hlavičky Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).  
  
2.  Pokud používáte 32bitové hostované kompilátory v 64bitovém operačním systému, použijte místo nich 64bitové hostované kompilátory. Další informace najdete v tématu [postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  Odstraňte nepotřebné vkládané soubory.  
  
4.  Odstraňte nepotřebné globální proměnné – například dynamickým přidělením paměti namísto deklarování velkého pole.  
  
5.  Odstraňte nepoužité deklarace.  
  
6.  Rozsáhlé funkce rozdělte na menší funkce.  
  
7.  Rozsáhlé třídy rozdělte na menší třídy.  
  
8.  Aktuální soubor rozdělte na menší soubory.  
  
 Pokud C1076 zobrazí okamžitě po zahájení sestavení, je hodnota zadaná u **/Zm** je pravděpodobně příliš vysoká. pro váš program. Omezit **/Zm** hodnotu.