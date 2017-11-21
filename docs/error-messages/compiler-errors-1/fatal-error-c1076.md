---
title: "Závažná chyba C1076 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1076
dev_langs: C++
helpviewer_keywords: C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e912cc4910ab1362719d94f374f145e90747e69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1076"></a>Závažná chyba C1076
Omezení kompilátoru: bylo dosaženo limitu interní haldy; pomocí parametru /Zm nastavte vyšší limit  
  
 Tuto chybu může způsobovat příliš mnoho symbolů nebo příliš mnoho instancí šablony.  
  
 Vyřešení této chyby:  
  
1.  Použití [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) možnost se nastavit limit paměti kompilátoru hodnotu zadanou v [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) chybová zpráva. Další informace, která zahrnuje jak nastavit tuto hodnotu [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)], najdete v části poznámky v [/Zm (zadat paměti omezení přidělení předkompilované hlavičky)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).  
  
2.  Pokud používáte 32bitové hostované kompilátory v 64bitovém operačním systému, použijte místo nich 64bitové hostované kompilátory. Další informace najdete v tématu [postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  Odstraňte nepotřebné vkládané soubory.  
  
4.  Odstraňte nepotřebné globální proměnné – například dynamickým přidělením paměti namísto deklarování velkého pole.  
  
5.  Odstraňte nepoužité deklarace.  
  
6.  Rozsáhlé funkce rozdělte na menší funkce.  
  
7.  Rozsáhlé třídy rozdělte na menší třídy.  
  
8.  Aktuální soubor rozdělte na menší soubory.  
  
 Pokud dojde k C1076, okamžitě po spuštění sestavení, je hodnota zadaná u **/Zm** je pravděpodobně příliš vysoká. k aplikaci. Snížit **/Zm** hodnotu.