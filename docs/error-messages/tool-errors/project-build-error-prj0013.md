---
title: Chyba sestavení projektu PRJ0013 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0013
dev_langs:
- C++
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d055043d5c7e7b030557ab03ceb7181c664ce01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318773"
---
# <a name="project-build-error-prj0013"></a>Chyba sestavení projektu PRJ0013
Systémový prostředek může být kriticky nízké. Nelze vytvořit kanál nutná ke spuštění sestavení.  
  
 Tato chyba označuje, zda je dostatek systémových prostředků. Pokud chcete tuto chybu vyřešit, snížit využití systémových prostředků jiné procesy aplikace.  
  
 Tato chyba může vyskytnout, pokud úroveň zabezpečení je nedostatečná pro vytvoření kanály (viz [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).