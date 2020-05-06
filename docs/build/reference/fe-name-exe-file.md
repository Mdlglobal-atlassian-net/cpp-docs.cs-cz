---
title: /Fe (název souboru EXE)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: f0bd8f3a96555cc29d06f74fb44a73bbed32889b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825575"
---
# <a name="fe-name-exe-file"></a>/Fe (název souboru EXE)

Určuje název a adresář pro soubor. exe nebo knihovnu DLL vytvořenou kompilátorem.

## <a name="syntax"></a>Syntaxe

> **/FE**[_cesta_] \
> **/FE:** _cesta_

### <a name="arguments"></a>Argumenty

*název*<br/>
Relativní nebo absolutní cesta a základní název souboru nebo relativní nebo absolutní cesta k adresáři nebo název základního souboru, který se má použít pro vygenerovaný spustitelný soubor.

## <a name="remarks"></a>Poznámky

Možnost **/FE** umožňuje zadat výstupní adresář, název výstupního souboru nebo obojí pro vygenerovaný spustitelný soubor. Pokud *cesta* končí oddělovačem cesty (**&#92;**), předpokládá se, že zadáte pouze výstupní adresář. V opačném případě se jako základní název výstupního souboru použije poslední součást *cesty* a zbytek *cesty* určuje výstupní adresář. Pokud *cesta* neobsahuje žádné oddělovače cest, předpokládá se, že v aktuálním adresáři určíte název výstupního souboru. *Cesta* musí být uzavřena do dvojitých uvozovek (**"**), pokud obsahuje znaky, které nemohou být v krátké cestě, například mezery, rozšířené znaky nebo součásti cesty delší než osm znaků.

Pokud není zadána možnost **/FE** nebo není-li zadán základní název souboru v *cestě*, kompilátor poskytne výstupnímu souboru výchozí název pomocí základního názvu prvního zdrojového nebo souborového souboru zadaného v příkazovém řádku a příponou. exe nebo. dll.

Pokud zadáte možnost [/c (kompilovat bez propojení)](c-compile-without-linking.md) , **/FE** nemá žádný vliv.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete stránku **vlastnosti** > konfigurace**Obecné** vlastnosti**linkeru** > .

1. Upravte vlastnost **výstupní soubor** . Kliknutím na **tlačítko OK** uložte změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Příklad

Následující příkazový řádek zkompiluje a propojí všechny zdrojové soubory C v aktuálním adresáři. Výsledný spustitelný soubor má název PROCESs. exe a je vytvořen v adresáři "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Příklad

Následující příkazový řádek vytvoří spustitelný soubor v `C:\BIN` se stejným základním názvem jako první zdrojový soubor v aktuálním adresáři:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)<br/>
