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
ms.openlocfilehash: dc61477da9547204acfce93bbedcd077787162c2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416953"
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

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
