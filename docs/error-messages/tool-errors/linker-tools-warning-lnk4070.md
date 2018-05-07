---
title: Upozornění linkerů Lnk4070 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e4599e96552f1b98ef0b1af8d38995ebbe5a83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4070"></a>Upozornění linkerů LNK4070
/OUT:filename – direktiva v. EXP se liší od název výstupního souboru, název souboru'; ignoruje – direktiva  
  
 `filename` Zadaný v [název](../../build/reference/name-c-cpp.md) nebo [KNIHOVNY](../../build/reference/library.md) příkaz při .exp soubor byl vytvořen se liší od výstupu `filename` , byla předpokládá, že ve výchozím nastavení, nebo zadaný [/OUT](../../build/reference/out-output-file-name.md) možnost.  
  
 Toto upozornění se zobrazí, když změníte název výstupního souboru, ve vývojovém prostředí a kde .def souboru projektu nebyl aktualizován. Ručně aktualizujte soubor .def vyřešit toto upozornění.  
  
 Program klienta, který používá výsledné knihoven DLL může dojít k potížím.