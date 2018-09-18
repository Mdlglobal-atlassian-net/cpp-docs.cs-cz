---
title: Chyba kompilátoru C2220 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4179b396e732ceeea20aeb9428d841a357a6d1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051318"
---
# <a name="compiler-error-c2220"></a>Chyba kompilátoru C2220

upozornění se zpracovalo jako chyba – nevygeneroval se žádný objekt soubor

[/WX](../../build/reference/compiler-option-warning-level.md) instruuje kompilátor, aby považovat všechna upozornění jako chyby. Protože došlo k chybě, byl generován žádný objekt nebo spustitelný soubor.

Tato chyba se zobrazí, pouze když **/WX** je příznak nastaven a během kompilace dojde k upozornění. Chcete-li tuto chybu opravit, musíte odstranit každé varování v projektu.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Pokud chcete vyřešit, použijte jednu z následujících postupů

- Opravte problémy, které způsobují upozornění ve vašem projektu.

- Kompilace na nižší úrovni upozornění – například použít **w3** místo **/W4**.

- Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro zakázání nebo potlačení konkrétního upozornění.

- Nepoužívejte **/WX** ke kompilaci.