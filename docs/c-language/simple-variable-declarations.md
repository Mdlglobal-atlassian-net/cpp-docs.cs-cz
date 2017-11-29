---
title: "Deklarace jednoduchých proměnných | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dd5ab69e0e6621324f04008c34b2a52dcbd20787
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="simple-variable-declarations"></a>Deklarace jednoduchých proměnných
Prohlášení o jednoduché proměnné nejjednodušší forma přímé deklarátor, určuje název a typ proměnné. Určuje také třídy úložiště proměnné a datového typu.  
  
 Třídy úložiště nebo typy (nebo obě) je nutné, deklarace proměnných. Proměnné bez typu (například `var;`) generovat upozornění.  
  
## <a name="syntax"></a>Syntaxe  
 `declarator`:  
 *ukazatel* opt  
  
 *deklarátor přímo*  
  
 *deklarátor přímo*:  
 *identifikátor*  
  
 *identifikátor*:  
 *nečíselným*  
  
 *identifikátor nečíselným*  
  
 *identifikátor číslice*  
  
 Pro aritmetické, struktury, sjednocení, výčty a void typy a pro typy reprezentována `typedef` názvy, jednoduché deklarátory můžete použít v deklaraci, protože specifikátor typu poskytuje zadáním informace. Ukazatele, pole a typy funkce vyžadují složitější deklarátory.  
  
 Můžete použít seznam identifikátorů oddělených čárkami (**,**) k určení několika proměnných ve stejné deklaraci. Všechny proměnné definované v deklaraci mají stejné základní typ. Příklad:  
  
```  
int x, y;        /* Declares two simple variables of type int */  
int const z = 1; /* Declares a constant value of type int */  
```  
  
 Proměnné `x` a `y` mohou být uloženy jakoukoli hodnotu v sadě definované `int` typu pro konkrétní implementaci. Jednoduchého objektu `z` je inicializován na hodnotu 1 a není změn.  
  
 Pokud deklaraci `z` byla Neinicializovaný statické proměnné nebo byla v rozsahu souboru získá má počáteční hodnotu 0 a by tato hodnota byla unmodifiable.  
  
```  
unsigned long reply, flag; /* Declares two variables  
                              named reply and flag     */  
```  
  
 V tomto příkladu obě proměnné, `reply` a `flag`, mají `unsigned long` zadejte a podržením nepodepsané celočíselné hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)