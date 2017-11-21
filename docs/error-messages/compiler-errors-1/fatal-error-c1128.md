---
title: "Závažná chyba C1128 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1128
dev_langs: C++
helpviewer_keywords: C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 83ec855a3280b1169ce3537ecf85944939449316
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1128"></a>Závažná chyba C1128
Počet oddílů překročil limit formátu souboru objektu: zkompilujte s možností /bigobj  
  
 Soubor s příponou .obj překročil počet povolených oddílů, omezení formátu objektu souboru COFF.  
  
 Toto omezení část dorazila může být výsledkem použití [/Gy](../../build/reference/gy-enable-function-level-linking.md) a sestavení ladicí verze; **/Gy** způsobí, že přejdete do vlastních oddílů sekvence COMDAT funkce. V laděném sestavení se nachází oddíl informací o ladění pro každou funkci COMDAT.  
  
 Upozornění C1128 může být vygenerováno také tehdy, pokud existuje příliš mnoho vložených funkcí.  
  
 Chcete-li opravit tuto chybu, rozdělení souboru zdroje do více soubory zdrojového kódu, kompilovat bez **/Gy**, nebo kompilovat s  [ /bigobj (zvýšit počet oddílů v. Soubor obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Pokud nejde kompilovat s **/Gy**, budete muset určit optimalizace individuálně, protože **/O2** a **/O1** i implikují **/Gy**.  
  
 Pokud je to možné, proveďte kompilaci bez informací o ladění.  
  
 Také může být nutné mít konkrétní instance šablon v samostatných souborech zdrojového kódu, spíše než je nechat vygenerovat kompilátorem.  
  
 Když portování kódu, C1128 pravděpodobně zobrazí nejprve při použití x64 kompilátoru a mnoho později pomocí x86 kompilátoru. x64 bude mít délku minimálně 4 částí spojené s každou funkci zkompilovat **/Gy** nebo vložená z šablony nebo vložené třídy: kód, pdata a informace a případně xdata ladění.  Kompilátor X86 nebude mít pdata.