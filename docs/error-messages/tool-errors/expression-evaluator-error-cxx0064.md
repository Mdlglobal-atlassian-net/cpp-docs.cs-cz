---
title: "CXX0064 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0064
dev_langs: C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ada57d8df67054fa6577b128a6be73921fbb7e81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0064"></a>Chyba při vyhodnocování výrazu CXX0064
Nelze nastavit bod přerušení na člena vázané virtuální funkce  
  
 Zarážku byl nastaven na člena virtuální funkce prostřednictvím ukazatele na objekt, jako například:  
  
```  
pClass->vfunc( int );  
```  
  
 Zarážky můžete nastavit na virtuální funkci zadáním třídy, jako například:  
  
```  
Class::vfunc( int );  
```  
  
 Tato chyba je stejný jako CAN0064.