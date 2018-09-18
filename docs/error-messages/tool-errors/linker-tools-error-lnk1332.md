---
title: Chyba Linkerů LNK1332 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1332
dev_langs:
- C++
helpviewer_keywords:
- LNK1332
ms.assetid: b31d5ca0-c27f-4177-896b-2637dccbde24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b256c61b9e9de6bf19e754054de1f55fcdec5f0b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094517"
---
# <a name="linker-tools-error-lnk1332"></a>Chyba linkerů LNK1332

zjištěna\<count > typy Windows Runtime naimportované do jednoho modulu a definovaný v jiném.

Při jeho aktuální cíl, linker zjistil <`count`> typy Windows Runtime, z nichž každý je naimportované do jednoho modulu a také definované v jiném modulu.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Opravte všechny chyby LNK2039 v sestavení podle návrhu v chybové zprávě.

## <a name="see-also"></a>Viz také

[Chyba linkerů LNK2039](../../error-messages/tool-errors/linker-tools-error-lnk2039.md)<br/>
[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)