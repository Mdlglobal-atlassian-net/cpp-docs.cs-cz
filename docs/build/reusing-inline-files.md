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
ms.workload: cplusplus
ms.openlocfilehash: f839babe036aff81174b954e1aef7abce8923386
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="reusing-inline-files"></a>Opětovné použití vložených souborů
Chcete-li znovu použít vloženého souboru, zadejte <<*filename* tam, kde je soubor je definovaný a nejprve použít, pak znovu použít *filename* bez << novější ve stejné nebo jiné příkaz. Příkaz k vytvoření souboru vložené musí spustit před všechny příkazy, které používají soubor.  
  
## <a name="see-also"></a>Viz také  
 [Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)