---
title: Upozornění linkerů Lnk4098 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aadf25d968d6d457f891cab49a43591455b9d12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4098"></a>Upozornění linkerů LNK4098
DEFAULTLIB 'knihovny, je v konfliktu s použití jiných knihovny; použít /NODEFAULTLIB:library  
  
 Pokoušíte se propojit s kompatibilní knihovny.  
  
> [!NOTE]
>  Běhové knihovny teď obsahují direktivy, aby se zabránilo mísí různé typy. Zobrazí se toto upozornění, pokud se pokusíte použít různé typy nebo ladění a bez ladění verzích běhové knihovny ve stejné aplikaci. Například pokud zkompilujete jeden soubor použít jednu druh běhové knihovny a druhý souboru použít jiný typ (například jednovláknové porovnání s více vlákny) a propojit je se pokusil, zobrazí se toto upozornění. Všechny zdrojové soubory pro použití stejné běhové knihovny musí zkompilují. Najdete v článku [použití běhové knihovny](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) – možnosti kompilátoru Další informace.  
  
 Můžete použít linkeru [/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md) přepínač tak, aby určit, které knihovny je hledání linkeru. Pokud se zobrazí LNK4098 a chcete vytvořit spustitelný soubor, který používá například jedním podprocesem, bez ladění běhové knihovny, použijte **/VERBOSE:LIB** možnost a zjistěte, které knihovny je hledání linkeru. Linkeru by měl tisk LIBC.lib a není LIBCMT.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib nebo MSVCRTD.lib jako knihovny vyhledávat. Se dá zjistit linkeru ignorovat nesprávné běhové knihovny pomocí [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pro každou knihovnu, kterou chcete ignorovat.  
  
 Následující tabulka uvádí, které knihovny třeba ji ignorovat, v závislosti na tom, které běhové knihovny, kterou chcete použít.  
  
|Použití této běhové knihovny|Ignorovat tyto knihovny|  
|-----------------------------------|----------------------------|  
|Jednovláknové (libc.lib)|Libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Více vláken (libcmt.lib)|Libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Vícevláknové použití knihovny DLL (msvcrt.lib)|Libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Ladění jednovláknové (libcd.lib)|Libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, msvcrtd.lib|  
|Ladění vícevláknových (libcmtd.lib)|Libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, msvcrtd.lib|  
|Ladění Multithreaded pomocí knihovny DLL (msvcrtd.lib)|Libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|  
  
 Například pokud se vám zobrazila tato upozornění a chcete vytvořit spustitelný soubor, který používá jiný debug, jednovláknové verzi běhové knihovny, můžete použít následující možnosti s linkeru:  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```