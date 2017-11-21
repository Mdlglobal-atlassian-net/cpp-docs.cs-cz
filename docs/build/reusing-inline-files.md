---
title: "Opětovné použití vložených souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cbad7ad7a4aee928158155a7a38c8d14a2b33a63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="reusing-inline-files"></a>Opětovné použití vložených souborů
Chcete-li znovu použít vloženého souboru, zadejte <<*filename* tam, kde je soubor je definovaný a nejprve použít, pak znovu použít *filename* bez << novější ve stejné nebo jiné příkaz. Příkaz k vytvoření souboru vložené musí spustit před všechny příkazy, které používají soubor.  
  
## <a name="see-also"></a>Viz také  
 [Vložené soubory v souboru pravidel](../build/inline-files-in-a-makefile.md)