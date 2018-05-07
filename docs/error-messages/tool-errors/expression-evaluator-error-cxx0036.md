---
title: CXX0036 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e1bf3cda85d7b3d64d51279688a52cec5c0336
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0036"></a>Chyba při vyhodnocování výrazu CXX0036
Chybný kontextu {...} specifikace  
  
 Tato zpráva se může objevit žádné několik chyb v použití operátoru kontextu (**{}**).  
  
-   Syntaxe context – operátor (**{}**) byl nesprávně zadán.  
  
     Syntaxe operátor kontextu je:  
  
     {*funkce*,*modulu*,*dll*}*výraz*  
  
     Toto nastavení určuje kontextu *výraz*. Operátor kontextu má stejnou prioritu a využití jako přetypování.  
  
     Koncové čárky lze vynechat. Pokud platí jedna z *funkce*, *modulu*, nebo *dll* obsahuje čárku literál musí uzavřete celý název v závorkách.  
  
-   Název funkce napsán správně nebo neexistuje v zadaném modulu nebo dynamickou knihovnu.  
  
     Protože C je malá a velká písmena jazyk, *funkce* musí mít v případě přesné definovaným ve zdroji.  
  
-   Modul nebo knihovna DLL nebyla nalezena.  
  
     Zkontrolujte název úplná cesta zadaném modulu nebo DLL.  
  
 Tato chyba je stejný jako CAN0036.