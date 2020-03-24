---
title: Chyba kompilátoru C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: fbe627a57e5defc499a4bc5d463e0bf33494acba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205657"
---
# <a name="compiler-error-c2414"></a>Chyba kompilátoru C2414

Neplatný počet operandů

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Operační kód nepodporuje počet použitých operandů. Zkontrolujte referenční příručku pro sestavení jazyka a určete správný počet operandů.

1. Novější procesor podporuje instrukci s jiným počtem operandů. Pokud chcete použít novější procesor, upravte možnost [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) .
