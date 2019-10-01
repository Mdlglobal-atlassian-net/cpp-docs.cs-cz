---
title: /LINKREPRO (název adresáře odkazů reprodukci)
description: Možnost linkeru nebo nástroje knihovny pro nastavení adresáře pro odkaz reprodukci.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686850"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO (název adresáře odkazů reprodukci)

Instruuje nástroj Linker nebo knihovny, aby vygeneroval odkaz reprodukci v zadaném adresáři.

## <a name="syntax"></a>Syntaxe

> **/LINKREPRO:** _adresář – název_

### <a name="arguments"></a>Argumenty

**/LINKREPRO:** _directory-Name_\
Uživatelem zadaný adresář, do kterého se má Uložit odkaz reprodukci. Názvy adresářů, které obsahují mezery, musí být uzavřeny do dvojitých uvozovek.

## <a name="remarks"></a>Poznámky

Možnost **/LINKREPRO** slouží k vytvoření *propojení reprodukci*. Je to sada artefaktů sestavení, které umožňují Microsoftu reprodukování problému, ke kterému dochází v době propojování nebo během operací knihovny. Je užitečné při potížích, jako je například selhání back-endu zahrnující generování kódu při propojování (LTCG), LINKERŮ LNK1000 linker nebo chyba linkeru. Nástroj vytvoří propojení reprodukci při zadání možnosti linkeru **/LINKREPRO** nebo při nastavení proměnné prostředí `link_repro` v prostředí pro sestavení příkazového řádku. Další informace najdete v části věnovaném předanému [propojení](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) v tématu [postup nahlášení problému se sadou C++ nástrojů Microsoftu](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Možnost linkeru **/LINKREPRO** a proměnná prostředí `link_repro` vyžadují, abyste určili výstupní adresář pro reprodukci propojení. V příkazovém řádku nebo v integrovaném vývojovém prostředí zadejte adresář pomocí možnosti **/LINKREPRO:** _Directory-Name_ . _Název adresáře_ , který zadáte, může být absolutní nebo relativní cesta, ale adresář musí existovat. Možnost příkazového řádku přepisuje všechny hodnoty adresáře nastavené v proměnné prostředí `link_repro`.

Informace o tom, jak omezit reprodukci generování propojení na konkrétní název cílového souboru, najdete v možnosti [/LINKREPROTARGET](linkreprotarget.md) . Pomocí této možnosti lze zadat konkrétní cíl pro vygenerování propojení reprodukci pro. Je užitečné v komplexních sestaveních, která vyvolávají nástroj Linker nebo knihovna více než jednou.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení této možnosti linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > **linker** >  stránka vlastností**příkazového řádku** .

1. Do pole **Další možnosti** zadejte možnost **/LINKREPRO:** _Directory-Name_ . Hodnota _název adresáře_ , kterou zadáte, musí existovat. Kliknutím na **tlačítko OK** aplikujte změnu.

Po vygenerování propojení reprodukci otevřete tuto stránku vlastností a odeberte možnost **/LINKREPRO** z vašich sestavení.

### <a name="to-set-this-linker-option-programmatically"></a>Chcete-li nastavit tuto možnost linkeru programově

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Další informace najdete v tématech

[Referenční příručka linkeru MSVC](linking.md)\
[MSVC Možnosti linkeru](linker-options.md)\
[/LINKREPROTARGET](linkreprotarget.md)
