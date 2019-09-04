---
title: '/Experimental: Module (povolení podpory modulu)'
description: 'Pomocí možnosti kompilátoru/Experimental: Module můžete povolit experimentální podporu kompilátoru pro moduly.'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 82cce127ad5a2f87d11e4a653035bd80ea9f5001
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294427"
---
# <a name="experimentalmodule-enable-module-support"></a>/Experimental: Module (povolení podpory modulu)

Umožňuje experimentální podporu kompilátoru pro moduly, jak je uvedeno v konceptu C++ 20 Standard.

## <a name="syntax"></a>Syntaxe

> **/Experimental: modul** [ **-** ]

## <a name="remarks"></a>Poznámky

Podporu experimentálních modulů můžete povolit pomocí možnosti kompilátoru **/Experimental: Module** společně s možností [/std: c + + nejnovější](std-specify-language-standard-version.md) . Můžete použít **/Experimental: Module-** k explicitnímu vypnutí podpory modulu.

Tato možnost je k dispozici od začátku v aplikaci Visual Studio 2015 Update 1. Od verze Visual Studio 2019 verze 16,2 nejsou koncepty C++ 20 Standard zcela implementovány v kompilátoru společnosti Microsoft C++ . Pomocí funkce moduly můžete vytvořit moduly s jedním oddílem a importovat standardní moduly knihovny poskytované společností Microsoft. Modul a kód, který ho využívá, musí být kompilovány se stejnými možnostmi kompilátoru.

Další informace o modulech a o tom, jak je lze použít a vytvořit, naleznete v tématu [Přehled modulů v C++ ](../../cpp/modules-cpp.md).

Tady je příklad možností příkazového řádku kompilátoru, které slouží k vytvoření modulu exportu ze zdrojového souboru *Module. IXX*:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Nastavte rozevírací seznam **Konfigurace** na **všechny konfigurace**.

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **jazyk** .

1. Upravte vlastnost **Povolit C++ moduly (experimentální)** a pak zvolte **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
