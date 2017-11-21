---
title: "Kompilátoru (úroveň 1) upozornění C4049 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4049
dev_langs: C++
helpviewer_keywords: C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e749571bcf4c0e1547279a857e50556f766c576
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4049"></a>C4049 kompilátoru upozornění (úroveň 1)
omezení kompilátoru: ukončení emisí číslo řádku  
  
 Tento soubor obsahuje více než 16 777 215 (2<sup>24</sup>-1) zdroj řádky. Kompilátor zastaví číslování na 16 777 215.  
  
 Pro kód po řádku 16 777 215:  
  
-   Image bude obsahovat žádné informace o ladění pro čísla řádků.  
  
-   Některé Diagnostika se může hlásit nesprávný řádek čísly.  
  
-   .asm výpisech (nebo DM) je pravděpodobně nesprávný řádek čísla.