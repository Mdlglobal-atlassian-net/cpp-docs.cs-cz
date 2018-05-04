---
title: Přidělování nulové paměti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0de013e9ddd3fb983436bf6ee0db290458936eb5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="allocating-zero-memory"></a>Přidělování nulové paměti
**ANSI 4.10.3** chování `calloc`, `malloc`, nebo `realloc` fungovat, pokud je požadovaná velikost je nulová.  
  
 Funkce `calloc`, `malloc` a `realloc` přijímají nulu jako argument. Není přidělena žádná skutečná paměť, ale je vrácen platný ukazatel a blok paměti lze modifikovat později pomocí funkce realloc.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)