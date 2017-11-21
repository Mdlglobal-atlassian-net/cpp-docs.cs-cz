---
title: "Upozornění linkerů Lnk4075 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4075
dev_langs: C++
helpviewer_keywords: LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 78ff64b316a9b87a95fa68a95b5e4ca57923649d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4075"></a>Upozornění linkerů LNK4075
ignoruje možnost "1" z důvodu specifikace "option2"  
  
 Druhá možnost přepsání první.  
  
 Možnosti linkeru vzájemně se vylučuje zadávají.  Zkontrolujte možnosti linkeru.  Tam, kde jsou možnosti linkeru zadán závisí na tom, jak jsou sestavení projektu.  
  
-   Pokud vytváříte ve vývojovém prostředí, zkontrolujte oblast stránky vlastností linkeru pro svůj projekt a v tématu, kde jsou specifikované obě možnosti linkeru.  V tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md) Další informace.  
  
-   Pokud vytvoříte na příkazovém řádku, podívejte se na možnosti linkeru zadaný existuje.  
  
-   Pokud vytvoříte pomocí skriptů sestavení, projděte skripty zobrazíte, kde jsou tyto možnosti linkeru specifikované.  
  
 Pokud zjistíte, kde jsou zadány možnosti linkeru vzájemně se vylučuje, odeberte jednu z možností linkeru.  
  
 Některé konkrétní příklady:  
  
-   Pokud jste modul, který byl kompilován s **/ZI**, což naznačuje možnost interní linker volat /EDITANDCONTINUE a modul, který byl kompilován s /OPT:REF, /OPT:ICF nebo /INCREMENTAL:NO, která vyžadují žádné /EDITANDCONTINUE, bude získáte LNK4075.  V tématu [/Z7, / zi, /ZI (formát informace ladění)](../../build/reference/z7-zi-zi-debug-information-format.md) Další informace.