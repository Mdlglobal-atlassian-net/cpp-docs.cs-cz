---
title: Závažná chyba C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203626"
---
# <a name="fatal-error-c1128"></a>Závažná chyba C1128

Počet oddílů překročil limit formátu souboru objektu: zkompilujte s možností /bigobj

Soubor s příponou .obj překročil počet povolených oddílů, omezení formátu objektu souboru COFF.

Dosažení tohoto omezení oddílu může být výsledkem použití [/Gy](../../build/reference/gy-enable-function-level-linking.md) a ladicího sestavení; **/Gy** způsobí, že funkce přejdou do svých vlastních oddílů COMDAT. V laděném sestavení se nachází oddíl informací o ladění pro každou funkci COMDAT.

Upozornění C1128 může být vygenerováno také tehdy, pokud existuje příliš mnoho vložených funkcí.

Chcete-li tuto chybu opravit, rozdělte zdrojový soubor do více souborů zdrojového kódu, zkompilujte bez **/Gy**nebo zkompilujte pomocí [/bigobj (zvyšte počet oddílů v. Soubor obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Pokud nezkompilujete pomocí **/Gy**, bude nutné určit optimalizace jednotlivě, protože **/O2** a **/O1** obě implikují **/Gy**.

Pokud je to možné, proveďte kompilaci bez informací o ladění.

Také může být nutné mít konkrétní instance šablon v samostatných souborech zdrojového kódu, spíše než je nechat vygenerovat kompilátorem.

Při přenosu kódu se C1128 pravděpodobně zobrazí jako první při použití kompilátoru x64 a mnohem později s kompilátorem x86. x64 bude mít minimálně 4 oddíly přidružené k jednotlivým funkcím kompilovaným **/Gy** nebo vložené ze šablon nebo třídy – inline: Code, pdata a Debug info a případně XData.  Kompilátor X86 nebude mít pdata.
