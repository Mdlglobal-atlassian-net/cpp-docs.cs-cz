---
title: Závažná chyba C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 83eb5e01eac377b8f19a0e94dc1518e3ed557c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165635"
---
# <a name="fatal-error-c1854"></a>Závažná chyba C1854

> nejde zapsat informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: "*filename*.

Jste zadali [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) možnost po zadání [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) možnost pro stejný soubor.

Chcete-li vyřešit tento problém, obecně nastavit pouze jeden soubor ve vašem projektu a být zkompilován pomocí **/Yc** možnost a nastavte všechny soubory pro kompilaci pomocí **/Yu** možnost. Podrobnosti o použití **/Yc** možnosti a nastavení v integrovaném vývojovém prostředí sady Visual Studio, naleznete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md). Další informace o použití předkompilovaných hlaviček, naleznete v tématu [vytváření Předkompilované soubory hlaviček](../../build/creating-precompiled-header-files.md).
