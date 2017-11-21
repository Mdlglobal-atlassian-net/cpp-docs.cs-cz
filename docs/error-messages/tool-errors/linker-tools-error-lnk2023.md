---
title: "Chyba linkerů Lnk2023 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2023
dev_langs: C++
helpviewer_keywords: LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37370cd4637680783761e787e6ca38bdd5bada84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2023"></a>Chyba linkerů LNK2023
Chybný dll nebo vstupní bod \<knihovny dll nebo vstupní bod >  
  
 Nesprávná verze msobj90.dll načítá linkeru. Zajistěte, aby link.exe a msobj90.dll ve své cestě měly stejnou verzi.  
  
 Závislost msobj90.dll nemusí být k dispozici. V seznamu závislostí msobj90.dll je:  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 Zkontrolujte váš počítač pro všechny ostatní kopie msobj90.dll, který může být zastaralý.