---
title: Chyba kompilátoru C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 5730102371d00ebaf3ae05fdefb70184b58d7c18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481769"
---
# <a name="compiler-error-c3505"></a>Chyba kompilátoru C3505

> nejde načíst knihovnu typů '*guid*.

C3505 může nastat, pokud jsou spuštěny 32bitové, hostované x86 křížový kompilátor pro 64bitovou verzi, x64 cílí na 64-bit počítače, protože kompilátor běží pod WOW64 a můžete pouze číst z podregistru 32-bit.

Můžete tuto chybu vyřešit vytvořením 32bitové a 64bitové verze knihovny typů, které se pokoušíte importovat a registrujte je oba.  Nebo můžete použít nativní 64bitový kompilátor, který je potřeba změnit váš **adresáře VC ++** vlastnost v integrovaném vývojovém prostředí přejděte na 64bitový kompilátor.

Další informace najdete v tématu,

- [Postupy: Povolení 64bitové sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Postupy: Konfigurace projektů Visual C++ pro 64bitové platformy x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)