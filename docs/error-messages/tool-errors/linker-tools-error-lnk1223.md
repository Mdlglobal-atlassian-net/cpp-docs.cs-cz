---
title: Chyba linkerů LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 9c9d4c7224a7e65775354a86bd34fa9ea1b074af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195029"
---
# <a name="linker-tools-error-lnk1223"></a>Chyba linkerů LNK1223

soubor je neplatný nebo poškozený: soubor obsahuje neplatné. pdata příspěvky

V případě platforem RISC, které používají PDATA, k této chybě dojde, pokud kompilátor vygeneroval oddíl. pdata s neseřazenými položkami.

Chcete-li tento problém vyřešit, zkuste kompilovat bez [/GL (celková optimalizace programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) , která je povolena. V některých případech může tato chyba způsobovat i prázdné tělo funkce.
