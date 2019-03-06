---
title: Nastavení možností kompilátoru
ms.date: 11/04/2016
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
ms.openlocfilehash: cc1d4a4a6c782a8ec07cfebfc1905f3c3f8872cf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416290"
---
# <a name="setting-compiler-options"></a>Nastavení možností kompilátoru

Možnosti kompilátoru jazyka C++ a C lze nastavit buď ve vývojovém prostředí, nebo na příkazovém řádku.

## <a name="in-the-development-environment"></a>Ve vývojovém prostředí

Můžete nastavit možnosti kompilátoru pro každý projekt v jeho **stránky vlastností** dialogové okno. V levém podokně vyberte **vlastnosti konfigurace**, **C/C++** a pak zvolte kategorii parametrů kompilátoru. V tématech pro jednotlivé možnosti kompilátoru je popsáno, jak tento parametr nastavíte a kde ho ve vývojovém prostředí najdete. Zobrazit [– možnosti kompilátoru](../../build/reference/compiler-options.md) úplný seznam.

## <a name="outside-the-development-environment"></a>Mimo vývojové prostředí

Možnosti kompilátoru (CL.exe) je možné nastavit:

- [Na příkazovém řádku](../../build/reference/compiler-command-line-syntax.md)

- [V souborech příkazů](../../build/reference/cl-command-files.md)

- [V proměnné prostředí CL](../../build/reference/cl-environment-variables.md)

Možnosti zadané v proměnné prostředí CL se používají při každém vyvolání CL. Pokud je v proměnné prostředí CL nebo na příkazovém řádku uveden název souboru příkazů, použijí se možnosti zadané v tomto souboru příkazů. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.

Možnosti kompilátoru se zpracovávají „zleva doprava“ a při zjištění konfliktu platí poslední parametr (nejvíce vpravo). Proměnná prostředí CL se zpracovává před příkazovým řádkem, takže v případě konfliktů mezi proměnnou prostředí CL a příkazovým řádkem má přednost příkazový řádek.

## <a name="additional-compiler-topics"></a>Další témata týkající se kompilátoru

- [Rychlá kompilace](../../build/reference/fast-compilation.md)

- [CL vyvolává linker](../../build/reference/cl-invokes-the-linker.md)

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)
