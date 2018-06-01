---
title: -CLRHEADER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cda2f03e8a0473d2c45f54c96ca97b043d80d5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704438"
---
# <a name="clrheader"></a>/CLRHEADER

Zobrazí informace specifické pro CLR.

## <a name="syntax"></a>Syntaxe

> / CLRHEADER *souboru*

### <a name="arguments"></a>Arguments

|||
|-|-|
*Soubor*| Soubor bitové kopie vytvořené s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Poznámky

**/ CLRHEADER** zobrazí informace o hlavičkách .NET použít libovolné spravované aplikace. Výstup zobrazuje umístění a velikost v bajtech v záhlaví .NET a částech v hlavičce.

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

Při **/CLRHEADER** se používá na soubor, který byl kompilován s volbou/CLR, budou existovat **clr záhlaví:** části ve výstupu dumpbin. Hodnota **příznaky** označuje, která možnost/CLR byl použit:

- 0 – / CLR (image může obsahovat nativního kódu).

Můžete také programově zkontrolovat, pokud byl vytvořený bitovou kopii pro modul common language runtime.  Další informace najdete v tématu [postupy: určení, pokud bitová kopie je nativní nebo CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017. Kód, který musí být "čistý" nebo "bezpečnou" musí být přesně do jazyka C#.

## <a name="see-also"></a>Viz také:

- [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
