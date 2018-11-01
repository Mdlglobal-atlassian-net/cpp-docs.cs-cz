---
title: Chyba linkerů LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 4d932a89f1b0bde27f6de2f84b2ed103dab1b1b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620724"
---
# <a name="linker-tools-error-lnk2013"></a>Chyba linkerů LNK2013

opravte typ opravou přetečení. Cílový 'název symbolu' je mimo rozsah

Linker nemůže pojmout potřebné adresy nebo posun do uvedené instrukce, protože cílový symbol je příliš vzdálený od umístění instrukce.

Tento problém lze vyřešit vytvořením více bitových kopií nebo pomocí [/ORDER](../../build/reference/order-put-functions-in-order.md) možnost tak instrukce a cíl byly blíže.

Pokud je název symbolu symbol definovaný uživatelem (nikoli symbol vygenerovaný kompilátorem), lze pro odstranění chyby zkusit také následující akce:

- Změnit statickou funkci na nestatickou.

- Přejmenovat část kódu obsahující statickou funkci, aby byla stejná jako volající.

Chcete-li zjistit, zda je funkce statická, použijte příkaz `DUMPBIN /SYMBOLS`.