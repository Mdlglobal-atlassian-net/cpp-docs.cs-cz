---
title: "Chyba linkerů Lnk1211 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1211
dev_langs: C++
helpviewer_keywords: LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c0fd4ac4ae616d256d3d5971fe417dcf7846b4ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1211"></a>Chyba linkerů LNK1211
informace o předkompilovaných typu nebyl nalezen. 'název souboru' není propojená nebo přepsání  
  
 Soubor daného objektu, kompilovat s [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nebyl specifikován v příkazu odkaz nebo byl přepsán.  
  
 Pokud vytváříte ladicí knihovny, který používá předkompilovaných hlaviček, a pokud zadáte /Yc a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ vygeneruje soubor předkompilovaných objekt, který obsahuje CodeView ladicí informace. Této chybě dojde, pouze když ukládáte soubor předkompilovaných objektu v knihovně, použijte k tvorbě spustitelné bitové kopie knihovny, a soubory objektů, které jsou odkazované neobsahují přenositelné odkazy na některé funkce, které definuje soubor předkompilovaných objektu.  
  
 Chcete-li vyřešit tuto situaci dvěma způsoby:  
  
-   Zadejte [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) – možnost kompilátoru k přidání informací CodeView z předkompilované hlavičky do každého objektu modulu. Tato metoda je méně vhodné, protože obecně vytváří velkého objektu moduly, které může prodloužit doba nutná k propojení aplikace.  
  
-   Zadejte [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) a předat název libovolný řetězec, když vytvoříte předkompilovaný hlavičkový soubor, který neobsahuje žádné definice funkcí. To bude směrovat kompilátoru pro vytvoření symbolu v souboru předkompilovaných objektu a pro vydávání odkaz na tento symbol do každého souboru objektu, který použít předkompilovaný hlavičkový soubor, který je přidružený soubor předkompilovaných objektu.  
  
 Když zkompilujete modul s **/Yc** a **/Yl**, kompilátor vytvoří symbol podobná `__@@_PchSym_@00@...@symbol_name`, kde se třemi tečkami (...) představuje řetězec znaků generované kompilátorem a uloží jej do modul objektu. Zdrojový soubor, který kompilujete s Tento předkompilovaných hlaviček odkazuje zadaný symbol, což způsobí, že linkeru zahrnuje modul objektu a jeho ladicí informace z knihovny.  
  
 Další informace o této chybě najdete v článku znalostní báze Q102697 PRB: sestavení chyby použití předkompilovaných hlaviček v ladění Lib.