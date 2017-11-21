---
title: "CXX0030 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0030
dev_langs: C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffa1dd85419943ede6a13d61cb82924c32b5e80a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0030"></a>Chyba při vyhodnocování výrazu CXX0030
výraz není evaluatable  
  
 Vyhodnocení výrazu ladicím programu nelze získat hodnotu výrazu, protože do něj zapisuje. Jeden pravděpodobnou příčinou je, že výraz odkazuje na paměti, která je mimo program adresního prostoru (vyhodnocení ukazatele null je jedním z příkladů). Windows neumožňuje přístup k paměti, která je mimo program adresní prostor.  
  
 Můžete chtít přepište výraz pomocí závorek řídit pořadí vyhodnocování.  
  
 Tato chyba je stejný jako CAN0030.