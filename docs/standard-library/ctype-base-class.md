---
title: "ctype_base – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: locale/std::ctype_base
dev_langs: C++
helpviewer_keywords: ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc45c762c4abe772164f2db365361b9f2277a260
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctypebase-class"></a>ctype_base – třída
Třída slouží jako základní třída pro omezující vlastnosti třídy šablony [ctype](../standard-library/ctype-class.md). Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct ctype_base : public locale::facet
{
    enum
 {
    alnum,
 alpha,
    cntrl,
 digit,
    graph,
 lower,
    print,
 punct,
    space,
 upper,
    xdigit
 };
    typedef short mask;
    ctype_base(
 size_t _Refs = 0);

 ~ctype_base();

};
```  
  
## <a name="remarks"></a>Poznámky  
 Definuje masku výčtu. Každý konstanta výčtu charakterizuje jiný způsob, jak klasifikovat znaky, podle definice funkce s podobnými názvy, které jsou deklarované v hlavičce \<ctype.h >. Konstanty jsou:  
  
- **místo** (funkce [isspace –](../standard-library/locale-functions.md#isspace))  
  
- **Tisk** (funkce [isprint –](../standard-library/locale-functions.md#isprint))  
  
- **Stisknutím kláves CTRL +** (funkce [iscntrl –](../standard-library/locale-functions.md#iscntrl))  
  
- **horní** (funkce [isupper –](../standard-library/locale-functions.md#isupper))  
  
- **nižší** (funkce [islower –](../standard-library/locale-functions.md#islower))  
  
- **číslice** (funkce [IsDigit –](../standard-library/locale-functions.md#isdigit))  
  
- **punct** (funkce [ispunct –](../standard-library/locale-functions.md#ispunct))  
  
- **xdigit** (funkce [isxdigit –](../standard-library/locale-functions.md#isxdigit))  
  
- **Alpha** (funkce [isalpha –](../standard-library/locale-functions.md#isalpha))  
  
- **alnum** (funkce [isalnum –](../standard-library/locale-functions.md#isalnum))  
  
- **graf** (funkce [isgraph –](../standard-library/locale-functions.md#isgraph))  
  
 Kombinace klasifikace podle ORing můžete charakterizovat tyto konstanty. Konkrétně je vždy hodnotu true, **alnum** == ( **alpha** &#124; **číslice** \) a **grafu** \= \= \( **alnum** &#124; **punct**).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



