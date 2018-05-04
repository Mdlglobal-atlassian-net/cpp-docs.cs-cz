---
title: Holé (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a60cdec00f3109bfcc332feeaca24ba5d6880f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="naked-c"></a>Naked (C)
**Konkrétní Microsoft**  
  
 Atribut třídy úložiště naked je rozšíření jazyka C specifické pro společnost Microsoft. Pro funkce deklarované s atributem třídy úložiště naked generuje kompilátor kód bez kódu prologu a epilogu. Neviditelné funkce jsou užitečné, potřebujete-li napsat vlastní sekvence kódu prologu a epilogu pomocí vloženého kódu assembleru. Neviditelné funkce jsou užitečné k psaní ovladačů virtuálních zařízení.  
  
 Konkrétní informace o používání holé atribut najdete v tématu [holé funkce](../c-language/naked-functions.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)