---
title: Upozornění Linkerů LNK4075 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a021a9345975dcb197ab578901baf22f76db846
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059651"
---
# <a name="linker-tools-warning-lnk4075"></a>Upozornění linkerů LNK4075

ignoruje kvůli specifikaci "možnost2" číslo "možnost1"

Druhá možnost přepíše první.

Jsou zadané linkeru vzájemně se vylučující možnosti.  Prozkoumejte možnosti linkeru.  Tam, kde jsou možnosti linkeru zadán závisí na tom, jak se sestavení projektu.

- Pokud vytváříte ve vývojovém prostředí, podívejte se do stránky vlastností linkeru pro váš projekt a v tématu, kde jsou zadané obě možnosti linkeru.  Zobrazit [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md) Další informace.

- Při sestavování v příkazovém řádku, podívejte se na možnosti linkeru, existuje zadaná.

- Pokud vytváříte skripty sestavení, projděte vaše skripty, abyste zjistili, kde jsou zadané tyto možnosti linkeru.

Pokud zjistíte, kde jsou zadány možnosti vzájemně se vylučující linkeru, odeberte jednu z možností propojovacího programu.

Některé konkrétní příklady:

- Pokud jste modul, který byl kompilován s **/zi**, což zahrnuje interní linkeru možnost volat neignoruje a modul, který byl kompilován s OPT, /OPT:ICF nebo/incremental: no, které neznamená žádné neignoruje, bude Získejte LNK4075.  Zobrazit [/Z7, / zi, /ZI (formát informací o ladění)](../../build/reference/z7-zi-zi-debug-information-format.md) Další informace.