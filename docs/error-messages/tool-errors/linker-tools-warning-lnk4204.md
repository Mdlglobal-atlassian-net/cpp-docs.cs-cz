---
title: Upozornění Linkerů LNK4204 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee6164f20bbf91a8cb0b88d8a1333107f239d3f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136230"
---
# <a name="linker-tools-warning-lnk4204"></a>Upozornění linkerů LNK4204

'filename' neobsahuje ladicí informace pro odkazující modul objekt se propojí, jako by nebyly dostupné žádné ladicí informace

Soubor PDB má chybný podpis. Propojovací program bude pokračovat k propojení objektu bez ladicích informací. Možná budete chtít znovu zkompilovat pomocí souboru objektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost.

LNK4204 může dojít, pokud některé objekty v knihovně odkazovat na soubor, který již existuje. Tato situace může nastat například při opětovném sestavování řešení objektový soubor může být odstraněn a nelze znovu sestavit kvůli chybě při kompilaci. V takovém případě buď kompilací s **/Z7**, nebo **/Fd**, aktualizovat objekty, které chcete odkazovat na jeden soubor na knihovnu (který není výchozí název souboru PDB).  Další informace najdete v tématu [/Fd (název souboru databáze programu)](../../build/reference/fd-program-database-file-name.md).  Ujistěte se, že PDB je uložen s knihovnou pokaždé, když se aktualizuje v systému správy zdrojového kódu.