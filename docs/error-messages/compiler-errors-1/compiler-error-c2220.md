---
title: Chyba kompilátoru C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206658"
---
# <a name="compiler-error-c2220"></a>Chyba kompilátoru C2220

Upozornění se považuje za chybu – negeneroval se žádný soubor objektu.

[/WX](../../build/reference/compiler-option-warning-level.md) říká kompilátoru, aby považoval všechna upozornění za chyby. Protože došlo k chybě, nebyl vygenerován žádný objekt nebo spustitelný soubor.

Tato chyba se zobrazí pouze v případě, že je nastaven příznak **/WX** a během kompilace dojde k upozornění. Chcete-li tuto chybu opravit, je nutné eliminovat všechna upozornění v projektu.

### <a name="to-fix-use-one-of-the-following-techniques"></a>K opravě použijte některý z následujících postupů:

- Opravte problémy, které způsobují upozornění v projektu.

- Zkompilujte na nižší úrovni upozornění, například použijte **/w3** namísto **/W4**.

- Použijte direktivu pragma [Upozornění](../../preprocessor/warning.md) k zakázání nebo potlačení konkrétního upozornění.

- Nepoužívejte **/WX** ke kompilaci.
