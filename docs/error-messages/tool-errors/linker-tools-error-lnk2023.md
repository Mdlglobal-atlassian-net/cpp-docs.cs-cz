---
title: Chyba linkerů Lnk2023 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b53fba3743d6d072930e430c15b79e0e31d68d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302604"
---
# <a name="linker-tools-error-lnk2023"></a>Chyba linkerů LNK2023
Chybný dll nebo vstupní bod \<knihovny dll nebo vstupní bod >  
  
 Nesprávná verze msobj90.dll načítá linkeru. Zajistěte, aby link.exe a msobj90.dll ve své cestě měly stejnou verzi.  
  
 Závislost msobj90.dll nemusí být k dispozici. V seznamu závislostí msobj90.dll je:  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 Zkontrolujte váš počítač pro všechny ostatní kopie msobj90.dll, který může být zastaralý.