---
title: 'Postupy: ladění sestavení pro vydání | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e733375f01d4b2b8ec7090f7f70ad1ec5280cd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374476"
---
# <a name="how-to-debug-a-release-build"></a>Postupy: Ladění sestavení pro vydání
Můžete ladit sestavení pro vydání aplikace.  
  
### <a name="to-debug-a-release-build"></a>K ladění sestavení pro vydání  
  
1.  Otevřete **stránky vlastností** dialogové okno pro projekt. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** uzlu. Nastavit **Debug Information Format** k [kompatibilní s C7 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) nebo **databázi programu (/Zi)**.  
  
3.  Rozbalte položku **Linkeru** a klikněte na **Obecné** uzlu. Nastavit **Povolit přírůstkové propojování** k [ne (/ PŘÍRŮSTKOVÉ: Ne)](../../build/reference/incremental-link-incrementally.md).  
  
4.  Vyberte **ladění** uzlu. Nastavit **Generovat ladicí informace** k [Ano (/ DEBUG)](../../build/reference/debug-generate-debug-info.md).  
  
5.  Vyberte **optimalizace** uzlu. Nastavit **odkazy** k [/OPT:REF](../../build/reference/opt-optimizations.md) a **Povolit skládání sekvence COMDAT** k [/OPT:ICF](../../build/reference/opt-optimizations.md).  
  
6.  Nyní můžete ladit aplikace verzi sestavení. Najít problém, krok prostřednictvím code (nebo použijte pouze v době ladění), dokud zjistíte, kdy dojde k selhání, a pak určit nesprávné parametry nebo kódu.  
  
     Pokud aplikace funguje v sestavení ladicí verze, ale v sestavení pro vydání selže, může jedna optimalizace kompilátoru vystavení vadu ve zdrojovém kódu. A izolovat daný problém, zakážete vybrané optimalizace pro každého souboru se zdrojovým kódem, dokud vyhledat soubor a optimalizace, která je příčinou problému. (Urychlit proces, můžete rozdělit do dvou skupin souborů, zakázat optimalizace na jednu skupinu a když narazíte na potíže ve skupině, pokračovat dělení až izolovat soubor problém.)  
  
     Můžete použít [/RTC](../../build/reference/rtc-run-time-error-checks.md) pokusit vystavit takové chyby v sestavení pro ladění.  
  
     Další informace najdete v tématu [optimalizace si kód](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)