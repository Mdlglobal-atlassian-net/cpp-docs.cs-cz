---
title: CXX0030 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669c585c637129c1fb6a480d91b31e5a1264fd22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0030"></a>Chyba při vyhodnocování výrazu CXX0030
výraz není evaluatable  
  
 Vyhodnocení výrazu ladicím programu nelze získat hodnotu výrazu, protože do něj zapisuje. Jeden pravděpodobnou příčinou je, že výraz odkazuje na paměti, která je mimo program adresního prostoru (vyhodnocení ukazatele null je jedním z příkladů). Windows neumožňuje přístup k paměti, která je mimo program adresní prostor.  
  
 Můžete chtít přepište výraz pomocí závorek řídit pořadí vyhodnocování.  
  
 Tato chyba je stejný jako CAN0030.