---
title: "Závažná chyba nástroje NMAKE U1099 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1099
dev_langs: C++
helpviewer_keywords: U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e84cb96fdc8b3abfa118d653162e40c90683447a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1099"></a>Závažná chyba nástroje NMAKE U1099
přetečení zásobníku  
  
 Makefile zpracovává byla příliš složitý pro aktuální přidělení zásobníku v nástroji NMAKE. NMAKE má přidělení 0x3000 (12K).  
  
 A zvyšte tak přidělení zásobníku na NMAKE, spusťte [nástroje editbin /stack](../../build/reference/stack.md) nástroj s větší možnost zásobníku:  
  
 **Editbin – /STACK:reserve NMAKE. SOUBOR EXE**  
  
 kde *rezervovat* je číslo větší než aktuální přidělení zásobníku v nástroji NMAKE.