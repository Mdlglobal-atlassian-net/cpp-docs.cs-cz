---
title: CXX0065 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78c25c9c6bde27219f10e4047dc7a6ab416f55d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297534"
---
# <a name="expression-evaluator-error-cxx0065"></a>Chyba při vyhodnocování výrazu CXX0065
Proměnná musí rámce zásobníku  
  
 Výraz obsahuje proměnné, která existuje v aktuálním oboru, ale ještě nebyl vytvořen.  
  
 Této chybě může dojít, když máte stupeň do prologu funkce ale ještě nebyla nastavení rámce zásobníku pro funkci, nebo pokud máte stupeň do ukončovací kód pro funkci.  
  
 Procházet kód prologu, dokud rámce zásobníku byl nastavený před vyhodnocení výrazu.  
  
 Tato chyba je stejný jako CAN0065.