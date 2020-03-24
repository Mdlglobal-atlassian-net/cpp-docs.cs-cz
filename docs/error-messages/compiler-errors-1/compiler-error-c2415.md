---
title: Chyba kompilátoru C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205618"
---
# <a name="compiler-error-c2415"></a>Chyba kompilátoru C2415

nesprávný typ operandu

Operační kód nepoužívá operandy tohoto typu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Operační kód nepodporuje počet použitých operandů. Zkontrolujte referenční příručku pro sestavení jazyka a určete správný počet operandů.

1. Novější procesor podporuje instrukci s dalšími typy. Pokud chcete použít novější procesor, upravte možnost [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) .
