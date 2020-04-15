---
title: Referenční dokumentace nástroje XDCMake
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: 9970470d1feb471f9e0b8c9284a08337dac7ef0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335861"
---
# <a name="xdcmake-reference"></a>Referenční dokumentace nástroje XDCMake

xdcmake.exe je program, který kompiluje soubory .xdc do souboru XML. Soubor XDC je vytvořen kompilátorem MSVC pro každý soubor zdrojového kódu, když je zdrojový kód kompilován s [/doc](doc-process-documentation-comments-c-cpp.md) a když soubor zdrojového kódu obsahuje komentáře dokumentace označené značkami XML.

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Použití souboru xdcmake.exe ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete složku **Vlastnosti konfigurace.**

1. Klepněte na stránku **vlastností Komentáře dokumentu XML.**

> [!NOTE]
> možnosti xdcmake.exe na příkazovém řádku se liší od možností při použití nástroje xdcmake.exe ve vývojovém prostředí (stránkách vlastností). Informace o použití nástroje xdcmake.exe ve vývojovém prostředí naleznete v tématu [XML Document Generator Tool Property Pages](xml-document-generator-tool-property-pages.md).

## <a name="syntax"></a>Syntaxe

xdcmake`input_filename options`

## <a name="parameters"></a>Parametry

*input_filename*<br/>
Název souboru .xdc použitý jako vstup do souboru xdcmake.exe. Zadejte jeden nebo více souborů .xdc nebo použijte *.xdc k použití všech souborů .xdc v aktuálním adresáři.

*Možnosti*<br/>
Nula nebo více z následujících položek:

|Možnost|Popis|
|------------|-----------------|
|/?, /nápověda|Zobrazit nápovědu pro xdcmake.exe.|
|/assembly:*název souboru*|Umožňuje určit hodnotu značky \<> sestavení v souboru XML.  Ve výchozím nastavení je \<hodnota značky> sestavení stejná jako název souboru XML.|
|/nologo|Potlačit zprávu o autorských právech.|
|/out:*název souboru*|Umožňuje zadat název souboru XML.  Ve výchozím nastavení je název souboru XML názvem prvního souboru XDC zpracovaného souborem xdc.exe.|

## <a name="remarks"></a>Poznámky

Visual Studio vyvolá xdcmake.exe automaticky při vytváření projektu. Můžete také vyvolat xdcmake.exe na příkazovém řádku.

Další informace o přidávání poznámek k dokumentaci do souborů zdrojového kódu naleznete v části [Doporučené značky pro komentáře k dokumentaci.](recommended-tags-for-documentation-comments-visual-cpp.md)

## <a name="see-also"></a>Viz také

[Dokumentace XML](xml-documentation-visual-cpp.md)
