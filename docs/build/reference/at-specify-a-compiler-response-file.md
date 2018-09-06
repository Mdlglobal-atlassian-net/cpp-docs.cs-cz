---
title: '@ (Zadat soubor odezvy kompilátoru) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 430e6372c1ca26e946c2ff26bfcfe9180dfb0dba
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894451"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Zadat soubor odezvy kompilátoru)

Určuje soubor odezvy kompilátoru.

## <a name="syntax"></a>Syntaxe

> **\@**<em>response_file</em>

## <a name="arguments"></a>Arguments

*response_file*  
Textový soubor obsahující kompilátoru příkazy.

## <a name="remarks"></a>Poznámky

Soubor odpovědí může obsahovat všechny příkazy, které zadáte v příkazovém řádku. To může být užitečné, pokud vaše argumenty příkazového řádku být delší než 127 znaků.

Není možné určit **\@** možnost v souboru odpovědí. To znamená soubor odpovědí nelze vložit jiný soubor s odpovědí.

Z příkazového řádku můžete zadat libovolný počet možností soubor odpovědi (například `@respfile.1 @respfile.2`) jak chcete.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

- Soubor odpovědí nelze zadat z vývojového prostředí a musí být zadán v příkazovém řádku.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
