---
title: "Proměnné prostředí LINK | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67b36afce92140c4f205f8e5a4a46dfc7ac2d300
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="link-environment-variables"></a>Proměnné prostředí LINK

Nástroj LINK používá následující proměnné prostředí:  
  
-   ODKAZ a \_odkaz\_, pokud je definována. Nástroj LINK přidá možnosti a argumenty, které jsou definované v proměnné prostředí LINK a připojí možnosti a argumenty definované v \_odkaz\_ proměnnou prostředí pro argumenty příkazového řádku před zpracováním.  
  
-   LIB, pokud je definována. Nástroje pro propojení používá cesta LIB při hledání objektu, knihovny nebo jiné souboru zadat na příkazovém řádku nebo pomocí [/základní](../../build/reference/base-base-address.md) možnost. Také používá LIB cesta k nalezení PDB soubor s názvem v objektu. Proměnná LIB může obsahovat jednu nebo více specifikací cesty oddělené středníky. Jedna cesta musí odkazovat podadresáři \lib instalace Visual C++.  
  
-   CESTA, pokud tento nástroj je potřeba spustit CVTRES a nemůže najít soubor ve stejném adresáři jako odkaz sám sebe. (Odkaz vyžaduje CVTRES propojení .res souboru.) Cesta musí odkazovat na podadresáři \bin instalace Visual C++.  
  
-   TMP k určení adresáře při propojování OMF nebo .res soubory.  
  
## <a name="see-also"></a>Viz také  

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)   
[Sestavení kódu C/C++ na příkazovém řádku](../../build/building-on-the-command-line.md)  
[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
