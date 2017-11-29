---
title: "CXX0065 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0065
dev_langs: C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a80869ad54541a493450ce4cc3696da5da6116b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0065"></a>Chyba při vyhodnocování výrazu CXX0065
Proměnná musí rámce zásobníku  
  
 Výraz obsahuje proměnné, která existuje v aktuálním oboru, ale ještě nebyl vytvořen.  
  
 Této chybě může dojít, když máte stupeň do prologu funkce ale ještě nebyla nastavení rámce zásobníku pro funkci, nebo pokud máte stupeň do ukončovací kód pro funkci.  
  
 Procházet kód prologu, dokud rámce zásobníku byl nastavený před vyhodnocení výrazu.  
  
 Tato chyba je stejný jako CAN0065.