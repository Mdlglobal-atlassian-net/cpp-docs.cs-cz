---
title: Závažná chyba C1128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d2604b17b656efab3a3575469eff6a02df960c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226262"
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