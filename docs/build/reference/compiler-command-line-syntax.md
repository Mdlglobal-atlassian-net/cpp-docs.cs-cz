---
title: "Syntaxe příkazového řádku kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f2047324280a3909c60542e3994639747bb6ecd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-command-line-syntax"></a>Syntaxe příkazového řádku kompilátoru
CL příkazového řádku používá následující syntaxe:  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 Následující tabulka popisuje vstup pro příkaz CL.  
  
|Položka|Význam|  
|-----------|-------------|  
|*možnost*|Jeden nebo více [možností CL](../../build/reference/compiler-options.md). Všimněte si, že všechny možnosti použít pro všechny zadané zdrojové soubory. Možnosti jsou určené lomítkem (/) nebo pomlčkou (-). Pokud možnost trvá argument, možnost Popis dokumenty, jestli chcete povolit mezeru mezi parametrem a argumenty. Názvy možností (s výjimkou možnost/Help) se rozlišují malá a velká písmena. V tématu [pořadí možností CL](../../build/reference/order-of-cl-options.md) Další informace.|  
|`file`|Název jeden nebo více zdrojových souborů, soubory .obj nebo knihovny. CL zkompiluje zdrojové soubory a předá názvy soubory .obj a knihovny linkeru. V tématu [syntaxe názvu souboru CL](../../build/reference/cl-filename-syntax.md) Další informace.|  
|*lib*|Jeden nebo více názvy knihoven. CL předává tyto názvy linkeru.|  
|*soubor příkazů*|Soubor, který obsahuje více možností a názvy souborů. V tématu [soubory příkazů CL](../../build/reference/cl-command-files.md) Další informace.|  
|*vyjádřit výslovný odkaz*|Jeden nebo více [možnosti linkeru](../../build/reference/linker-options.md). CL předává tyto možnosti linkeru.|  
  
 Můžete zadat libovolný počet možností, názvy souborů a názvy knihoven, tak dlouho, dokud počet znaků v příkazovém řádku není delší než 1024, omezení, závisí na operační systém.  
  
 Informace o návratová hodnota cl.exe najdete v tématu [vrátit hodnota cl.exe](../../build/reference/return-value-of-cl-exe.md) .  
  
> [!NOTE]
>  Příkazového řádku vstupní limit 1024 znaků není zaručeno, zůstane v budoucích verzích systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)