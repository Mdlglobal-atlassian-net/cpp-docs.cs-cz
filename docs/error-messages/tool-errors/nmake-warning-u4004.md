---
title: Upozornění nástroje NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: d59b5656d76025fa56bfc76bad800659f25acf53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193196"
---
# <a name="nmake-warning-u4004"></a>Upozornění nástroje NMAKE U4004

příliš mnoho pravidel pro cíl ' TargetName '

Pro daný cíl byl zadán více než jeden blok popisu pomocí jednoduchých dvojtečk ( **:** ) jako oddělovačů. NMAKE provedl příkazy v bloku prvního popisu a ignoruje později bloky.

Chcete-li zadat stejný cíl v několika závislostech, použijte jako oddělovač v každé čáře závislosti dvojité dvojtečky (`::`).
