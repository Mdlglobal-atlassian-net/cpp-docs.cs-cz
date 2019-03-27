---
title: Referenční dokumentace nástroje XDCMake
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: 097c105e005a3c734ba86139ed3b4b6ecdcf49d9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823319"
---
# <a name="xdcmake-reference"></a>Referenční dokumentace nástroje XDCMake

xdcmake.exe je program, který se zkompiluje soubory do souboru XML. Je vytvořen soubor .xdc kompilátorem MSVC pro každý zdrojový soubor kódu při kompilaci zdrojového kódu s [/doc](doc-process-documentation-comments-c-cpp.md) a pokud obsahuje komentáře k dokumentaci označené značky XML souboru se zdrojovým kódem.

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Použití xdcmake.exe ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** složky.

1. Klikněte na tlačítko **komentáře dokumentu XML** stránku vlastností.

> [!NOTE]
>  Při použití xdcmake.exe ve vývojovém prostředí (stránky vlastností), se liší od možností xdcmake.exe možnosti příkazového řádku. Informace o používání xdcmake.exe ve vývojovém prostředí najdete v tématu [stránky vlastností nástroje Generátor dokumentů XML](xml-document-generator-tool-property-pages.md).

## <a name="syntax"></a>Syntaxe

xdcmake `input_filename options`

## <a name="parameters"></a>Parametry

*input_filename*<br/>
Název souboru .xdc soubory sloužící jako vstup pro xdcmake.exe. Zadejte jeden nebo více souborů .xdc nebo použijte *.xdc používat všechny soubory v aktuálním adresáři.

*Možnosti*<br/>
Nula nebo více z následujících akcí:

|Možnost|Popis|
|------------|-----------------|
|/?, /help|Zobrazit nápovědu pro xdcmake.exe.|
|/ Assembly:*název souboru*|Umožňuje zadat hodnotu \<sestavení > značky v souboru XML.  Výchozí hodnota \<sestavení > Značka je stejný jako název souboru XML.|
|/nologo|Potlačí zprávu o autorských právech.|
|/ out:*název souboru*|Umožňuje zadat název souboru XML.  Ve výchozím nastavení název souboru XML je název prvního souboru .xdc zpracovány xdcmake.exe.|

## <a name="remarks"></a>Poznámky

Visual Studio se vyvolá xdcmake.exe automaticky při sestavování projektu. Můžete také vyvolat xdcmake.exe na příkazovém řádku.

Zobrazit [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments-visual-cpp.md) pro další informace o přidání komentáře k dokumentaci souborů se zdrojovým kódem.

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)