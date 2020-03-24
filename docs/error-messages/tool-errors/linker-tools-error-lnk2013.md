---
title: Chyba linkerů LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194743"
---
# <a name="linker-tools-error-lnk2013"></a>Chyba linkerů LNK2013

opravte typ opravou přetečení. Cílový 'název symbolu' je mimo rozsah

Linker nemůže pojmout potřebné adresy nebo posun do uvedené instrukce, protože cílový symbol je příliš vzdálený od umístění instrukce.

Tento problém můžete vyřešit vytvořením několika imagí nebo pomocí možnosti [/Order](../../build/reference/order-put-functions-in-order.md) , aby se instrukce a cíl vzájemně rozblížily.

Pokud je název symbolu symbol definovaný uživatelem (nikoli symbol vygenerovaný kompilátorem), lze pro odstranění chyby zkusit také následující akce:

- Změnit statickou funkci na nestatickou.

- Přejmenovat část kódu obsahující statickou funkci, aby byla stejná jako volající.

Chcete-li zjistit, zda je funkce statická, použijte příkaz `DUMPBIN /SYMBOLS`.
