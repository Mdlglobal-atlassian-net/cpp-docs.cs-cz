---
title: "CL vyvolává Linker | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32a3bdd1e227b894ca5a32ddfaa8c46a478a19f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cl-invokes-the-linker"></a>CL vyvolává linker
CL vyvolává linker automaticky po kompilování, pokud se používá možnost /c. CL předá linkeru názvů .obj soubory vytvořené během kompilace a názvy všechny další soubory zadané na příkazovém řádku. Linkeru používá možnosti uvedené v proměnném prostředí odkaz. Možnost/Link můžete použít k určení možnosti linkeru na příkazovém řádku CL. Možnosti, které následují možnosti/Link přepíšou nastavení v proměnné prostředí odkaz. Možnosti v následující tabulce potlačit propojení.  
  
|Možnost|Popis|  
|------------|-----------------|  
|/c|Kompilovat bez propojení|  
|/ /P E, /EP,|Předběžné zpracování bez kompilování a propojování|  
|/Zg|Generovat prototypy funkcí|  
|/ZS|Kontrola syntaxe|  
  
 Další informace o propojení najdete v tématu [možnosti Linkeru](../../build/reference/linker-options.md).  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že jsou kompilování tři C zdrojové soubory: MAIN.c, MOD1.c a MOD2.c. Každý soubor obsahuje volání funkci definovanou v jiném souboru:  
  
-   MAIN.c volá funkci `func1` v MOD1.c a funkce `func2` v MOD2.c.  
  
-   MOD1.c volání funkce standardní knihovny `printf_s` a `scanf_s`.  
  
-   MOD2.c volání funkce grafiky s názvem `myline` a `mycircle`, která jsou definována v knihovně s názvem MYGRAPH.lib.  
  
 K vytvoření tohoto programu, kompilovat s následující příkazový řádek:  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL nejprve zkompiluje zdrojové soubory C a vytvoří objekt soubory MAIN.obj, MOD1.obj a MOD2.obj. Kompilátor umístí do každého souboru .obj název standardní knihovny. Další podrobnosti najdete v tématu [použití běhové knihovny](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 CL předá názvy soubory .obj, společně s názvem MYGRAPH.lib, linkeru. Linkeru přeloží externí odkazy následujícím způsobem:  
  
1.  V MAIN.obj, odkaz na `func1` vyřešen v definici MOD1.obj; odkaz na `func2` vyřešen v definici MOD2.obj.  
  
2.  V MOD1.obj, odkazy na `printf_s` a `scanf_s` se přeloží pomocí definice do knihovny, která vyhledá linkeru s názvem v rámci MOD1.obj.  
  
3.  V MOD2.obj, odkazy na `myline` a `mycircle` se přeloží pomocí definice v MYGRAPH.lib.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)