---
title: -Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98dc9416ecee69bca285ff54d6321144c4a3fd02
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724422"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)