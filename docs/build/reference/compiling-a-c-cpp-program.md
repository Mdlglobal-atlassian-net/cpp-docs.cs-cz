---
title: MSVC C/C++ reference kompilátoru – Visual Studio
description: MSVC možnosti sady nástrojů kompilátoru.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077379"
---
# <a name="compiling-a-cc-project"></a>Kompilace jazyka C/C++ Project

Možnosti jazyka C++ C a kompilátoru lze nastavit buď v integrovaném vývojovém prostředí sady Visual Studio, nebo na příkazovém řádku.

## <a name="in-visual-studio"></a>V nástroji Visual Studio

Můžete nastavit možnosti kompilátoru pro každý projekt v dialogovém okně **stránky vlastností** sady Visual Studio. V levém podokně vyberte možnost **Vlastnosti konfigurace**, **C/C++**  a pak zvolte kategorii možností kompilátoru. V tématech pro jednotlivé možnosti kompilátoru je popsáno, jak tento parametr nastavíte a kde ho ve vývojovém prostředí najdete. Úplný seznam najdete v tématu [Možnosti kompilátoru MSVC](compiler-options.md) .

## <a name="from-the-command-line"></a>Z příkazového řádku

Možnosti kompilátoru (CL.exe) je možné nastavit:

- [Na příkazovém řádku](compiler-command-line-syntax.md)

- [V souborech příkazů](cl-command-files.md)

- [V proměnné prostředí CL](cl-environment-variables.md)

Možnosti zadané v proměnné prostředí CL se používají při každém vyvolání CL. Pokud je v proměnné prostředí CL nebo na příkazovém řádku uveden název souboru příkazů, použijí se možnosti zadané v tomto souboru příkazů. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.

Možnosti kompilátoru se zpracovávají „zleva doprava“ a při zjištění konfliktu platí poslední parametr (nejvíce vpravo). Proměnná prostředí CL se zpracovává před příkazovým řádkem, takže v případě konfliktů mezi proměnnou prostředí CL a příkazovým řádkem má přednost příkazový řádek.

## <a name="additional-compiler-topics"></a>Další témata týkající se kompilátoru

- [Parametry kompilátoru MSVC](compiler-options.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

- [CL vyvolává linker](cl-invokes-the-linker.md)

Informace o volbě hostitele kompilátoru a cílové architektury naleznete v tématu [Configure C++ projects for 64-bit a cíle x64](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)
