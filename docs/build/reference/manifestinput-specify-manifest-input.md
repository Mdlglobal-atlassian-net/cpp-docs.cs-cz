---
title: /MANIFESTINPUT (Určit vstup manifestu)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: bf192664a7a2402b06621167d91dff67ce0741a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321355"
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

Tuto možnost nelze nastavit přímo v sadě Visual Studio. Místo toho použijte **přídavné soubory manifestu** vlastnosti projektu, chcete-li určit další soubory manifestu k zahrnutí. Další informace najdete v tématu [vstup a výstup, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogového okna stránky vlastností](input-and-output-manifest-tool.md).

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
