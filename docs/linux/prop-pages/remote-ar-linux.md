---
title: Archiv vzdálených vlastnosti (C++ Linux) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
author: mikeblome
ms.author: mblome
f1_keywords: []
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 004e015b7e5ad8a99b3bea2bf21b7b598f2fedbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328650"
---
# <a name="remote-archive-properties-c-linux"></a>Archiv vzdálených vlastnosti (C++ Linux)

Vlastnost | Popis
--- | ---
Vytvoření indexu archivu | Vytvoření indexu archivu (viz ranlib).  To lze urychlit propojení a snížit závislosti v rámci vlastní knihovny.
Vytvořit dynamické archivu | Vytvořte dynamické archivu.  Dynamické archivu obsahuje relativepaths k objektům místo vkládání objektů.  Přepínání mezi tenký a obvykle vyžaduje odstranění existující knihovnu.
Vytvoření bez upozornění na | Bez varování, pokud knihovny vytvoření.
Zkrácení časové razítko | Použijte pro časová razítka a UID/gids nula.
Potlačit úvodní nápis při spouštění | Dont zobrazit číslo verze.
Verbose | Verbose
Další možnosti | Další možnosti.
Výstupní soubor | / Out možnost přepíše výchozí název a umístění program, který vytvoří lib.
Archiver | Určuje program, který má být vyvolán při propojování statické objekty nebo cestu k archiver ve vzdáleném systému.
Časový limit archiver | Časový limit vzdálené archiver, v milisekundách.
Kopírovat výstup | Určuje, jestli zkopírujte výstupní soubor sestavení ze vzdáleného systému v místním počítači.
