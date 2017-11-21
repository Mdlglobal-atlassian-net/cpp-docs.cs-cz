---
title: omezit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: restrict_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9176336ac96d88a34d758fd55c09a3a938f371fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="restrict"></a>restrict
**Konkrétní Microsoft**  
  
 Použití deklarace funkce nebo definice, která vrací typ ukazatele, sděluje kompilátoru, že funkce vrátí objekt, pro nějž nebude vytvořen alias s dalšími ukazateli.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(restrict) return_type f();  
```  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor bude šířit `__declspec(restrict)`. Například funkce CRT `malloc` je upravena pomocí `__declspec(restrict)`, a tedy ukazatele inicializované do umístění v paměti pomocí `malloc` budou také zahrnuty jako alias.  
  
 Kompilátor kontroluje, zda není pro ukazatel ve skutečnosti vytvořen alias. Odpovědností vývojáře je zajistit, aby programátor nevytvořil alias na ukazatel, který je označen modifikátorem `restrict __declspec`.  
  
 Podobnou sémantiku na proměnné, najdete v části [__restrict](../cpp/extension-restrict.md).  
  
## <a name="example"></a>Příklad  
 V tématu [noalias](../cpp/noalias.md) pro příklad použití `restrict`.  
  
 Informace o – klíčové slovo omezení, která je součástí C++ AMP najdete v tématu [omezení (C++ AMP)](../cpp/restrict-cpp-amp.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)