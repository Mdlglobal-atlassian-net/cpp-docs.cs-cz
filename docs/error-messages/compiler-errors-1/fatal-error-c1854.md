---
title: Závažná chyba C1854 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83450169ec928bb77e46916619c84b3b9a3443a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029387"
---
# <a name="fatal-error-c1854"></a>Závažná chyba C1854

> nejde zapsat informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: "*filename*.

Jste zadali [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) možnost po zadání [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) možnost pro stejný soubor.

Chcete-li vyřešit tento problém, obecně nastavit pouze jeden soubor ve vašem projektu a být zkompilován pomocí **/Yc** možnost a nastavte všechny soubory pro kompilaci pomocí **/Yu** možnost. Podrobnosti o použití **/Yc** možnosti a nastavení v integrovaném vývojovém prostředí sady Visual Studio, naleznete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md). Další informace o použití předkompilovaných hlaviček, naleznete v tématu [vytváření Předkompilované soubory hlaviček](../../build/reference/creating-precompiled-header-files.md).
