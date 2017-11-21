---
title: "Klíčová slova dědičnosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
dev_langs: C++
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65d338f642d705fec6f1a45b5e88f05c1ee55cc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="inheritance-keywords"></a>Klíčová slova dědičnosti
**Konkrétní Microsoft**  
  
```  
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;  
```  
  
 kde:  
  
 *Název třídy*  
 Název deklarované třídy.  
  
 Jazyk C++ umožňuje deklarovat ukazatel na člen třídy před definicí třídy. Příklad:  
  
```  
class S;  
int S::*p;  
```  
  
 Ve výše, kódu `p` je deklarován jako ukazatel na celé číslo člena třídy S. Ale `class S` má ještě není definován v tomto kódu; ho pouze bylo deklarováno. Když kompilátor na takový ukazatel narazí, musí vytvořit obecné rozlišení ukazatele. Velikost rozlišení je závislá na zadaném modelu dědičnosti. Pro určení modelu dědičnosti existují čtyři způsoby:  
  
-   V prostředí IDE pod **reprezentace ukazatele na člena**  
  
-   Pomocí příkazového řádku [/vmg](../build/reference/vmb-vmg-representation-method.md) přepínače  
  
-   Pomocí [pointers_to_members –](../preprocessor/pointers-to-members.md) – Direktiva pragma  
  
-   Pomocí klíčových slov dědičnosti `__single_inheritance`, `__multiple_inheritance` a `__virtual_inheritance`. Tento postup řídí model dědičnosti na základě každé třídy.  
  
    > [!NOTE]
    >  Je-li vždy po definování třídy deklarován ukazatel na člen třídy, není třeba použít žádnou z těchto možností.  
  
 Deklarování ukazatele na člen třídy před definicí třídy ovlivňuje velikost a rychlost výsledného spustitelného souboru. Čím složitější dědičnost třída používá, tím větší je počet bajtů potřebných k zastoupení ukazatele na člen třídy a tím větší je kód potřebný k interpretaci ukazatele. Jednoduchá dědičnost je nejméně náročná a virtuální dědičnost je nejsložitější.  
  
 Je-li výše uvedený příklad změněn na:  
  
```  
class __single_inheritance S;  
int S::*p;  
```  
  
 ukazatelé na členy třídy `class S` budou používat nejmenší možnou reprezentaci bez ohledu na možnosti příkazového řádku nebo direktivy pragma.  
  
> [!NOTE]
>  Stejná dopředná deklarace reprezentace ukazatele na člen třídy by se měla nacházet v každé jednotce překladu, která deklaruje ukazatele na členy této třídy, a deklarace by se měla objevit před deklarací ukazatelů na členy.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)