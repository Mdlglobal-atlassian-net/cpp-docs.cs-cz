---
title: "STDIN – stdout, stderr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7683a0ed1e40a0b65ea3a400c460dcd23ecef2d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr
## <a name="syntax"></a>Syntaxe  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Jsou to standardní datových proudů pro vstupní, výstupní a výstupní chybě.  
  
 Ve výchozím nastavení je přečíst standardní vstup z klávesnice, při tisku standardní výstupní zařízení a standardní chyba na obrazovku.  
  
 Následující ukazatele datového proudu jsou k dispozici pro přístup k standardní datové proudy:  
  
|Ukazatele|Stream|  
|-------------|------------|  
|`stdin`|Standardní vstup|  
|**STDOUT**|Standardní výstup|  
|`stderr`|Standardní chyba|  
  
 Tyto ukazatele slouží jako argumenty pro funkce. Některé funkce, jako například **getchar** a `putchar`, použijte `stdin` a **stdout** automaticky.  
  
 Tyto ukazatele jsou konstanty a nelze jí přiřadit nové hodnoty. `freopen` Funkce lze přesměrovat datové proudy soubory disku nebo do jiných zařízení. Operační systém umožňuje přesměrovat standardní vstupní a výstupní na úrovni příkaz programu.  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)