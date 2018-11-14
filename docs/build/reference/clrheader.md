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
ms.openlocfilehash: e35cf79cdaa10c9632e1c588e2b49f45cfbef283
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330850"
---
# <a name="clrheader"></a>/CLRHEADER

Zobrazit informace specifické pro CLR.

## <a name="syntax"></a>Syntaxe

> / CLRHEADER *souboru*

### <a name="arguments"></a>Arguments

*Soubor*<br/>
Sestavován soubor obrázku [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Poznámky

**/ CLRHEADER** zobrazí informace o hlavičkách .NET použít libovolné spravované aplikace. Výstup zobrazuje umístění a velikost v bajtech, .NET záhlaví a oddílů v záhlaví.

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

Při **/CLRHEADER** se používá u souboru, který byl zkompilován s parametrem/CLR, bude existovat **clr záhlaví:** část ve výstupu dumpbin. Hodnota **příznaky** označuje, která možnost/CLR. byla použita:

- 0 – / CLR (image může obsahovat nativní kód).

Můžete také programově ověřit, pokud byla vytvořena image pro modul common language runtime.  Další informace najdete v tématu [postupy: určení, pokud je bitová kopie nativní nebo CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Kód, který musí být "čistě" nebo "bezpečné" by měl být přenést do C#.

## <a name="see-also"></a>Viz také:

- [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
