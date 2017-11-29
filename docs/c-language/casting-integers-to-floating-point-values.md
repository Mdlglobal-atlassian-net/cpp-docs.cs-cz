---
title: "Přetypování celých čísel na hodnoty s plovoucí desetinnou čárkou | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0c91c9533baec350ba66ae1ab4db472c0ea8bcdf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="casting-integers-to-floating-point-values"></a>Přetypování celých čísel na hodnoty s plovoucí desetinnou čárkou
**ANSI 3.2.1.3** směr zkrácení při celé číslo je převedeno na číslo s plovoucí desetinnou čárkou, které nelze vyjádřit přesně původní hodnotu  
  
 Když je celé číslo přetypováno na hodnotu čísla s plovoucí desetinnou čárkou, které nemůže přesně představovat hodnotu, je tato hodnota zaokrouhlena (nahoru nebo dolů) na nejbližší vhodnou hodnotu.  
  
 Například přetypování **nepodepsané dlouho** (s 32 bity přesnosti) k **float** (jehož mantisa má 23 bity přesnost) Zaokrouhlí číslo na nejbližší násobek 256. **Dlouho** 4,294,966,913 k 4,294,967,167 hodnoty jsou zaokrouhleny na **float** hodnotu 4,294,967,040.  
  
## <a name="see-also"></a>Viz také  
 [Matematické s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)