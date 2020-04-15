---
title: /MANIFESTINPUT (Určit vstup manifestu)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337495"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Určit vstup manifestu)

Určuje vstupní soubor manifestu, který má být zahrnut do manifestu vloženého do obrazu.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parametry

*Název_souboru*<br/>
Soubor manifestu, který má být zahrnut do vloženého manifestu.

## <a name="remarks"></a>Poznámky

Volba **/MANIFESTINPUT** určuje cestu vstupního souboru, který má být používán k vytvoření vloženého manifestu ve spustitelném obrazu. Pokud máte více vstupních souborů manifestu, použijte přepínač vícekrát – jednou pro každý vstupní soubor. Vstupní soubory manifestu jsou sloučeny a vytvoří vložený manifest. Tato možnost vyžaduje **/MANIFEST:EMBED** možnost.

Tuto možnost nelze nastavit přímo v sadě Visual Studio. Místo toho použijte **vlastnost Další soubory manifestu** projektu k určení dalších souborů manifestu, které mají být zahrnuty. Další informace naleznete v [tématu Manifest Tool Property Pages](manifest-tool-property-pages.md).

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti propojovacího zařízení MSVC](linker-options.md)
