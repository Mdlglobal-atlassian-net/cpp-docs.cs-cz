---
title: Chyba linkerů LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194925"
---
# <a name="linker-tools-error-lnk1302"></a>Chyba linkerů LNK1302

podporuje pouze propojování bezpečných. netmodule; Nepovedlo se propojit soubor. netmodule.

A. netmodule (zkompilovaný s **/ln**) byl předán propojovacímu programu v rámci uživatele, který se pokusil vyvolat propojení MSIL.  C++ Modul je platný pro propojení MSIL, pokud je zkompilován s možností **/clr: Safe**.

Chcete-li tuto chybu opravit, zkompilujte s možností **/clr: Safe** , pokud chcete povolit propojení MSIL, nebo předejte soubor **/CLR** nebo **/clr: Pure** . obj místo modulu.

Další informace najdete v tématu

- [/LN (vytvoření modulu MSIL)](../../build/reference/ln-create-msil-module.md)

- [Soubory .netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md)
