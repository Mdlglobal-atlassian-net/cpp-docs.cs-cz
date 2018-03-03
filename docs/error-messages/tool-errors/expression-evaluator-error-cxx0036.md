---
title: "CXX0036 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdf6ddf412786a53ec8da995c2824274da2da3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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