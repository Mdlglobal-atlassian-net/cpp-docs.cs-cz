---
title: Závažná chyba C1010 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae762c15c96ed7c12a20d2070d22cdc556667ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064084"
---
# <a name="fatal-error-c1010"></a>Závažná chyba C1010

Neočekávaný konec souboru při hledání předkompilované hlavičky. Nezapomněli jste přidat ' #include název "ke zdroji?

Zadaný soubor include [/Yu](../../build/reference/yu-use-precompiled-header-file.md) není uveden ve zdrojovém souboru.  Tato možnost je povolená ve výchozím nastavení ve většině typů projektu Visual C++ a "stdafx.h" je výchozí zahrnout soubor určený parametrem tuto možnost.

V prostředí Visual Studio použijte jednu z následujících metod pro vyřešení této chyby:

- Pokud nepoužijete předkompilovaných hlaviček v projektu, nastavte **vytvořit/použít předkompilovanou hlavičku** vlastnost zdrojové soubory pro **není použití předkompilovaných hlaviček**. Nastavení této možnosti kompilátoru, postupujte podle těchto kroků:

   1. V podokně Průzkumník řešení projektu, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.

   1. V levém podokně klikněte **C/C++** složky.

   1. Klikněte na tlačítko **předkompilované hlavičky** uzlu.

   1. V pravém podokně klikněte na tlačítko **vytvoření a použití předkompilovaných hlaviček**a potom klikněte na tlačítko **není použití předkompilovaných hlaviček**.

- Ujistěte se, že máte nikoli neúmyslně odstranit, přejmenovat nebo odebrat soubor hlaviček (ve výchozím nastavení, stdafx.h) z aktuálního projektu. Tento soubor se také musí být součástí než jakýkoli jiný kód ve zdrojových souborech pomocí **#include "stdafx.h"**. (Tento soubor hlavičky je zadán jako **vytvořit/použít PCH prostřednictvím souboru** vlastnosti projektu)