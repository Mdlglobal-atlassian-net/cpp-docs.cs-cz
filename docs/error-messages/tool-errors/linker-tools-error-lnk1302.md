---
title: Chyba linkerů LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160442"
---
# <a name="linker-tools-error-lnk1302"></a>Chyba linkerů LNK1302

podporuje jenom propojování zabezpečených modulů .NET. nedá se propojit soubor .netmodule

.Netmodule (zkompilovaná **/LN**) byl předán linkeru uživatel pokus o vyvolání jazyka MSIL propojování.  Modulu jazyka C++ je platný pro jazyk MSIL propojení, pokud je kompilován **/CLR: safe**.

Chcete-li opravit tuto chybu, proveďte kompilaci s **/CLR: safe** na povolit propojování na jazyk MSIL, nebo předejte **/CLR** nebo **/CLR: pure** souboru .obj linkeru místo modulu.

Další informace naleznete v tématu

- [/LN (vytvoření modulu MSIL)](../../build/reference/ln-create-msil-module.md)

- [Soubory .netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md)