---
title: "Třídy úložiště jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: afec3ea0d88ff7ede9c498a270e2806a4ceb79e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-storage-classes"></a>Třídy úložiště jazyka C
"Třídy úložiště" proměnné určuje, zda položka má životnost "globální" nebo "místní". C volá tyto dvě životnosti "statická" a "automatické". Položka s globální životnost existuje a má hodnotu v průběhu provádění tohoto programu. Všechny funkce mají globální životnosti.  
  
 Automatické proměnné nebo proměnné s místní životnosti jsou přiděleny nové úložiště, každý ovládací prvek čas provádění předá do bloku ve kterém jsou definovány. Při provádění vrátí, proměnné už mít smysl hodnoty.  
  
 C poskytuje následující specifikátory třídy úložiště:  
  
## <a name="syntax"></a>Syntaxe  
 *specifikátor třídy úložiště*:  
 **automaticky**  
  
 **Registrace**  
  
 **statické**  
  
 **extern**  
  
 **Definice TypeDef**  
  
 **__declspec** ( *rozšířené decl – modifikátor seq* ) / * specifické pro Microsoft\*/  
  
 S výjimkou `__declspec`, můžete použít pouze jednu *specifikátor třídy úložiště* v *deklarace specifikátor* v deklaraci. Pokud se žádné určení třídy úložiště, vytvořte deklarace v rámci bloku automaticky objektů.  
  
 Položky deklarovat s **automaticky** nebo **zaregistrovat** specifikátor mít místní životnosti. Položky deklarovat s **statické** nebo `extern` specifikátor mají globální životnosti.  
  
 Vzhledem k tomu `typedef` a `__declspec` se sémanticky liší od jiných čtyři *specifikátor třídy úložiště* terminály, jsou popsány samostatně. Konkrétní informace o `typedef`, najdete v části [Typedef – deklarace](../c-language/typedef-declarations.md). Konkrétní informace o `__declspec`, najdete v části [rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md).  
  
 Umístění deklarace proměnné a funkce v rámci zdrojové soubory ovlivní také třídy úložiště a viditelnosti. Deklarace mimo všechny definice funkcí se říká, že se zobrazí na "externí úrovni". Deklarace v rámci definice funkcí se zobrazí na "interní úrovni".  
  
 Přesný význam jednotlivých specifikátor třídy úložiště závisí na dva faktory:  
  
-   Určuje, zda se zobrazí deklarace na externí nebo interní úrovni  
  
-   Jestli je položka jejich deklarováním proměnné nebo funkce  
  
 [Specifikátory třídy úložiště pro deklarace na externí úrovni](../c-language/storage-class-specifiers-for-external-level-declarations.md) a [specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md) popisují *specifikátor třídy úložiště* terminály v každý typ deklarace a vysvětlují, použije se výchozí chování při *specifikátor třídy úložiště* je vynechaný proměnné. [Specifikátory třídy úložiště s deklaracemi funkce](../c-language/storage-class-specifiers-with-function-declarations.md) popisuje specifikátory třídy úložiště použít s funkcí.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)