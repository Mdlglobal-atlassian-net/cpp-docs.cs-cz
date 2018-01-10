---
title: "Typ pro textové literály | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2342777bfd2b1a039e68766e8dfe00ac2fa2f932
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-for-string-literals"></a>Typ pro textové literály
Textové literály mít typ pole `char` (tedy **char []**). (Široká charakterová řetězce mít typ pole `wchar_t` (tedy **[] wchar_t**).) To znamená, že řetězec je pole s prvky typu `char`. Počet prvků v poli je roven počtu znaků v řetězci plus jeden pro ukončující znak null.  
  
## <a name="see-also"></a>Viz také  
 [Textové literály jazyka C](../c-language/c-string-literals.md)