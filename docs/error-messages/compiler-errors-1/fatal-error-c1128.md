---
title: Závažná chyba C1128 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0b0c308811b642e0064304cab0688215ac949a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079645"
---
# <a name="fatal-error-c1128"></a>Závažná chyba C1128

Počet oddílů překročil limit formátu souboru objektu: zkompilujte s možností /bigobj

Soubor s příponou .obj překročil počet povolených oddílů, omezení formátu objektu souboru COFF.

Dosažení tohoto omezení oddílů může být způsobeno použitím [/Gy](../../build/reference/gy-enable-function-level-linking.md) a sestavením ladění. **/Gy** způsobí, že funkce přejdou do vlastních oddílů COMDAT. V laděném sestavení se nachází oddíl informací o ladění pro každou funkci COMDAT.

Upozornění C1128 může být vygenerováno také tehdy, pokud existuje příliš mnoho vložených funkcí.

Chcete-li tuto chybu opravit, rozdělte zdrojový soubor do více souborů zdrojového kódu, proveďte kompilaci bez **/Gy**, nebo kompilací s  [ /bigobj (zvýšení počtu oddílů v. Soubor obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Pokud neprovedete kompilaci s **/Gy**, budete muset zadat optimalizace individuálně, protože **/O2** a **/O1** obě implikují **/Gy**.

Pokud je to možné, proveďte kompilaci bez informací o ladění.

Také může být nutné mít konkrétní instance šablon v samostatných souborech zdrojového kódu, spíše než je nechat vygenerovat kompilátorem.

Při přenosu kódu se upozornění C1128 pravděpodobně zobrazí nejprve při použití x64 kompilátoru a později se x86 kompilátoru. x64 bude mít délku minimálně 4 oddíly, které jsou spojené s každou funkcí zkompilovanou **/Gy** nebo vloženou ze šablony či vložené třídy: code, pdata a debug info a případně xdata.  Kompilátor X86 nebude mít pdata.