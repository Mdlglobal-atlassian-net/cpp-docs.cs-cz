---
title: "Nevhodný přístup ke sjednocení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71fe791e776450d21878144447cf95cdedb34875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení
**ANSI 3.3.2.3** členem objekt union přistupuje pomocí členem jiného typu  
  
 Pokud je deklarovaná spojení dvou typů a jedna hodnota je uložena, ale sjednocení přistupuje s jiným typem, nespolehlivé výsledky.  
  
 Například spojení **float** a `int` je deklarován. A **float** hodnota je uložena, ale tento program později přistupuje k hodnotě jako `int`. V takové situaci by hodnota závisí na interní úložiště **float** hodnoty. Celočíselná hodnota, nebudou spolehlivé.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)