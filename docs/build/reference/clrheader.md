---
title: /CLRHEADER
ms.date: 11/04/2016
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 6a1240e2d3ad2ac3a454c610a6f49d07e50951e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820699"
---
# <a name="clrheader"></a>/CLRHEADER

Zobrazit informace specifické pro CLR.

## <a name="syntax"></a>Syntaxe

> / CLRHEADER *souboru*

### <a name="arguments"></a>Arguments

*Soubor*<br/>
Sestavován soubor obrázku [/CLR](clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Poznámky

**/ CLRHEADER** zobrazí informace o hlavičkách .NET použít libovolné spravované aplikace. Výstup zobrazuje umístění a velikost v bajtech, .NET záhlaví a oddílů v záhlaví.

Pouze [/HEADERS](headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](gl-whole-program-optimization.md) – možnost kompilátoru.

Při **/CLRHEADER** se používá u souboru, který byl zkompilován s parametrem/CLR, bude existovat **clr záhlaví:** část ve výstupu dumpbin. Hodnota **příznaky** označuje, která možnost/CLR. byla použita:

- 0 – / CLR (image může obsahovat nativní kód).

Můžete také programově ověřit, pokud byla vytvořena image pro modul common language runtime.  Další informace najdete v tématu [jak: Určit, pokud je bitová kopie nativní nebo CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Kód, který musí být "čistě" nebo "bezpečné" by měl být přenést do C#.

## <a name="see-also"></a>Viz také:

- [DUMPBIN – možnosti](dumpbin-options.md)
