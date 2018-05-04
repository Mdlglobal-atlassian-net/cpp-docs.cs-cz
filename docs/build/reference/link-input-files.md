---
title: Vstupní soubory LINK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d61a24916c3b56cf666a85483414f86753f7f59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="link-input-files"></a>Vstupní soubory LINK
U souborů, které obsahují objekty, jejich import a standardní knihovny, prostředky, definice modulu a zadejte příkaz poskytnete linkeru. ODKAZ nepoužívá přípony souborů aby předpoklady o obsahu souboru. Místo toho odkaz prověří každý vstupní soubor zjistit, jaký typ souboru je.  
  
 Soubory objektů na příkazovém řádku se zpracovávají v pořadí, ve kterém se objeví na příkazovém řádku. Knihovny jsou prohledávány v pořadí příkazového řádku taky s výstrahou, následující: nepřeložené symboly, které jsou při uvedení do souboru objektu z knihovny, které budou staženy v této knihovně první a potom následující knihovny z příkazového řádku a [/DEFAULTLIB (zadat výchozí knihovnu)](../../build/reference/defaultlib-specify-default-library.md) direktivy a potom na žádné knihovny na začátek příkazového řádku.  
  
> [!NOTE]
>  ODKAZ už přijme středník (nebo jakýkoli jiný znak) jako začátek komentář do odpovědi soubory a soubory pořadí. Středníky rozpoznávají jen jako začátek komentáře ve soubory definice modulu (.def).  
  
 ODKAZ používá následující typy vstupní soubory:  
  
-   [soubory .obj](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [.netmodule soubory](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [soubory .lib](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [soubory .exp](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [soubory .def](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [soubory PDB](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [soubory .res](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [soubory .exe](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [soubory s příponou .txt](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [soubory .ilk](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)