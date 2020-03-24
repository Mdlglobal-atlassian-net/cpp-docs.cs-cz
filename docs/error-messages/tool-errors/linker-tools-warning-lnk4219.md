---
title: Upozornění linkerů LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 4488539a4f7282180048f1e3530e62e35c3b339e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183095"
---
# <a name="linker-tools-warning-lnk4219"></a>Upozornění linkerů LNK4219

Oprava přetečení opravy názvu Cílový název symbolu target je mimo rozsah a vkládání převodů.

Linker vložil převod v situaci, kdy se adresa nebo posun nedokázal do dané instrukce vejít, protože cílový symbol je příliš daleko od umístění instrukce.

Je možné změnit pořadí obrázku (například pomocí možnosti [/Order](../../build/reference/order-put-functions-in-order.md) ), abyste zabránili nadbytečné úrovni nepřímých odkazů.
