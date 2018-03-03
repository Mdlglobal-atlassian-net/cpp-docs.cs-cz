---
title: "CXX0065 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db01baa10191df50c1f319bf8320263657088d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0065"></a>Chyba při vyhodnocování výrazu CXX0065
Proměnná musí rámce zásobníku  
  
 Výraz obsahuje proměnné, která existuje v aktuálním oboru, ale ještě nebyl vytvořen.  
  
 Této chybě může dojít, když máte stupeň do prologu funkce ale ještě nebyla nastavení rámce zásobníku pro funkci, nebo pokud máte stupeň do ukončovací kód pro funkci.  
  
 Procházet kód prologu, dokud rámce zásobníku byl nastavený před vyhodnocení výrazu.  
  
 Tato chyba je stejný jako CAN0065.