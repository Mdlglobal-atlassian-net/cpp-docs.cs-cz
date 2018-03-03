---
title: "Holé (C) | Microsoft Docs"
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
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 474cb57ced17088c0ce9be8613a9373c702afe69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="naked-c"></a>Naked (C)
**Konkrétní Microsoft**  
  
 Atribut třídy úložiště naked je rozšíření jazyka C specifické pro společnost Microsoft. Pro funkce deklarované s atributem třídy úložiště naked generuje kompilátor kód bez kódu prologu a epilogu. Neviditelné funkce jsou užitečné, potřebujete-li napsat vlastní sekvence kódu prologu a epilogu pomocí vloženého kódu assembleru. Neviditelné funkce jsou užitečné k psaní ovladačů virtuálních zařízení.  
  
 Konkrétní informace o používání holé atribut najdete v tématu [holé funkce](../c-language/naked-functions.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)