---
title: "Přidělování nulové paměti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 010e6b42c2c5ef1cb78fbbf446b77221caf25e14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-zero-memory"></a>Přidělování nulové paměti
**ANSI 4.10.3** chování `calloc`, `malloc`, nebo `realloc` fungovat, pokud je požadovaná velikost je nulová.  
  
 Funkce `calloc`, `malloc` a `realloc` přijímají nulu jako argument. Není přidělena žádná skutečná paměť, ale je vrácen platný ukazatel a blok paměti lze modifikovat později pomocí funkce realloc.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)