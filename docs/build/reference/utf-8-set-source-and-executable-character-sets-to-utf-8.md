---
title: -utf-8 (nastavení zdrojové a spustitelné znakové sady UTF-8) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 218ea7986e37ce9cfa98aeeb1da3c209bef73f8f
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029681"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/ UTF-8 (nastavení zdrojové a spustitelné znakové sady na UTF-8)

Určuje zdrojové znakové sady a provedení znakové sady jako UTF-8.

## <a name="syntax"></a>Syntaxe

```
/utf-8
```

## <a name="remarks"></a>Poznámky

Můžete použít **/UTF-8** můžete zadat zdroj a spuštění znakové sady jako kódování pomocí kódování UTF-8. Je ekvivalentní se zadáním **/source-charset:utf – 8 /execution-charset:utf – 8** na příkazovém řádku. Některé z těchto možností také umožňuje **/Validate-Charset** možnost ve výchozím nastavení. Seznam podporovaných identifikátory znakových stránek a znakové sady názvy, naleznete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů k určení, zda zdrojový soubor je v zakódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je zakódován pomocí aktuální znakové stránce uživatele, pokud zadáte znakovou stránku pomocí **/UTF-8** nebo **/Source-Charset** možnost. Visual Studio umožňuje uložit zdrojovém kódu jazyka C++ pomocí některého z několika kódování znaků. Informace o spuštění a zdrojová znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.

1. V **rozšířené možnosti**, přidejte **/UTF-8** možnosti a určete upřednostňované kódování.

1. Zvolte **OK** uložte provedené změny.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/ Execution-Charset (nastavení znakové sady spuštění)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/validate-charset (ověření kompatibilních znaků)](../../build/reference/validate-charset-validate-for-compatible-characters.md)