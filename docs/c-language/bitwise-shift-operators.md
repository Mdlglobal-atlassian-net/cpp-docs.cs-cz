---
title: "Operátory bitového posunutí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e13e65e42febf2256e11bcb428e98805cdd6550f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bitwise-shift-operators"></a>Operátory bitového posunutí
Operátory posunutí posunutí doleva jejich první operand (`<<`) nebo doprava (`>>`) podle počtu pozic Druhý operand určuje.  
  
## <a name="syntax"></a>Syntaxe  
 *SHIFT – výraz*:  
 *doplňkové – výraz*  
  
 *výraz SHIFT*`<<`*doplňkové výraz shift výraz*`>>`*doplňkové – výraz*   
  
 Oba operandy musí být celočíselné hodnoty. Obvyklé aritmetické převody; provést tyto operátory Typ výsledku je typ levý operand po převodu.  
  
 U leftward posuny vacated správných bitů nastavení na hodnotu 0. Pro rightward posuny jsou vyplněny vacated levé bits na základě typu první operand po převodu. Pokud je typ `unsigned`, jsou nastavené na hodnotu 0. Jinak jsou naplní se přihlašovací bitové kopie. Pro operátory posunutí doleva bez přetečení, příkaz  
  
```  
expr1 << expr2   
```  
  
 je ekvivalentní násobení 2<sup>Výraz2</sup>. Pro operátory posunutí doprava  
  
```  
expr1 >> expr2   
```  
  
 je ekvivalentní dělení 2<sup>Výraz2</sup> Pokud `expr1` je bez znaménka nebo má hodnotu nezáporné.  
  
 Výsledek operace posunutí není definován, pokud druhý operand je záporný nebo pokud pravý operand je větší než nebo rovna šířce v bitech propagovaných levý operand.  
  
 Vzhledem k tomu, že převody provést pomocí k posunu neposkytují operátory přetečení nebo podtečení podmínky, informace mohou být ztracena, pokud výsledek operace posunutí není možné vyjádřit v typ první operand po převodu.  
  
```  
unsigned int x, y, z;  
  
x = 0x00AA;  
y = 0x5500;  
  
z = ( x << 8 ) + ( y >> 8 );  
```  
  
 V tomto příkladu `x` přesunuty zbývajících osm pozic a `y` je posunuté právo osm pozic. Přidání posunuté hodnot, udělíte 0xAA55 a přiřazení `z`.  
  
 Záporná s posunem vpravo výsledkem poloviční původní hodnota zaokrouhlí směrem dolů. Například-253 (binární 11111111 00000011) zapuštěno správné jeden bit vytváří-127 (binární 11111111 10000001). Pozitivní 253 posuny doprava k vytvoření +126.  
  
 Posun doprava zachovává bit znaménka. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán.  
  
## <a name="see-also"></a>Viz také  
 [Operátory posunu vlevo a vpravo (>> a <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)