---
title: Chyba při vyhodnocování výrazu CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195510"
---
# <a name="expression-evaluator-error-cxx0033"></a>Chyba při vyhodnocování výrazu CXX0033

Chyba v informacích o typu OMF

Spustitelný soubor neměl pro ladění platný formát modulu objektů (OMF).

Tato chyba je shodná s CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Spustitelný soubor nebyl vytvořen pomocí linkeru, který byl vydán v této verzi vizuálu C++. Znovu propojte kód objektu pomocí aktuální verze souboru LINK. exe.

1. Soubor. exe byl pravděpodobně poškozen. Zkompilujte program znovu a znovu propojte.
