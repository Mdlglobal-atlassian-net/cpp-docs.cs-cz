---
title: /GZ (Povolit běhovou kontrolu chyb rámce zásobníku)
ms.date: 11/04/2016
f1_keywords:
- /gz
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
ms.openlocfilehash: 35475b87b8f59fbb0fb24e62690f8fc24c7cb4e9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423466"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Povolit běhovou kontrolu chyb rámce zásobníku)

Provede stejné operace jako [/RTC (kontroly chyb za běhu)](../../build/reference/rtc-run-time-error-checks.md) možnost. Zastaralé

## <a name="syntax"></a>Syntaxe

```
/GZ
```

## <a name="remarks"></a>Poznámky

**/GZ** platí pouze pro použití v nonoptimized ([/Od (zakázat (ladění))](../../build/reference/od-disable-debug.md)) sestavení.

**/GZ** se už nepoužívá od sady Visual Studio 2005; použijte [/RTC (kontroly chyb za běhu)](../../build/reference/rtc-run-time-error-checks.md) místo. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).

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
