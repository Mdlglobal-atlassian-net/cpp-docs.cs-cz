---
title: Závažná chyba C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 5ab98c46d60d15cdcb6de22aa922d62453d41880
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204488"
---
# <a name="fatal-error-c1047"></a>Závažná chyba C1047

Soubor nebo soubor knihovny byl vytvořen pomocí staršího kompilátoru než jiné objekty. znovu sestavit staré objekty a knihovny

C1047 je způsobena tím, že soubory objektů nebo knihovny sestavené s **/LTCG** jsou propojeny společně, ale v případě, že jsou tyto soubory objektů nebo C++ knihovny sestaveny s různými verzemi sady nástrojů vizuálu.

K tomu může dojít, pokud začnete používat novou verzi kompilátoru, ale neprovedete čisté opětovné sestavení stávajících souborů nebo knihoven.

Chcete-li vyřešit C1047, znovu sestavte všechny soubory objektů nebo knihovny.
