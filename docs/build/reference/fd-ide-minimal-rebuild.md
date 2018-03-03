---
title: "-FD (minimální opětovné sestavení IDE) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0dfcf34be03204b920e5a4459c6a2d7ea6c506d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (minimální opětovné sestavení IDE)
**/FD** není dostupná uživatelům s výjimkou v [příkazového řádku](../../ide/command-line-property-pages.md) stránce vlastností projektu C++ **stránky vlastností** dialogové okno pole, pokud a pouze v případě [/Gm (povolit minimální sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) zároveň nevyberete. **/FD** nemá žádný vliv jiné než z vývojového prostředí. **/FD** nebude vystavena, ve výstupu **cl /?**.  
  
 Pokud nepovolíte **/Gm** ve vývojovém prostředí **/FD** se použije. **/FD** zajistí, že soubor IDB má dostatek informací o závislostech. **/FD** se používá pouze ve vývojovém prostředí a neměl by být použit z příkazového řádku nebo skriptu buildu.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)