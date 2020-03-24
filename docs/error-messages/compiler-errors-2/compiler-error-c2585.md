---
title: Chyba kompilátoru C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177388"
---
# <a name="compiler-error-c2585"></a>Chyba kompilátoru C2585

explicitní převod na typ je dvojznačný.

Převod typu může vydávat více než jeden výsledek.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Převod z typu třídy nebo struktury na základě vícenásobné dědičnosti. Pokud typ dědí stejnou základní třídu více než jednou, funkce nebo operátor převodu musí použít překlad oboru (`::`) k určení, které zděděné třídy použít při převodu.

1. Byl definován operátor převodu a konstruktor, který provádí stejnou konverzi.
