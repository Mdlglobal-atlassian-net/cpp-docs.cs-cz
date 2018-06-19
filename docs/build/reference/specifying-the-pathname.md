---
title: Určení názvu cesty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2dd121909fbe0aa2f9305b7bd5779b995a69719
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375659"
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