---
title: Pole ve výrazech | Dokumentace Microsoftu
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
ms.openlocfilehash: b792bc02cf620cbd961830a99e35ae0c61898fed
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408692"
---
# <a name="arrays-in-expressions"></a>Pole ve výrazech
Když identifikátor typu pole objeví ve výrazu jiné než `sizeof`, adresy (**&**), nebo inicializace odkazu, je převeden na ukazatel na první prvek pole. Příklad:  
  
```cpp 
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 Ukazatel `psz` odkazuje na první prvek pole `szError1`. Všimněte si, že pole, narozdíl od ukazatelů, nejsou upravitelné l-hodnoty. Proto je následující přiřazení neplatné:  
  
```cpp 
szError1 = psz;  
```  
  
## <a name="see-also"></a>Viz také:  
 [Pole](../cpp/arrays-cpp.md)