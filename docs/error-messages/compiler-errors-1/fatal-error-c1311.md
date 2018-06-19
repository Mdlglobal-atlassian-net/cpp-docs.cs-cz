---
title: Závažná chyba C1311 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b3759a5fec4b072f9a9b300670d61cb0d101c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226671"
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