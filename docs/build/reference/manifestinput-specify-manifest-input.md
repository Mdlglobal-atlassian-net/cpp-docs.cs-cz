---
title: /MANIFESTINPUT (Určit vstup manifestu)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: bf192664a7a2402b06621167d91dff67ce0741a9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814222"
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

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
