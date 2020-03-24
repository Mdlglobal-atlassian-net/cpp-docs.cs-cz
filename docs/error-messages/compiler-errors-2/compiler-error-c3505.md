---
title: Chyba kompilátoru C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 0c67eb46208c35c1b11a74898107ad3c0e6e570d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200847"
---
# <a name="compiler-error-c3505"></a>Chyba kompilátoru C3505

> Nelze načíst knihovnu typů '*GUID*'

C3505 může být způsobena tím, že spouštíte 32 x86-bit pro procesory x86 pro 64-bit v počítači s 64, protože kompilátor je spuštěn v prostředí WOW64 a lze jej číst pouze 32 z 16bitového podregistru.

Tuto chybu můžete vyřešit vytvořením 32 a 64 bitových verzí knihovny typů, kterou se pokoušíte importovat, a jejich registrací.  Můžete také použít nativní kompilátor 64, který vyžaduje změnu vlastnosti **adresářů VC + +** v rozhraní IDE, aby odkazovala na 64 kompilátor.

Další informace najdete v tématu.

- [Postupy: Povolení 64bitové sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Postupy: Konfigurace projektů Visual C++ pro 64bitové platformy x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
