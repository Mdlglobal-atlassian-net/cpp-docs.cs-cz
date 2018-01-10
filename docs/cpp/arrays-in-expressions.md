---
title: "Pole ve výrazech | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29f6e16e665d8076ed5a1fe593e1bb9437f1406a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="arrays-in-expressions"></a>Pole ve výrazech
Jakmile identifikátor typu pole se zobrazí ve výrazu jiné než `sizeof`, adresa (**&**), nebo inicializace odkazu, je převedena na ukazatel na první prvek pole. Příklad:  
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 Ukazatel `psz` odkazuje na první prvek pole `szError1`. Všimněte si, že pole, narozdíl od ukazatelů, nejsou upravitelné l-hodnoty. Proto je následující přiřazení neplatné:  
  
```  
szError1 = psz;  
```  
  
## <a name="see-also"></a>Viz také  
 [Pole](../cpp/arrays-cpp.md)