---
title: Upozornění Linkerů LNK4098 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2068534d51ae1350510a349f875c1977299edb1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019147"
---
# <a name="linker-tools-warning-lnk4098"></a>Upozornění linkerů LNK4098

DEFAULTLIB 'library' je v konfliktu s použitím jiných knihoven; Použijte/NODEFAULTLIB: library

Pokoušíte se propojit s kompatibilní knihovny.

> [!NOTE]
>  Knihovny za běhu nyní obsahovat direktivy, aby se zabránilo kombinace různých typů. Zobrazí se toto upozornění, pokud se pokusíte použít různé typy nebo ladění a verze knihovny run-time ve stejném programu. Například pokud jste kompilaci jednoho souboru chcete použít jeden druh běhové knihovny a další soubor použít jiný typ (například s jedním vláknem a s více vlákny) a propojit je se pokusil, se zobrazí toto upozornění. Byste měli kompilovat všechny zdrojové soubory používat stejné knihovny run-time. Zobrazit [použití knihovny Run-Time](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) možnosti kompilátoru pro další informace.

Můžete použít propojovacího programu [: lib](../../build/reference/verbose-print-progress-messages.md) přepínač tak, aby určit, které knihovny hledání linkeru. Pokud se zobrazí LNK4098 a chcete-li vytvořit spustitelný soubor, který používá, například jednovláknový, bez ladění runtime knihoven, použijte **: lib** možnost zjistit, které knihovny hledání linkeru. Propojovací program by měl vytisknout LIBC.lib a není LIBCMT.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib nebo MSVCRTD.lib jako Prohledané knihovny. Poznáte linkeru, aby ignorovat nesprávné knihovny za běhu pomocí [: / NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pro každou knihovnu, kterou chcete ignorovat.

Následující tabulka uvádí, které knihovny mají být ignorovány, v závislosti na tom, které knihovny run-time, kterou chcete použít.

|Použití této knihovny run-time|Ignorovat tyto knihovny|
|-----------------------------------|----------------------------|
|S jedním vláknem (libc.lib)|Libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Vícevláknové (libcmt.lib)|Libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Vícevláknové použití knihovny DLL (msvcrt.lib)|Libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Ladění s jedním vláknem (libcd.lib)|Libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, msvcrtd.lib|
|Ladění vícevláknových (libcmtd.lib)|Libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, msvcrtd.lib|
|Ladění vícevláknové použití knihovny DLL (msvcrtd.lib)|Libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|

Například pokud obdržíte toto upozornění a chcete ji vytvořit spustitelný soubor, který používá verzi knihovny za běhu bez ladění, s jedním vláknem, můžete použít následující možnosti pomocí linkeru:

```
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```