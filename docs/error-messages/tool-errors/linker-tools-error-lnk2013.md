---
title: Chyba Linkerů LNK2013 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04ce4ca8079317da090cf05d43f41e4e40a6b19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041737"
---
# <a name="linker-tools-error-lnk2013"></a>Chyba linkerů LNK2013

opravte typ opravou přetečení. Cílový 'název symbolu' je mimo rozsah

Linker nemůže pojmout potřebné adresy nebo posun do uvedené instrukce, protože cílový symbol je příliš vzdálený od umístění instrukce.

Tento problém lze vyřešit vytvořením více bitových kopií nebo pomocí [/ORDER](../../build/reference/order-put-functions-in-order.md) možnost tak instrukce a cíl byly blíže.

Pokud je název symbolu symbol definovaný uživatelem (nikoli symbol vygenerovaný kompilátorem), lze pro odstranění chyby zkusit také následující akce:

- Změnit statickou funkci na nestatickou.

- Přejmenovat část kódu obsahující statickou funkci, aby byla stejná jako volající.

Chcete-li zjistit, zda je funkce statická, použijte příkaz `DUMPBIN /SYMBOLS`.