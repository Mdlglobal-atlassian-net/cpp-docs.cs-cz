---
title: Závažná chyba C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: feb385161c9bc13d89052b4947174fbdce7a0d00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457379"
---
# <a name="fatal-error-c1854"></a>Závažná chyba C1854

> nejde zapsat informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: "*filename*.

Jste zadali [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) možnost po zadání [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) možnost pro stejný soubor.

Chcete-li vyřešit tento problém, obecně nastavit pouze jeden soubor ve vašem projektu a být zkompilován pomocí **/Yc** možnost a nastavte všechny soubory pro kompilaci pomocí **/Yu** možnost. Podrobnosti o použití **/Yc** možnosti a nastavení v integrovaném vývojovém prostředí sady Visual Studio, naleznete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md). Další informace o použití předkompilovaných hlaviček, naleznete v tématu [vytváření Předkompilované soubory hlaviček](../../build/reference/creating-precompiled-header-files.md).
