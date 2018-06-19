---
title: Volba formátu .netmodule vstupní soubory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62575d3e816bdc10587e7a4c9cebcea735329ec1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372718"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Výběr formátu vstupních souborů .netmodule
Soubor .obj MSIL (Kompilovat s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md)) lze také použít jako soubor .netmodule.  soubory .obj obsahovat metadata a nativní symboly.  .netmodules obsahují pouze metadata.  
  
 Můžete předat souboru .obj MSIL do jiné sady Visual Studio kompilátoru prostřednictvím / addmodule – možnost kompilátoru (ale mějte na paměti, že stane součástí výsledné sestavení a musí být součástí sestavení v souboru .obj).  Visual C# a Visual Basic třeba mít / addmodule – možnost kompilátoru.  
  
> [!NOTE]
>  Ve většině případů musíte předat linkeru souboru .obj z kompilace vytvořený modul .net.  Předání souboru .dll nebo .netmodule modulu MSIL do linkeru může mít za následek LNK1107.  
  
 soubory .obj, spolu s jejich přidružené .h soubory, které odkazují prostřednictvím # zdroje include, povolí aplikací C++ využívat nativní typy v modulu, zatímco v souboru .netmodule, mohou být spotřebovávána pouze spravované typy aplikace C++.  Pokud se pokusíte předat souboru .obj na #using, informace o nativní typy nebude k dispozici. #include souborů .h souboru .obj místo.  
  
 Kompilátory jiné sady Visual Studio může využít pouze spravované typy z modulu.  
  
 Použijte následující postupy k určení, jestli je potřeba použít .netmodule nebo souboru .obj jako vstup modulu linkeru jazyka Visual C++:  
  
-   Pokud vytváříte s kompilátoru Visual Studio než Visual C++, vytvářet .netmodule a používat .netmodule jako vstup linkeru.  
  
-   Pokud používáte Visual C++ compiler k vytvoření moduly a pokud ve modulu nebo modulech se použije k vytvoření něco jiného než knihovny, použijte soubory .obj vyprodukované kompilátor jako vstup modulu linkeru; Nepoužívejte soubor .netmodule jako vstup.  
  
-   Pokud moduly se použije pro sestavení (není spravované) nativní knihovny, použijte soubory .obj jako vstup linkeru modulu a generovat soubor knihovny LIB.  
  
-   Pokud moduly se použije k vytvoření spravované knihovny, a pokud všechny modulu vstup linkeru bude ověřitelný (vytvořeného pomocí/clr: safe), použijte soubory .obj jako vstup linkeru modulu a vygenerujte .dll (sestavení) nebo soubor knihovny .netmodule (modulu).  
  
-   Pokud moduly se použije k vytvoření spravované knihovny, a pokud jeden nebo více modulů vstup linkeru se vytváří pomocí jenom možnosti/CLR, použijte soubory .obj jako vstup linkeru modulu a generovat .dll (sestavení).  Pokud chcete vystavit spravované typy v knihovně, a pokud chcete aplikace C++ využívat nativní typy v knihovně, své knihovny bude obsahovat soubory .obj pro moduly součástí knihovny (také můžete pro odeslání souborů .h pro každý modul takže může být odkazováno s #include ze zdrojového kódu).  
  
## <a name="see-also"></a>Viz také  
 [Soubory .netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md)