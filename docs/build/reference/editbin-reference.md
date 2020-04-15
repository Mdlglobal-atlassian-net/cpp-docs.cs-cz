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
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328340"
---
# <a name="editbin-reference"></a>EDITBIN – odkaz

Binární editor souborů Microsoft COFF (EDITBIN. EXE) upravuje binární soubory formátu Common Object File Format (COFF). Editbin můžete použít k úpravě souborů objektů, spustitelných souborů a knihoven dynamických spojů (DLL).

> [!NOTE]
> Tento nástroj lze spustit pouze z příkazového řádku sady Visual Studio. Nelze jej spustit ze systémového příkazového řádku nebo z Průzkumníka souborů.

EDITBIN není k dispozici pro použití v souborech vytvořených s možností kompilátoru [/GL.](gl-whole-program-optimization.md) Jakékoli změny binárních souborů vytvořených s /GL bude muset být dosaženo rekompilací a propojením.

- [PŘÍKAZOVÝ ŘÁDEK EDITBIN](editbin-command-line.md)

- [MOŽNOSTI EDITBIN](editbin-options.md)

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení msvc](c-cpp-build-tools.md)
