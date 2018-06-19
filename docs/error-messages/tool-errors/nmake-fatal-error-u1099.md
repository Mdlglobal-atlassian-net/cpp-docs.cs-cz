---
title: Závažná chyba nástroje NMAKE U1099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7be09691de4212d07b1452ffe33725a3978fc053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322101"
---
# <a name="nmake-fatal-error-u1099"></a>Závažná chyba nástroje NMAKE U1099
přetečení zásobníku  
  
 Makefile zpracovává byla příliš složitý pro aktuální přidělení zásobníku v nástroji NMAKE. NMAKE má přidělení 0x3000 (12K).  
  
 A zvyšte tak přidělení zásobníku na NMAKE, spusťte [nástroje editbin /stack](../../build/reference/stack.md) nástroj s větší možnost zásobníku:  
  
 **Editbin – /STACK:reserve NMAKE. SOUBOR EXE**  
  
 kde *rezervovat* je číslo větší než aktuální přidělení zásobníku v nástroji NMAKE.