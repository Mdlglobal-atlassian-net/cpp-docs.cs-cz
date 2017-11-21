---
title: "Závažná chyba C1026 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1026
dev_langs: C++
helpviewer_keywords: C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 187cfc1a59fc40a721be09aef9e78ef36c68f66a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1026"></a>Závažná chyba C1026
přetečení zásobníku analyzátoru, program příliš složitý  
  
 Místo požadované analyzovat program způsobila přetečení zásobníku kompilátoru.  
  
 Snížení složitosti výrazy podle:  
  
-   Snížení vnoření v `for` a `switch` příkazy. Uveďte hlubšímu vnořené příkazy v samostatné funkce.  
  
-   Rozdělení dlouho výrazů, které zahrnují operátory čárkou nebo volání funkce.