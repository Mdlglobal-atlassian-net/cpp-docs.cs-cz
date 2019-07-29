---
title: /MANIFESTINPUT (Určit vstup manifestu)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606463"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Určit vstup manifestu)

Určuje vstupní soubor manifestu, který má být zahrnut do manifestu vloženého do obrázku.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parametry

*Bitmap*<br/>
Soubor manifestu, který má být zahrnut do vloženého manifestu.

## <a name="remarks"></a>Poznámky

Možnost **/MANIFESTINPUT** Určuje cestu ke vstupnímu souboru, který se má použít k vytvoření vloženého manifestu ve spustitelné imagi. Máte-li více vstupních souborů manifestu, použijte přepínač několikrát pro každý vstupní soubor. Vstupní soubory manifestu jsou sloučeny pro vytvoření vloženého manifestu. Tato možnost vyžaduje možnost **/manifest: EMBED** .

Tuto možnost nelze nastavit přímo v sadě Visual Studio. Místo toho použijte vlastnost **Další soubory manifestu** projektu k určení dalších souborů manifestu, které mají být zahrnuty. Další informace najdete v tématu [stránky vlastností nástroje manifestu](manifest-tool-property-pages.md).

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
