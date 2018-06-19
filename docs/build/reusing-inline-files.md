---
title: Opětovné použití vložených souborů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 017364061093ef7a3c3e006f58c331c48a8009e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379897"
---
# <a name="reusing-inline-files"></a>Opětovné použití vložených souborů
Chcete-li znovu použít vloženého souboru, zadejte <<*filename* tam, kde je soubor je definovaný a nejprve použít, pak znovu použít *filename* bez << novější ve stejné nebo jiné příkaz. Příkaz k vytvoření souboru vložené musí spustit před všechny příkazy, které používají soubor.  
  
## <a name="see-also"></a>Viz také  
 [Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)