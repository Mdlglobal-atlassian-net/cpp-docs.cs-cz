---
title: Upozornění linkerů LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 790b0fa25bbf41c38b843e1a2ea757fdc0d10b9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395102"
---
# <a name="linker-tools-warning-lnk4204"></a>Upozornění linkerů LNK4204

'filename' neobsahuje ladicí informace pro odkazující modul objekt se propojí, jako by nebyly dostupné žádné ladicí informace

Soubor PDB má chybný podpis. Propojovací program bude pokračovat k propojení objektu bez ladicích informací. Možná budete chtít znovu zkompilovat pomocí souboru objektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost.

LNK4204 může dojít, pokud některé objekty v knihovně odkazovat na soubor, který již existuje. Tato situace může nastat například při opětovném sestavování řešení objektový soubor může být odstraněn a nelze znovu sestavit kvůli chybě při kompilaci. V takovém případě buď kompilací s **/Z7**, nebo **/Fd**, aktualizovat objekty, které chcete odkazovat na jeden soubor na knihovnu (který není výchozí název souboru PDB).  Další informace najdete v tématu [/Fd (název souboru databáze programu)](../../build/reference/fd-program-database-file-name.md).  Ujistěte se, že PDB je uložen s knihovnou pokaždé, když se aktualizuje v systému správy zdrojového kódu.