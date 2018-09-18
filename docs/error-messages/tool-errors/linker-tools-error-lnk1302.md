---
title: Chyba Linkerů LNK1302 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc85b37d58e12602c02c2207c1f38bda9344e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045507"
---
# <a name="linker-tools-error-lnk1302"></a>Chyba linkerů LNK1302

podporuje jenom propojování zabezpečených modulů .NET. nedá se propojit soubor .netmodule

.Netmodule (zkompilovaná **/LN**) byl předán linkeru uživatel pokus o vyvolání jazyka MSIL propojování.  Modulu jazyka C++ je platný pro jazyk MSIL propojení, pokud je kompilován **/CLR: safe**.

Chcete-li opravit tuto chybu, proveďte kompilaci s **/CLR: safe** na povolit propojování na jazyk MSIL, nebo předejte **/CLR** nebo **/CLR: pure** souboru .obj linkeru místo modulu.

Další informace naleznete v tématu

- [/LN (vytvoření modulu MSIL)](../../build/reference/ln-create-msil-module.md)

- [Soubory .netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md)