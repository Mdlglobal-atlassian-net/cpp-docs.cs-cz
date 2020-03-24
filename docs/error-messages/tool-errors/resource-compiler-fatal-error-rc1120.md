---
title: Závažná chyba kompilátoru prostředků RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173007"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Závažná chyba kompilátoru prostředků RC1120

nedostatek paměti, počet potřebných bajtů

Kompilátor prostředků má nedostatek úložiště pro položky, které ukládá do své haldy. Obvykle je to výsledek, který má příliš mnoho symbolů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Zvětšete místo ve stránkovacím souboru systému Windows. Další informace o zvětšení místa pro odkládací soubory najdete v tématu virtuální paměť v nápovědě k Windows.

1. Eliminujte nepotřebné soubory zahrnutí, zejména nepotřebné `#define`s a prototypy funkcí.

1. Rozdělte aktuální soubor na dva nebo více souborů a zkompilujte je samostatně.

1. Odeberte ostatní programy nebo ovladače běžící v systému, což by mohlo spotřebovat značné množství paměti.
