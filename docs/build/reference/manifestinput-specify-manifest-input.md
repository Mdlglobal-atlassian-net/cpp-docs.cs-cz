---
title: -MANIFESTINPUT (určení vstupu manifestu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5259df2216a8c844123c308ece7ac6b0b650ab39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705148"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Určit vstup manifestu)

Určuje vstupní soubor manifestu pro zahrnutí do manifestu, který je vložený v obrazu.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Soubor manifestu pro zahrnutí do vloženého manifestu.

## <a name="remarks"></a>Poznámky

**/MANIFESTINPUT** Určuje cestu vstupního souboru pro použití k tvorbě vloženého manifestu spustitelné bitové kopie. Pokud máte více vstupních souborů manifestu, použijte přepínač vícekrát – jednou pro každý vstupní soubor. Vstupní soubory manifestu jsou sloučeny pro tvorbu vloženého manifestu. Tato možnost vyžaduje **/MANIFEST: EMBED** možnost.

Tuto možnost nelze nastavit přímo v sadě Visual Studio. Místo toho použijte **přídavné soubory manifestu** vlastnosti projektu, chcete-li určit další soubory manifestu k zahrnutí. Další informace najdete v tématu [vstup a výstup, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogového okna stránky vlastností](../../ide/input-and-output-manifest-tool.md).

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)