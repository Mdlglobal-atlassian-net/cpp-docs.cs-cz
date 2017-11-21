---
title: "Nevhodný přístup ke sjednocení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54eeffebcc20846666c6ebb6a2951f8d55a5b8c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení
**ANSI 3.3.2.3** členem objekt union přistupuje pomocí členem jiného typu  
  
 Pokud je deklarovaná spojení dvou typů a jedna hodnota je uložena, ale sjednocení přistupuje s jiným typem, nespolehlivé výsledky.  
  
 Například spojení **float** a `int` je deklarován. A **float** hodnota je uložena, ale tento program později přistupuje k hodnotě jako `int`. V takové situaci by hodnota závisí na interní úložiště **float** hodnoty. Celočíselná hodnota, nebudou spolehlivé.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)