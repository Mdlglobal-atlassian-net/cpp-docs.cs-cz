---
title: Upozornění nástroje BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 57858827439ac8cc11e3718d7a484124ae8a6d74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197441"
---
# <a name="bscmake-warning-bk4504"></a>Upozornění nástroje BSCMAKE BK4504

soubor obsahuje příliš mnoho odkazů. ignorují se další odkazy z tohoto zdroje.

Soubor. cpp obsahuje více než 64 000 odkazů na symboly. Pokud BSCMAKE v souboru narazí na odkazy 64 000, ignorují se všechny další odkazy.

Chcete-li tento problém vyřešit, buď soubor rozdělte do dvou nebo více souborů, z nichž každý má méně než 64 000 odkazů na symbol, nebo použijte direktivu preprocesoru `#pragma component(browser)` k omezení symbolů, které jsou generovány pro konkrétní odkazy. Další informace najdete v tématu [Komponenta](../../preprocessor/component.md).
