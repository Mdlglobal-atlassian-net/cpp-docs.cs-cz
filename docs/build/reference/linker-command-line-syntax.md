---
title: Syntaxe příkazového řádku linkeru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd5b1b809bfbbb01bca91f3677774d396515f56e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376163"
---
# <a name="linker-command-line-syntax"></a>Syntaxe příkazového řádku linkeru
Ke spuštění odkaz. EXE, použijte následující syntaxi příkazu:  
  
```  
LINK arguments  
```  
  
 `arguments` Zahrnují možnosti a názvy souborů a lze jej zadat v libovolném pořadí. Možnosti jsou zpracování první a potom soubory. Slouží k oddělení argumenty mezery nebo karty.  
  
> [!NOTE]
>  Můžete spustit tento nástroj pouze z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] příkazového řádku. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů.  
  
 Na příkazovém řádku, možnost se skládá z specifikátor možnosti pomlčkou (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti trvat argument, zadáno po dvojtečkou (:). Nesmí být mezery ani karty jsou povoleny v rámci specifikace možnost kromě v rámci v možnosti/Comment řetězec v uvozovkách. Zadejte číselnou argumenty v desítkový nebo zápis jazyka C. Názvy možností a jejich – klíčové slovo nebo název souboru argumenty nejsou velká a malá písmena, ale mají identifikátory URI jako argumenty velká a malá písmena.  
  
 Chcete linkeru předat soubor, zadejte název souboru na příkazovém řádku po příkazu propojení. Můžete zadat absolutní nebo relativní cesta název souboru, a můžete použít zástupné znaky v názvu souboru. Pokud vynecháte tečku (.) a název souboru příponu, předpokládá odkaz .obj za účelem vyhledání souboru. ODKAZ nepoužívá přípony názvů souborů nebo chybějícím je aby předpoklady o obsahu souborů. Určuje typ souboru tak, že prověří ho a procesy odpovídajícím způsobem.  
  
 Link.exe vrátí hodnotu 0 pro úspěch (žádné chyby).  Linkeru, jinak vrátí počet chyba zastavení odkaz.  Například pokud linkeru generuje LNK1104, linkeru vrátí 1104.  Podle toho s nejnižším číslem chyby vrácené linkeru na chybu je 1 000.  Vrácená hodnota 128 představuje problém konfigurace operačního systému nebo soubor .config; zavaděč nebyla načíst link.exe nebo c2.dll.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)