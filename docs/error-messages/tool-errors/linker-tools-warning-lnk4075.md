---
title: Upozornění linkerů LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183485"
---
# <a name="linker-tools-warning-lnk4075"></a>Upozornění linkerů LNK4075

ignoruje se "možnost1" kvůli specifikaci "možnost2".

Druhá možnost Přepisuje první.

Jsou zadány vzájemně exkluzivní možnosti linkeru.  Projděte si možnosti linkeru.  Kde jsou zadány možnosti linkeru, závisí na způsobu sestavování projektu.

- Pokud sestavíte ve vývojovém prostředí, podívejte se na stránky vlastností linkeru pro váš projekt a zjistěte, kde jsou zadány obě možnosti linkeru.  Další informace naleznete v tématu [Nastavení vlastností kompilátoru a sestavení](../../build/working-with-project-properties.md) .

- Pokud sestavíte na příkazovém řádku, podívejte se na Možnosti linkeru, které tady zadáte.

- Pokud sestavíte pomocí skriptů sestavení, Projděte si skripty, abyste viděli, kde jsou tyto možnosti linkeru určeny.

Pokud zjistíte, kde jsou zadány vzájemně exkluzivní možnosti linkeru, odeberte jednu z možností linkeru.

Některé konkrétní příklady:

- Pokud propojíte modul, který byl zkompilován pomocí **/Zi**, což implikuje interní možnost linkeru s názvem/EDITANDCONTINUE a modul, který byl zkompilován s/OPT: REF,/OPT: ICF nebo/incremental: No, což neznamená, že se nejedná o/EDITANDCONTINUE, získáte linkerů LNK4075.  Další informace naleznete v tématu [/Z7,/Zi,/Zi (formát ladicích informací)](../../build/reference/z7-zi-zi-debug-information-format.md) .
