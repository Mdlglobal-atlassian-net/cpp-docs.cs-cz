---
title: Upozornění linkerů LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: 1758fffb72e183e8a186d115b2b3f3b30c32e047
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193873"
---
# <a name="linker-tools-warning-lnk4206"></a>Upozornění linkerů LNK4206

> předkompilované informace o typu se nenašly. *název souboru*není propojený nebo přepsaný; propojování objektu, jako by nebyly žádné ladicí informace

Soubor objektu *filename* kompilovaný pomocí [/YC](../../build/reference/yc-create-precompiled-header-file.md)nebyl v příkazu odkazu zadán nebo byl přepsán.

Běžným scénářem tohoto upozornění je, že objekt. obj, který byl zkompilován s/Yc, je v knihovně a kde nejsou žádné odkazy na symboly na objekt. obj z vašeho kódu.  V takovém případě linker nebude používat (nebo dokonce ani vidět) soubor. obj.  V takovém případě byste měli kód znovu kompilovat a používat [/yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pro objekty zkompilované pomocí [/Yu](../../build/reference/yu-use-precompiled-header-file.md).
