---
title: Závažná chyba C1026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c034d45b7f8b222471094f4580902ae1b8dc66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198102"
---
# <a name="fatal-error-c1026"></a>Závažná chyba C1026
přetečení zásobníku analyzátoru, program příliš složitý  
  
 Místo požadované analyzovat program způsobila přetečení zásobníku kompilátoru.  
  
 Snížení složitosti výrazy podle:  
  
-   Snížení vnoření v `for` a `switch` příkazy. Uveďte hlubšímu vnořené příkazy v samostatné funkce.  
  
-   Rozdělení dlouho výrazů, které zahrnují operátory čárkou nebo volání funkce.