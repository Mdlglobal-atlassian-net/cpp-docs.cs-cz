---
title: /Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: eb01d39ccbbdac60d629f95b9eb821ca0f2f5731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662394"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)

Odebere `fwait` příkazy interní `try` blokuje při použití [/FP: except](../../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru.

## <a name="syntax"></a>Syntaxe

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Poznámky

Tato možnost nemá žádný vliv, pokud **/FP: except** není zároveň zadaná. Pokud zadáte **/FP: s výjimkou** možnost, kompilátor se vloží `fwait` příkaz kolem každý jednotlivý řádek kódu `try` bloku. Tímto způsobem může kompilátor identifikovat konkrétní řádek kódu, který generuje výjimku. **/ Qimprecise_fwaits** odebere interní `fwait` pokyny k opuštění kolem pouze ta čeká `try` bloku. To zvyšuje výkon, ale kompilátor bude mít jenom řekl, který `try` blok způsobí výjimku, ne kterém řádku.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)