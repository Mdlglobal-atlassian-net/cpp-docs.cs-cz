---
title: "Chyba sestavení projektu PRJ0013 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0013
dev_langs: C++
helpviewer_keywords: PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a5c382cc0c47340c591acf3f44642118ebdf02f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0013"></a>Chyba sestavení projektu PRJ0013
Systémový prostředek může být kriticky nízké. Nelze vytvořit kanál nutná ke spuštění sestavení.  
  
 Tato chyba označuje, zda je dostatek systémových prostředků. Pokud chcete tuto chybu vyřešit, snížit využití systémových prostředků jiné procesy aplikace.  
  
 Tato chyba může vyskytnout, pokud úroveň zabezpečení je nedostatečná pro vytvoření kanály (viz [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).