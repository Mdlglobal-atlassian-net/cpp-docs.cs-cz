---
title: Chyba kompilátoru C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311745"
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