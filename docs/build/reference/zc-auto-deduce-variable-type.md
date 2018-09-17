---
title: '-Zc: auto (odvození typu proměnné) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09bb29b1baa6208f4b7473d8cbbc9a3abbe38e70
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709588"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (odvození typu proměnné)

**/Zc: Auto [-]** – možnost kompilátoru instruuje kompilátor, jak používat [auto – klíčové slovo](../../cpp/auto-keyword.md) pro deklarování proměnných. Pokud zadáte možnost výchozí **/Zc: Auto**, kompilátor odvodí typ proměnné deklarované z jeho výrazu inicializace. Pokud zadáte **/Zc:auto-**, kompilátor přiděluje proměnnou pro automatické třídě úložiště.

## <a name="syntax"></a>Syntaxe

> **/Zc:auto**[**-**]

## <a name="remarks"></a>Poznámky

Standard jazyka C++ definuje původní a revidovaný význam `auto` – klíčové slovo. Před Visual C++ 2010 klíčové slovo deklaruje proměnnou v automatické třídě úložiště; To znamená proměnná, která má místní dobu platnosti. Od verze Visual C++ 2010, klíčové slovo odvodí typ proměnné z výrazu inicializace deklarace. Použít **/Zc: Auto [-]** – možnost kompilátoru sdělit kompilátoru, aby použil původní a revidovaný význam `auto` – klíčové slovo. **/Zc: Auto** možnost zapnutá ve výchozím nastavení. [/ Permissive-](permissive-standards-conformance.md) možnost nezmění výchozí nastavení **/Zc: Auto**.

Kompilátor vyvolá odpovídající diagnostické zprávy, pokud vaše užívání `auto` – klíčové slovo v rozporu se aktuální **/Zc: Auto** – možnost kompilátoru. Další informace najdete v tématu [auto – klíčové slovo](../../cpp/auto-keyword.md). Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Zc: Auto** nebo **/Zc:auto-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[Auto – klíčové slovo](../../cpp/auto-keyword.md)
