---
title: "Upozornění linkerů Lnk4070 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4070
dev_langs: C++
helpviewer_keywords: LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca0a31fb3512b7b11150984fc3d15013cb75c0e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4070"></a>Upozornění linkerů LNK4070
/OUT:filename – direktiva v. EXP se liší od název výstupního souboru, název souboru'; ignoruje – direktiva  
  
 `filename` Zadaný v [název](../../build/reference/name-c-cpp.md) nebo [KNIHOVNY](../../build/reference/library.md) příkaz při .exp soubor byl vytvořen se liší od výstupu `filename` , byla předpokládá, že ve výchozím nastavení, nebo zadaný [/OUT](../../build/reference/out-output-file-name.md) možnost.  
  
 Toto upozornění se zobrazí, když změníte název výstupního souboru, ve vývojovém prostředí a kde .def souboru projektu nebyl aktualizován. Ručně aktualizujte soubor .def vyřešit toto upozornění.  
  
 Program klienta, který používá výsledné knihoven DLL může dojít k potížím.