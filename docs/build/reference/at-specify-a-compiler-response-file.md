---
title: '@ (Zadat soubor odezvy kompilátoru)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: c2b5578e1ce1db590bdf5abbff0c91e858803ad7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272998"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Zadat soubor odezvy kompilátoru)

Určuje soubor odezvy kompilátoru.

## <a name="syntax"></a>Syntaxe

> **\@**<em>response_file</em>

## <a name="arguments"></a>Arguments

*response_file*<br/>
Textový soubor obsahující kompilátoru příkazy.

## <a name="remarks"></a>Poznámky

Soubor odpovědí může obsahovat všechny příkazy, které zadáte v příkazovém řádku. To může být užitečné, pokud vaše argumenty příkazového řádku být delší než 127 znaků.

Není možné určit **\@** možnost v souboru odpovědí. To znamená soubor odpovědí nelze vložit jiný soubor s odpovědí.

Z příkazového řádku můžete zadat libovolný počet možností soubor odpovědi (například `@respfile.1 @respfile.2`) jak chcete.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

- Soubor odpovědí nelze zadat z vývojového prostředí a musí být zadán v příkazovém řádku.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
