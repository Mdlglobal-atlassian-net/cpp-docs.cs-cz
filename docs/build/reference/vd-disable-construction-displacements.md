---
title: /vd (Zakázat posunutí konstrukcí)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: a3e09bf923f9f77dfb594c598f8a14c766d052f8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426412"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Zakázat posunutí konstrukcí)

## <a name="syntax"></a>Syntaxe

```
/vdn
```

## <a name="arguments"></a>Arguments

**0**<br/>
Potlačí zobrazení skrytého členu vtordisp pro konstruktor nebo destruktor. Zvolte tuto možnost, pouze pokud jste si jisti, že všechny konstruktory a destruktory třídy volaly virtuální funkce virtuálně.

**1**<br/>
Povolí vytváření členů posunutí skryté vtordisp konstruktor nebo destruktor. Tato volba je výchozí hodnota.

**2**<br/>
Umožňuje používat [dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md) při konstrukci objektu. Například přetypování dynamic_cast z virtuální základní třídy na odvozenou třídu.

**/ vd2** přidá pole vtordisp v případě, že máte virtuální základ, s virtuálními funkcemi. **/ vd1** by mělo být dostatečné. Nejběžnější malá a velká where **/vd2** je nutné je po pouze virtuální funkce v základním virtuální destruktor.

## <a name="remarks"></a>Poznámky

Tyto možnosti platí pouze pro kód jazyka C++, který používá virtuální základy.

Visual C++ implementuje podpory skrytého konstrukce jazyka C++ v situacích, kdy je použita virtuální dědičnost. Posunutí konstrukcí vytvořené při volání virtuální funkce, deklarované v virtuální základ a přepsání v odvozené třídě problém vyřešit, je volána z konstruktoru během konstrukce další odvozené třídy.

Problém je, že virtuální funkce může být předáno nesprávné `this` ukazatel v důsledku rozporů mezi posunutí pro virtuální základy třídy a posunutí na její odvozené třídy. Řešení poskytuje jeden konstrukce posunutí úpravy, nazývá pole vtordisp pro každý virtuální základní třídy.

Ve výchozím nastavení pole vtordisp zavedení pokaždé, když kód definuje uživatelem definované konstruktory a destruktory a také přepsání virtuálních funkcí virtuálních základních tříd.

Tyto možnosti. ovlivňují celé zdrojové soubory. Použití [vtordisp](../../preprocessor/vtordisp.md) potlačit a potom znovu povolit pole vtordisp na základě třídy třídy.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
