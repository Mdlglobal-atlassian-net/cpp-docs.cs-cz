---
title: Nevhodný přístup ke sjednocení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c322ff9e411cc6c9ef845fdd9a289a9ed5c49d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383589"
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení
**ANSI 3.3.2.3** členem objekt union přistupuje pomocí členem jiného typu  
  
 Pokud je deklarovaná spojení dvou typů a jedna hodnota je uložena, ale sjednocení přistupuje s jiným typem, nespolehlivé výsledky.  
  
 Například spojení **float** a `int` je deklarován. A **float** hodnota je uložena, ale tento program později přistupuje k hodnotě jako `int`. V takové situaci by hodnota závisí na interní úložiště **float** hodnoty. Celočíselná hodnota, nebudou spolehlivé.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)