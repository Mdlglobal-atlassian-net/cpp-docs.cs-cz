---
title: "Postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f776cbaec0b890959db180a373d4cb4152ac5826
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-enable-a-64-bit-x64-hosted-visual-c-toolset-on-the-command-line"></a>Postupy: povolení 64-Bit, x64 hostovat sady nástrojů Visual C++ v příkazovém řádku

Visual C++ zahrnuje kompilátory, linkers a dalších nástrojů, které můžete použít k vytvoření specifických pro platformy verze aplikace, které můžou běžet v 32bitové, 64bitové nebo založené na ARM operačních systémech Windows. Další volitelné úlohy sady Visual Studio umožňují používat nástroje C++ pro jiné platformy, jako je iOS, Android a Linux. Architektura sestavení výchozí používá 32-bit, hostované x86 nástroje pro sestavení 32-bit, x86 nativní kód systému Windows. Ale pravděpodobně máte 64bitovém počítači. Můžete využít výhod na procesor a paměť místa pro 64bitový kód pomocí nástrojů 64-bit, hostované x64 při sestavování kód pro x86, x64 nebo procesory ARM.
  
> [!NOTE]
>  Informace o konkrétní nástroje, které jsou součástí každé edici Visual C++ najdete v tématu [funkcí v edicích Visual Studio a nástrojů pro Visual C++](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).  
>   
>  Informace o tom, jak pomocí prostředí Visual Studio IDE můžete vytvořit 64bitových aplikací najdete v tématu [postupy: Konfigurace projekty Visual C++ pro cíl 64-Bit, x64 platformy](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).  
  
Když instalujete zatížení C++ v instalačním programu sady Visual Studio, vždy nainstaluje 32bitová verze, hostované x86, nativní a multiplatformní kompilátoru nástroje potřebné k vytváření x86 a x64 kódu. Pokud zahrnete zatížení univerzální platformu Windows, nainstaluje taky hostované x86 křížové kompilátoru nástroje potřebné k vytváření kódu ARM. Pokud nainstalujete tyto úlohy na 64-bit, x64 procesoru, můžete také získat nativní 64bitová verze a křížové kompilátoru nástroje k vytváření x86 x 64 a ARM kódu. 32bitová verze a 64bitová verze nástrojů Generovat identické kód, ale nástroje 64-bit podporují více paměti pro předkompilované hlavičky symboly a optimalizace celého programu ([/GL](../build/reference/gl-whole-program-optimization.md) a [/ltgc](../build/reference/ltcg-link-time-code-generation.md)) možnosti. Pokud spustíte do limitu paměti při použití nástroje 32-bit, zkuste 64bitové nástroje.  

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Pomocí zástupce příkazového řádku vývojáře hostované 64-bit
  
Při instalaci sady Visual Studio v operačním systému Windows 64-bit zástupce příkazového řádku vývojáře další pro nativní 64bitové, x64 hostované a křížové kompilátory jsou k dispozici. K přístupu ke tyto příkazového řádku na Windows 10 na **spustit** nabídky, otevřete složku pro vaši verzi sady Visual Studio, například **Visual Studio 2017**a pak vyberte jednu z x64 nativní nebo mezi – nástroj vývojáře příkazového řádku. K přístupu ke tyto příkazového řádku v systému Windows 8, na **spustit** obrazovce otevřete **všechny aplikace**. V části pro nainstalovanou verzi sady Visual Studio, otevřete **Visual Studio** složky (v starší verze sady Visual Studio, může být název **nástroje sady Visual Studio**). V dřívějších verzích systému Windows, zvolte **spustit**, rozbalte položku **všechny programy**, složce pro vaši verzi **Visual Studio** (a na starší verze sady Visual Studio,  **Nástroje sady Visual Studio**). Další informace najdete v tématu [zástupce příkazového řádku vývojáře](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).  
  
## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Pomocí Vcvarsall.bat nastavte architektura 64-bit hostované sestavení
  
Některé z nativního nebo křížové nástrojů kompilátoru konfigurace sestavení lze použít na příkazovém řádku spuštěním vcvarsall.bat příkaz, který soubor. Tento příkaz Soubor nakonfiguruje cesty a proměnných prostředí, které umožňují konkrétní sestavení architektura v existujícím okně příkazového řádku. Konkrétní pokyny najdete v tématu [vývojáře příkaz soubory a umístění](../build/building-on-the-command-line.md#developer_command_files) .  
  
## <a name="see-also"></a>Viz také  

[Konfigurace Visual C++ pro 64bitové, x64 cíle](../build/configuring-programs-for-64-bit-visual-cpp.md)