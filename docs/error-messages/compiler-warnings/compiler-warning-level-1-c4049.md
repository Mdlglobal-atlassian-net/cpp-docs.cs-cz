---
title: Kompilátoru (úroveň 1) upozornění C4049 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eea293ff64ed8fe2bf4bf0d38d897eb82223802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4049"></a>C4049 kompilátoru upozornění (úroveň 1)
omezení kompilátoru: ukončení emisí číslo řádku  
  
 Tento soubor obsahuje více než 16 777 215 (2<sup>24</sup>-1) zdroj řádky. Kompilátor zastaví číslování na 16 777 215.  
  
 Pro kód po řádku 16 777 215:  
  
-   Image bude obsahovat žádné informace o ladění pro čísla řádků.  
  
-   Některé Diagnostika se může hlásit nesprávný řádek čísly.  
  
-   .asm výpisech (nebo DM) je pravděpodobně nesprávný řádek čísla.