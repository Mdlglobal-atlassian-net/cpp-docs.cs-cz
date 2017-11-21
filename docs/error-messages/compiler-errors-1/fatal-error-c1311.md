---
title: "Závažná chyba C1311 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1311
dev_langs: C++
helpviewer_keywords: C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aeb63e041ddfe26a8fc47afc838f2f5c3ce35d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1311"></a>Závažná chyba C1311
Formát COFF nelze inicializovat staticky 'var' s číslo (adresu bajtů)  
  
 Adresu, jehož hodnota není znám. v době kompilace nelze staticky přiřadit do proměnné, jehož typ má úložiště menší než čtyři bajtů.  
  
 Této chybě může dojít na kód, který je jinak platný C++.  
  
 Následující příklad ukazuje jednu podmínku, která může způsobit C1311.  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```