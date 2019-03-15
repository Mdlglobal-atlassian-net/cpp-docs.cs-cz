---
title: Referenční dokumentace kompilátoru MSVC C/C++ - Visual Studio
description: Možnosti sady nástrojů kompilátoru MSVC.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: 2269ba69cea2702ff190c791eb6753acb3619f7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810299"
---
# <a name="compiling-a-cc-project"></a>Kompilace projektu jazyka C/C++

Možnosti kompilátoru C a C++ lze nastavit v integrovaném vývojovém prostředí sady Visual Studio nebo na příkazovém řádku. 

## <a name="in-visual-studio"></a>In Visual Studio

Můžete nastavit možnosti kompilátoru pro každý projekt v jeho Visual Studio **stránky vlastností** dialogové okno. V levém podokně vyberte **vlastnosti konfigurace**, **C/C++** a pak zvolte kategorii parametrů kompilátoru. V tématech pro jednotlivé možnosti kompilátoru je popsáno, jak tento parametr nastavíte a kde ho ve vývojovém prostředí najdete. Zobrazit [– možnosti kompilátoru MSVC](compiler-options.md) úplný seznam.

## <a name="from-the-command-line"></a>Z příkazového řádku

Možnosti kompilátoru (CL.exe) je možné nastavit:

- [Na příkazovém řádku](compiler-command-line-syntax.md)

- [V souborech příkazů](cl-command-files.md)

- [V proměnné prostředí CL](cl-environment-variables.md)

Možnosti zadané v proměnné prostředí CL se používají při každém vyvolání CL. Pokud je v proměnné prostředí CL nebo na příkazovém řádku uveden název souboru příkazů, použijí se možnosti zadané v tomto souboru příkazů. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.

Možnosti kompilátoru se zpracovávají „zleva doprava“ a při zjištění konfliktu platí poslední parametr (nejvíce vpravo). Proměnná prostředí CL se zpracovává před příkazovým řádkem, takže v případě konfliktů mezi proměnnou prostředí CL a příkazovým řádkem má přednost příkazový řádek.

## <a name="additional-compiler-topics"></a>Další témata týkající se kompilátoru

- [Možnosti kompilátoru MSVC](compiler-options.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

- [CL vyvolává linker](cl-invokes-the-linker.md)

Informace o volbě kompilátoru hostitele a cílové architektury, najdete v části [projekty konfigurace C++ pro 64bitové x64 cíle](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)
