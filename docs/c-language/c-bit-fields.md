---
title: C Bit pole | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ebc62a975e534d89fd99dbb05a65e8d6cb379bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-bit-fields"></a>Bitová pole jazyka C
Kromě deklarátory pro členové struktury a sjednocení může být struktura deklarátor také zadaný počet bitů, nazývá "pole bit". Jeho délka nastavena z deklarátor pro název pole dvojtečkou. Bitová pole interpretována jako typ integrální.  
  
## <a name="syntax"></a>Syntaxe  
 *Struktura deklarátor*:  
 *deklarátor*  
  
 *Specifikátor typu deklarátor* opt**:** *konstantní výraz*  
  
 *Konstantní výraz* Určuje šířku pole v bitech. *Specifikátor typu* pro `declarator` musí být `unsigned int`, **podepsané int**, nebo `int`a *konstantní výraz* musí být nezáporné celočíselná hodnota. Pokud je hodnota nula, deklaraci neobsahuje žádné `declarator`. Pole Bitová pole, ukazatele na bitových polí a funkce, které vracejí bitová pole nejsou povoleny. Volitelné `declarator` názvy pole verze. Bitová pole lze deklarovat pouze jako součást struktury. Address-of – operátor (**&**) nelze použít pro součásti bitová pole.  
  
 Nelze na něj odkazovat nepojmenované bitových polí a jejich obsah v době běhu nepředvídatelné. Mohou být použity jako "fiktivní" pole pro účely zarovnání. Nepojmenované bitové pole, jehož šířka je zadaný jako 0 zaručuje, že úložiště pro člena v následujících *seznam struktura prohlášení* začínajícího `int` hranic.  
  
 Bitová pole musí být dostatečně dlouhé, aby obsahovat vzoru bit. Například nejsou právní těchto dvou příkazů:  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
 Tento příklad definuje dvourozměrná pole s názvem struktury `screen`.  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
 Toto pole obsahuje 2 000 prvků. Každý prvek je strukturu jednotlivých obsahující čtyři pole bit členy: `icon`, `color`, `underline`, a `blink`. Velikost jednotlivých struktura je dva bajty.  
  
 Bitová pole mají stejnou sémantiku jako typ celé číslo. To znamená, že bitová pole je použít ve výrazech stejným způsobem jako proměnnou stejného základního typu se použije bez ohledu na to, kolik bits se v poli verze.  
  
 **Konkrétní Microsoft**  
  
 Bit polí definovaných jako `int` jsou považovány za podepsané. Rozšíření Microsoft standardu ANSI C umožňuje `char` a **dlouho** typy (obě **podepsané** a `unsigned`) pro bitových polí. Nepojmenované bitových polí s základní typ **dlouho**, **krátké**, nebo `char` (**podepsané** nebo `unsigned`) vynutit zarovnání k určité hranici podle základního typu.  
  
 Bitová pole jsou přidělené v rámci celé číslo z nejméně významným na většinu významných bitů. V následujícím kódu  
  
```  
struct mybitfields  
{  
    unsigned short a : 4;  
    unsigned short b : 5;  
    unsigned short c : 7;  
} test;  
  
int main( void );  
{  
    test.a = 2;  
    test.b = 31;  
    test.c = 0;  
}  
```  
  
 službu bits by být uspořádána následujícím způsobem:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 Vzhledem k tomu, že 8086 rodina procesorů ukládá nízkou bajt celočíselné hodnoty před vysoké bajtů na celé číslo `0x01F2` by vyšší uložené ve fyzické paměti jako `0xF2` následuje `0x01`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarace struktury](../c-language/structure-declarations.md)