---
title: "Určení názvu cesty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f03d3f2bb10fa6b12cb046fd77f45a2bc6153064
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-the-pathname"></a>Určení názvu cesty
Jednotlivé možnosti výstupního souboru přijme *pathname* argument, který můžete zadat umístění a název souboru výstupního souboru. Argument může zahrnovat název jednotky, adresář a název souboru. Žádné místo je povolena možnost až argument.  
  
 Pokud *pathname* obsahuje název souboru bez přípony, kompilátor poskytuje výstup výchozí rozšíření. Pokud *pathname* zahrnuje adresáře, ale žádný název souboru kompilátoru vytvoří soubor s výchozím názvem v určeném adresáři. Výchozí název je založen na základní název zdrojového souboru a příponu výchozí na základě typu výstupního souboru. Pokud necháte *pathname* zcela, kompilátor vytvoří soubor s výchozím názvem ve výchozím adresáři.  
  
 Případně *pathname* argument může být název zařízení (AUX, CON, PRN nebo NUL), nikoli název souboru. Nepoužívejte mezeru mezi parametrem a název zařízení nebo dvojtečkou jako součást název zařízení.  
  
|Název zařízení|Představuje|  
|-----------------|----------------|  
|AUX|Pomocná zařízení|  
|CON|Konzola|  
|PRN|Tiskárny|  
|NUL|Null zařízení (žádný soubor)|  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek souboru mapování odešle do tiskárny:  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)