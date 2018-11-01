---
title: EDITBIN – odkaz
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: c2c0ee66ed1811755edc33b24737e057554fd01f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542902"
---
# <a name="editbin-reference"></a>EDITBIN – odkaz

Microsoft COFF binární soubor Editor (EDITBIN. Soubor EXE) upraví binárních souborů Common Object File Format (COFF). Editbin – můžete použít k úpravě souborů objektů, spustitelných souborů a dynamické knihovny (DLL).

> [!NOTE]
>  Tento nástroj můžete spustit pouze z příkazového řádku sady Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů.

Editbin – není k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru. Veškeré úpravy binární soubory, které jsou vytvořené pomocí/GL. muset dosáhnout při opětovné kompilaci a propojování.

- [Editbin – příkazový řádek](../../build/reference/editbin-command-line.md)

- [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)

## <a name="see-also"></a>Viz také

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)