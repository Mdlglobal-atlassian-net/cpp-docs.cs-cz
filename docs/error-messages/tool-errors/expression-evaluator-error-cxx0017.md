---
title: CXX0017 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7540dc701ffa6e0acb3d2661e1196e5f4552d2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0017"></a>Chyba při vyhodnocování výrazu CXX0017
nebyl nalezen – symbol  
  
 Symbol zadaný ve výrazu nebyl nalezen.  
  
 Možnou příčinou této chyby je případu Neshoda v názvu symbolu. Protože C a C++ se malá a velká písmena jazyků, musí být uvedeny názvu symbolu v případě přesné, ve kterém je definovaný ve zdroji.  
  
 Této chybě může dojít při pokusu o přiřazení typu proměnné, aby bylo možné sledovat proměnnou během ladění. `typedef` Deklaruje nový název typu, ale nedefinuje nového typu. Typecast pokus v ladicím programu vyžaduje název určitého typu.  
  
 Tato chyba je stejný jako CAN0017.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zkontrolujte, zda že je symbol je již deklarována okamžiku v programu, kde se používá.  
  
2.  Použít název skutečný typ přetypovat proměnné v ladicím programu, ne `typedef`-definovaný název.