---
title: Upozornění linkerů LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 98c53c9b998e9bd544c1cc72bd2b0c3fd2b0a418
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193859"
---
# <a name="linker-tools-warning-lnk4204"></a>Upozornění linkerů LNK4204

v názvu souboru chybí ladicí informace pro odkazující modul. propojování objektu, jako by nebyly žádné ladicí informace

Soubor. pdb má chybný podpis. Linker bude pokračovat v propojení tohoto objektu bez ladicích informací. Je možné, že budete chtít znovu zkompilovat soubor objektu pomocí možnosti [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

K LINKERŮ LNK4204 může dojít, pokud některé objekty v knihovně odkazují na soubor, který již neexistuje. K tomu může dojít při opakovaném sestavování řešení, například. soubor objektu může být odstraněn a nebude znovu sestaven z důvodu chyby kompilace. V tomto případě buď zkompilujte s **/Z7**nebo **/FD**, aby se objekty aktualizovaly tak, aby odkazovaly na jeden soubor pro knihovnu (což není výchozí název souboru. pdb).  Další informace najdete v tématu [/FD (název souboru databáze programu)](../../build/reference/fd-program-database-file-name.md).  Zajistěte, aby byl soubor. pdb uložen spolu s knihovnou pokaždé, když se aktualizuje v systému správy zdrojového kódu.
