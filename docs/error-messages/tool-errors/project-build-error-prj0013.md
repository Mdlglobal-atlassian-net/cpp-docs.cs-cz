---
title: Chyba sestavení projektu PRJ0013 | Dokumentace Microsoftu
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
ms.openlocfilehash: aeb0ac9011697c440667a538bd1805780810fb4a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221556"
---
# <a name="project-build-error-prj0013"></a>Chyba sestavení projektu PRJ0013
Systémový prostředek může být kriticky nízký. Nelze vytvořit kanál požadovaný ke spuštění sestavení.  
  
 Tato chyba označuje, že není dostatek systémových prostředků. Chcete-li vyřešit tuto chybu, snížit využití systémových prostředků jiné procesy aplikace.  
  
 K této chybě může dojít také úroveň zabezpečení není dostatečná k vytváření kanálů (viz [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).