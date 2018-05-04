---
title: Pole ve výrazech | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3e57a97d9be3ef6245c09c6112caf72318fe784
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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